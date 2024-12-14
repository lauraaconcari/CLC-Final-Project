# Scalability and Performance of an Online Shop

## Course: Master’s in Data Science

### Authors:
- Laura Concari (1890490)
- Francesco Sbordone (1969869)

**Academic Year**: 2023/2024

---

## Table of Contents

- [Introduction](#introduction)
- [Key Features](#key-features)
- [System Design](#system-design)
- [AWS Services and Implementation](#aws-services-and-implementation)
- [Testing and Results](#testing-and-results)
- [Technologies Used](#technologies-used)
- [Setup Instructions](#setup-instructions)
- [Project Structure](#project-structure)
- [Contributing](#contributing)
- [License](#license)

---

## Introduction

This project demonstrates the scalability and performance of a cloud-based web application simulating an online store. The application was developed using Django, containerized with Docker, and deployed on AWS infrastructure to ensure high availability, efficiency, and scalability. Key goals include testing the system under varying loads and optimizing performance through automated scaling and resource management.

---

## Key Features

1. **Web Application**:
   - Built with Django.
   - Allows users to browse and order products.
   - Includes a manager interface for adding and managing products.

2. **Dockerization**:
   - Ensures portability and ease of deployment.
   - Dockerfile builds the application environment and dependencies.

3. **Cloud Infrastructure**:
   - Hosted on AWS with services like EC2, S3, RDS, Lambda, and SQS.
   - Auto-scaling and load balancing for optimized resource usage.

4. **Image Processing**:
   - Automated image resizing via AWS Lambda triggered by S3 uploads.

5. **Scalable Database**:
   - PostgreSQL database hosted on AWS RDS.

---

## System Design

### Architecture Overview:

- **Application Load Balancer (ALB)**:
  - Distributes traffic across multiple EC2 instances.
  - Ensures redundancy and efficient load handling.

- **Auto Scaling Group**:
  - Dynamically adjusts the number of EC2 instances based on traffic.

- **AWS S3 and Lambda**:
  - Stores and processes product images.
  - Resized images are saved and their URLs updated in the database.

- **PostgreSQL Database**:
  - Manages data related to users, products, and orders.

---

## AWS Services and Implementation

### Key AWS Services:

1. **EC2 Instances**:
   - Host the Django application.
   - Deployed using a custom AMI with Docker pre-configured.

2. **S3 Bucket**:
   - Stores product images.
   - Triggers Lambda functions for image resizing and database updates.

3. **AWS Lambda**:
   - **Resizing Function**: Resizes images to 268x200 pixels.
   - **Database Update Function**: Updates image URLs in the RDS database.

4. **Amazon SQS**:
   - Buffers tasks between Lambda functions.
   - Improves reliability and decouples components.

5. **RDS**:
   - PostgreSQL database for backend storage.

6. **CloudWatch**:
   - Monitors system metrics (CPU, memory, network traffic).
   - Alerts for auto-scaling triggers.

---

## Testing and Results

### Types of Tests:

1. **Load Test**:
   - Simulated 30 concurrent users over 20 minutes.
   - Observed stable CPU and memory usage with no performance degradation.

2. **Stress Test**:
   - Pushed the system to its limits with 150 users over 1.5 hours.
   - Identified resource bottlenecks and validated auto-scaling policies.

3. **Endurance Test**:
   - Evaluated system stability under 500 users for 3 hours.
   - Confirmed durability and recovery of the system during extended high loads.

### Key Insights:
- Auto-scaling effectively maintained performance during traffic spikes.
- AWS SQS improved task reliability and decoupled components.
- Identified optimal configurations to minimize latency and maximize resource efficiency.

---

## Technologies Used

- **Programming Language**: Python
- **Framework**: Django
- **Containerization**: Docker
- **Cloud Services**: AWS (EC2, S3, RDS, Lambda, SQS, CloudWatch)
- **Database**: PostgreSQL

---

## Setup Instructions

### Prerequisites:

1. Install Docker and AWS CLI.
2. Configure AWS credentials with appropriate IAM roles.

### Steps:

1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/online-shop-scalability.git
   ```

2. Build and run the Docker container:
   ```bash
   docker build -t online-shop .
   docker run -d -p 80:80 online-shop
   ```

3. Deploy infrastructure on AWS:
   - Launch EC2 instances with the custom AMI.
   - Configure S3, RDS, Lambda, and SQS as per the architecture.

4. Monitor system performance using CloudWatch.

---

## Project Structure

```
online-shop-scalability/
├── app/                        # Django application code
├── Dockerfile                  # Docker configuration
├── README.md                   # Documentation
├── report.pdf                  # Project report
└── tests/                      # Load, stress, and endurance test scripts
```

---

## Contributing

Contributions are welcome! Follow these steps:

1. Fork the repository.
2. Create a feature branch:
   ```bash
   git checkout -b feature-name
   ```
3. Commit your changes:
   ```bash
   git commit -m "Add feature description"
   ```
4. Push your changes:
   ```bash
   git push origin feature-name
   ```
5. Submit a pull request for review.

---

## License

This project is licensed under the [MIT License](LICENSE). Use responsibly.
