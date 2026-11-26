# AWS Multi-Website Hosting Using EC2 and Apache HTTP Server

## Project Overview

This project demonstrates how to host three different frontend websites on a single AWS EC2 instance using Apache HTTP Server (httpd).

All three websites are deployed in the AWS Mumbai Region (ap-south-1) and accessed through a single EC2 public IP address using different URL paths.

## Websites Hosted

### 1. Grocery Shopping Website
A frontend grocery shopping website featuring:
- Grocery product listings
- Product categories
- Shopping cart counter
- Responsive user interface

### 2. Ticket Booking Website
A frontend ticket booking website featuring:
- Event listings
- Event categories
- Search functionality
- Ticket booking interface

### 3. College Student Registration Website
A frontend college registration website featuring:
- College information
- Course listings
- Student registration form
- Responsive user interface

## AWS Services and Technologies

| Technology | Purpose |
|---|---|
| Amazon EC2 | Hosting the websites |
| AWS Mumbai Region | Deployment region (ap-south-1) |
| Apache HTTP Server | Serving website content |
| Linux | Server operating system |
| HTML | Website structure |
| CSS | Website styling |
| JavaScript | Frontend interactions |

## Architecture

All three websites are hosted on one EC2 instance.

```text
                 Internet
                    |
                    |
              AWS EC2 Instance
               (Mumbai Region)
                    |
             Apache HTTP Server
                 (Port 80)
                    |
          /var/www/html/
                    |
       +------------+------------+
       |            |            |
    Grocery       Ticket       College
    Website       Booking     Registration
       |            |            |
    /grocery/    /ticket/     /college/
```

## Deployment Configuration

### Website Directory Structure

```text
/var/www/html/
│
├── grocery/
│   └── index.html
│
├── ticket/
│   └── index.html
│
└── college/
    └── index.html
```

### Apache Installation

```bash
sudo yum update -y
sudo yum install httpd -y
```

### Start and Enable Apache

```bash
sudo systemctl start httpd
sudo systemctl enable httpd
```

### Create Website Directories

```bash
sudo mkdir -p /var/www/html/grocery
sudo mkdir -p /var/www/html/ticket
sudo mkdir -p /var/www/html/college
```

### Set Permissions

```bash
sudo chown -R apache:apache /var/www/html/
sudo chmod -R 755 /var/www/html/
```

### Restart Apache

```bash
sudo systemctl restart httpd
```

## Accessing the Websites

Replace `YOUR_PUBLIC_IP` with your EC2 instance's public IPv4 address.

- Grocery Website: `http://YOUR_PUBLIC_IP/grocery/`
- Ticket Booking Website: `http://YOUR_PUBLIC_IP/ticket/`
- College Registration Website: `http://YOUR_PUBLIC_IP/college/`

## AWS Security Group Configuration

| Type | Protocol | Port |
|---|---|---|
| SSH | TCP | 22 |
| HTTP | TCP | 80 |

SSH access should be restricted to your own IP address.

## Key Learnings

- Launching and configuring an AWS EC2 instance.
- Installing and managing Apache HTTP Server.
- Deploying multiple websites on a single Linux server.
- Managing website directories and file permissions.
- Configuring AWS Security Groups.
- Accessing hosted websites through a public IP address.

## Project Limitations

This project contains frontend-only websites. Database integration, authentication, payment processing and backend functionality are not implemented.

## Future Improvements

- Configure custom domains using Amazon Route 53.
- Enable HTTPS using SSL/TLS.
- Configure automated deployment.
- Implement backend and database integration.
- Explore hosting with multiple EC2 instances and load balancing.

---

**Project Status:** Completed

**Deployment Region:** AWS Mumbai (ap-south-1)
