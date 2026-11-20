# Deploying an Nginx Web Server on AWS EC2

Author: Md Mostafa Riad

## Introduction

This hands-on DevOps project demonstrates how to deploy
an Nginx web server on an AWS EC2 instance running Ubuntu.

## Technologies Used

- Amazon EC2
- Ubuntu Linux
- Nginx
- AWS Security Groups
- SSH
- Git and GitHub

## Architecture

Browser → Internet → Security Group → EC2 → Nginx

## Step 1: Launch an EC2 Instance

- Open the AWS Management Console.
- Navigate to EC2.
- Launch an Ubuntu instance.
- Select an appropriate instance type.
- Create or select a key pair.
- Configure networking.

## Step 2: Configure Security Groups

Configure the following inbound rules:

| Protocol | Port | Source |
|----------|------|--------|
| SSH | 22 | My IP |
| HTTP | 80 | Anywhere IPv4 |

Restrict SSH access to trusted IP addresses.

## Step 3: Connect to EC2

```bash
chmod 400 my-key.pem
ssh -i my-key.pem ubuntu@PUBLIC_IP
```

Replace the key filename and public IP with your own values.

## Step 4: Install Nginx

```bash
sudo apt update
sudo apt install nginx -y
```

## Step 5: Start and Enable Nginx

```bash
sudo systemctl start nginx
sudo systemctl enable nginx
sudo systemctl status nginx
```

## Step 6: Verify the Deployment

```bash
curl -I http://localhost
```

Open the EC2 public IP in a web browser:

```text
http://PUBLIC_IP
```

The Nginx welcome page should appear.

## Step 7: Troubleshooting

If the website is unavailable:

- Verify that the EC2 instance is running.
- Check the security group rules.
- Confirm that Nginx is running.
- Review the Nginx error logs.

```bash
sudo tail -n 50 /var/log/nginx/error.log
```

## Key Learning Outcomes

- AWS infrastructure provisioning
- Linux server administration
- Network security configuration
- Web server deployment
- Service monitoring and troubleshooting

## Cleanup

Terminate the dedicated lab instance when it is no
longer needed to avoid unnecessary AWS charges.

## Conclusion

This project demonstrates the fundamental skills
required to deploy and manage a cloud-based web server.

## GitHub Portfolio

https://github.com/mustafaridny-byte/DevOps-Project
