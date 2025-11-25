# Full Migration of a WordPress Site to AWS (EC2 + RDS + S3 + CloudFront)

This technical document describes the complete migration of an existing WordPress installation from a traditional hosting environment to AWS. The objective was to build a cleaner, more scalable and production-ready architecture while preserving the original content and functionality.

Each referenced screenshot corresponds to the `/screenshots` folder (1 to 37).

---

# 1. AWS Environment Setup

## 1.1 EC2 Instance Deployment
**Screenshots 1–3**

A new Amazon Linux 2023 EC2 instance was created with Apache, PHP-FPM and required PHP modules.
The instance was placed behind a security group allowing HTTP/HTTPS/SSH and configured with an IAM role for S3 access.

---

## 1.2 RDS MySQL Deployment
**Screenshots 4–6**

An Amazon RDS MySQL instance was provisioned with:

- Database identifier
- WordPress database name
- WordPress user credentials
- EC2 security group as inbound source

The instance was validated and connection parameters stored for WordPress.

---

# 2. Migrating Files and Database

## 2.1 Uploading WordPress Files
**Screenshots 7–10**

The original WordPress project files were transferred to the EC2 instance into:

/var/www/html


Permissions were normalized for Apache.

---

## 2.2 Importing the Database
**Screenshots 11–13**

The SQL dump from the previous hosting platform was imported into RDS using the standard MySQL client.

---

# 3. WordPress Configuration

## 3.1 Updating wp-config.php
**Screenshots 14–17**

The WordPress configuration was updated to point to RDS using:

- DB_NAME
- DB_USER
- DB_PASSWORD
- DB_HOST
- Table prefix

Salt keys were regenerated.

---

## 3.2 First Boot from EC2 Public IP
**Screenshots 18–19**

The site was loaded via the EC2 public IP to ensure the application and database connection were fully functional before attaching the domain.

---

# 4. DNS Layer

## 4.1 Route 53 DNS Configuration
**Screenshots 20–23**

A Route 53 record was created pointing:

wp.estebanalvaredo.com → CloudFront → EC2


DNS propagation was tested before proceeding.

---

# 5. CDN and HTTPS Layer

## 5.1 CloudFront + ACM Integration
**Screenshots 24–27**

A CloudFront distribution was created pointing to the EC2 origin, and an ACM-issued certificate was attached for full HTTPS support.

The distribution was validated over HTTPS.

---

# 6. Final Validation

## 6.1 WordPress Final Operation
**Screenshots 28–37**

Final checks were performed:

- HTTPS functioning end-to-end
- WordPress login and admin panel operational
- Frontend loading under the new domain
- Media handling fully functional
- Database served by RDS
- CDN layer active

Screenshot **#37** shows the final frontend and backend running under HTTPS.

---

# 7. Result

The migration successfully moves the WordPress site from traditional hosting to a modern AWS architecture, providing improved performance, scalability and long-term maintainability.
