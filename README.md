# WordPress Migration to AWS (EC2 + RDS + S3 + CloudFront)

This repository documents the migration of a WordPress site from a traditional hosting environment to AWS, using an architecture based on EC2, RDS, S3 and CloudFront.

The goal was to reproduce a real-world production scenario, ensuring the migrated environment remained fully functional, secure and optimized for long-term operation.

---

## Architecture Overview

The final deployment uses the following AWS components:

- **Amazon EC2** – hosts the WordPress application using Apache + PHP
- **Amazon RDS (MySQL)** – offloads the database to a managed backend
- **Amazon EBS** – stores static assets and media
- **Amazon CloudFront** – CDN layer in front of the application
- **AWS Certificate Manager (ACM)** – provides the HTTPS certificate
- **Route 53** – manages DNS and subdomain routing

---

## Screenshots

All screenshots (1–37) documenting each phase of the process are stored under:

/screenshots


---

## Full Documentation

The complete step-by-step migration guide is available at:

/docs/migracion-wordpress-aws.md


---

## Technologies Used

- Amazon Linux 2023
- Apache 2.4
- PHP 8.x
- WordPress (latest)
- RDS MySQL 8
- AWS CLI
- WP-CLI
- S3 + CloudFront
- ACM
- Route 53

---

```text
wp-migration-aws/
├── docs/
│ ├── migracion-wordpress-aws.md
│ └── screenshots/
└── README.md
```

---

## Final Result

The WordPress instance is now fully migrated and operational on AWS.
Screenshot **#37** shows the final state with both the frontend and dashboard running under HTTPS.

---

## Author
Esteban Alvaredo
Cloud & Systems Engineer (AWS SAA-C03 Certified)

LinkedIn: https://www.linkedin.com/in/estebanalvaredo
Portfolio: https://cloud.estebanalvaredo.com