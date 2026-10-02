# Cloud-Native Application Deployment & Storage Pipeline

A resilient, cloud-native backend built with Java, Spring Boot, and AWS cloud ecosystem components (EC2, S3, RDS, IAM). The service exposes RESTful APIs to ingest multipart file payloads, persisting file binaries securely in AWS S3 and tracking document metadata within an Amazon RDS (MySQL) relational database.

---

## Architecture Overview

* **Compute (Amazon EC2):** Hosts the containerized/standalone Spring Boot application runtime behind tailored Security Groups.
* **Relational Storage (Amazon RDS - MySQL):** Stores relational metadata (entity identifiers, user context, uploaded timestamps, and S3 file keys).
* **Object Storage (Amazon S3):** Manages unstructured object storage for multipart file payloads with custom bucket policies.
* **Identity & Access Management (AWS IAM):** Enforces least-privilege security by leveraging IAM roles and policies, eliminating hardcoded cloud credentials.

---

## Tech Stack

* **Language:** Java 17 / 21
* **Framework:** Spring Boot 3 (Spring Web, Spring Data JPA)
* **Cloud & Storage:** AWS SDK for Java 2.x (S3), Amazon RDS (MySQL), Amazon EC2
* **Emulation & Testing:** Docker, Docker Compose, LocalStack (S3 emulator)
* **Build Tool:** Maven

---

## Project Structure

```text
├── src/main/java/com/example/demo/
│   ├── config/
│   │   └── AwsConfig.java                # AWS SDK S3Client Bean configuration
│   ├── controller/
│   │   └── DocumentController.java       # Multipart file ingestion & retrieval endpoints
│   ├── model/
│   │   └── UserDocument.java             # JPA Entity mapped to relational schema
│   ├── repository/
│   │   └── UserDocumentRepository.java   # Spring Data JPA persistence interface
│   ├── service/
│   │   └── S3Service.java                # Core AWS S3 integration service
│   └── DemoApplication.java
├── docker-compose.yml                    # Local infrastructure (LocalStack S3 + MySQL)
├── pom.xml
└── README.md
