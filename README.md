Live DevOps Project for Resume: Jenkins CI/CD with GitHub Integration

Description:
This project demonstrates a practical implementation of a Continuous Integration and Continuous Deployment (CI/CD) pipeline using Jenkins and GitHub on an AWS EC2 instance. It includes setting up Jenkins, integrating it with GitHub, and automating the deployment of a Node.js application using Docker. This hands-on project showcases your ability to streamline DevOps workflows and is an excellent addition to your resume.
## Steps:

### 1. Set up Jenkins on AWS EC2 Instance

```sh
sudo apt update
sudo apt install openjdk-11-jre
java -version
curl -fsSL https://pkg.jenkins.io/debian/jenkins.io.key | sudo tee /usr/share/keyrings/jenkins-keyring.asc > /dev/null
echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] https://pkg.jenkins.io/debian binary/ | sudo tee /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt-get update
sudo apt-get install jenkins
sudo systemctl enable jenkins
sudo systemctl start jenkins
sudo systemctl status jenkins
```

### 2. Access Jenkins
Open a web browser and navigate to http://<your-ec2-public-ip>:8080.
Retrieve the initial admin password:
sudo cat /var/lib/jenkins/secrets/initialAdminPassword

```sh
sudo apt update
sudo apt install openjdk-11-jre
java -version
```

### 3. Install Jenkins

```sh
curl -fsSL https://pkg.jenkins.io/debian/jenkins.io.key | sudo tee /usr/share/keyrings/jenkins-keyring.asc > /dev/null
echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] https://pkg.jenkins.io/debian binary/ | sudo tee /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt-get update
sudo apt-get install jenkins
sudo systemctl enable jenkins
sudo systemctl start jenkins
sudo systemctl status jenkins
```

### 4. Access Jenkins
Open a web browser and navigate to `http://<your-ec2-public-ip>:8080`.

Retrieve the initial admin password:
```sh
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```

### 5. Install Docker

```sh
sudo apt install docker.io
sudo usermod -a -G docker $USER
```

### 6. Create Dockerfile for Node.js Application

Create a Dockerfile in your project directory:

```dockerfile
FROM node:12.2.0-alpine
WORKDIR /app
COPY . .
RUN npm install
EXPOSE 8000
CMD ["node", "app.js"]
```

### 7. Build and Run Docker Container Locally

```sh
docker build . -t node-app
docker run -d --name node-todo-app -p 8000:8000 node-app
```

### 8. Integrate Jenkins with GitHub

1. Generate a Personal Access Token on GitHub.
2. In Jenkins, configure the GitHub plugin with this token.
3. Create a new Jenkins job, set it to pull the repository containing the Node.js application from GitHub.


### 9. Configure Jenkins Job

In the Jenkins job configuration, add a build step to execute shell commands:

```sh
docker build . -t node-app-todo
docker run -d --name node-app-container -p 8000:8000 node-app-todo
```

### 10. Automate the Build and Deployment Process

Set up a webhook in your GitHub repository to trigger the Jenkins job on every push.

### Project Outcome
- **Automated Build:** Every code commit to the GitHub repository triggers an automated build process in Jenkins.
- **Continuous Testing:** Integrated unit tests ensure code quality before deployment.
- **Deployment Automation:** The application is automatically deployed to a specified environment upon successful build and test.
- **Enhanced Efficiency:** Streamlined DevOps process with reduced manual tasks and faster release cycles.

### Conclusion
This project demonstrates practical skills in setting up and managing CI/CD pipelines using Jenkins, GitHub, and Docker on AWS. It highlights your ability to automate software development processes and is a valuable addition to your resume.

### License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

### Acknowledgments
- Jenkins
- Docker
- GitHub
- AWS

