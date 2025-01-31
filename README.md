# Jenkins Web Hosting Automation #


# project Overview #


This project demonstrates a Continuous Integration/Continuous Deployment (CI/CD) pipeline using Jenkins to automatically deploy a web application. The pipeline is configured to pull code from GitHub, build it, and deploy it to an AWS EC2 instance.


# Prerequisites #

- AWS EC2 instance (Ubuntu)

- Jenkins 2.485 or higher

- Java (OpenJDK 17)

- Git

- Web server (Apache2)

- GitHub account

# Infrastructure Setup #

# AWS EC2 Configuration #

- Launch an Ubuntu EC2 instance

- Configure Security Groups:

- Allow SSH (Port 22)

- Allow HTTP (Port 80)

- Allow Jenkins (Port 8080)

- Allow Custom TCP (Port 8080)



# java Installation #


bash

    sudo apt update
    sudo apt install openjdk-17-jdk -y

# Install Jenkins: #

bash

              curl -fsSL https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key | sudo tee \
              /usr/share/keyrings/jenkins-keyring.asc > /dev/null
              echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
             https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
              /etc/apt/sources.list.d/jenkins.list > /dev/null
              sudo apt update
              sudo apt install jenkins -y

# Start Jenkins service: #

bash
 
     sudo systemctl start jenkins
     sudo systemctl enable jenkins
     
# Web Server Setup #

Install Apache2:

bash

      sudo apt install apache2 -y

# Configure web root permissions: #

bash

    sudo chown -R jenkins:jenkins /var/www/html
    
# Jenkins Pipeline Configuration: #

1  Access Jenkins dashboard at http://your-ec2-ip:8080

2  Install suggested plugins

3  Create a new Pipeline job

4  Configure GitHub webhook for automatic triggers

5  Add pipeline script in Jenkinsfile

    sudo visudo

    jenkins ALL=(ALL) NOPASSWD: ALL


# Repository Structure #

    ├── index.html
    ├── css/
    └── styles.css
    ├── js/
    └── main.js
    ├── Jenkinsfile
    └── README.md
    
# pipeline stage #
    
-  Checkout : Pulls the latest code from GitHub

- Build: Prepares the web application

- Deploy: Copies files to Apache web root

- Test: Verifies deployment success

# Deployment #

The application is automatically deployed when:

- Push to main branch
  
- Manual build trigger
  
- Scheduled builds (if configured)

# Access Application #

After successful deployment, access the application at:

    http://your-ec2-ip
    
# Monitoring #

- Check Jenkins dashboard for build status
  
- View console output for detailed logs
  
- Monitor Apache2 logs: /var/log/apache2/

# Troubleshooting #

# 1. Jenkins Build Fails #

- Check Git credentials
  
- Verify Jenkins permissions
  
- Review console output


# 2. Deployment Issues

- Verify Apache2 service status
  
- Check file permissions
  
- Review Jenkins workspace


# 3. Access Issues

- Confirm security group settings
  
- Verify Apache2 configuration
  
- Check instance public IP


# Security Considerations #

- Use AWS security groups to restrict access

- Implement Jenkins security best practices

- Regularly update dependencies

- Secure sensitive credentials in Jenkins

- Use HTTPS for production deployments


# Author #

KUNAL JADHAV 

# Result :

![Screenshot 2024-11-16 230409](https://github.com/user-attachments/assets/60fa03ba-9951-4fc1-8c47-67ff016dbaca)


