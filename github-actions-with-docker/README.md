"# Simple-java-app" 

# maven goal to package java app
mvn clean package

# Execute locally (Java 11 needed) and access the application on http://localhost:8080
java -jar target/spring-boot-web.jar

## Docker way

# Docker build image
docker build -t ultimate-cicd-pipeline:v1 .  # -t for tag
# docker run image(container)
docker run -d -p 8010:8080 -t ultimate-cicd-pipeline:v1

######################## Install/configure Jenkins ########################

- Pre-Requisites:
  Java (JDK)
  
- Run the below commands to install Java and Jenkins
 sudo apt update
 sudo apt install openjdk-11-jre 
 

- Verify Java is Installed
  java -version

# Command to install jenkins

curl -fsSL https://pkg.jenkins.io/debian/jenkins.io-2023.key | sudo tee \
  /usr/share/keyrings/jenkins-keyring.asc > /dev/null
echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
  https://pkg.jenkins.io/debian binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt-get update
sudo apt-get install jenkins

**Note: ** By default, Jenkins will not be accessible to the external world due to the inbound traffic restriction by AWS. Open port 8080 in the inbound traffic rules as show below.

EC2 > Instances > Click on
In the bottom tabs -> Click on Security
Security groups
Add inbound traffic rules as shown in the image (you can just allow TCP 8080 as well, in my case, I allowed All traffic).
Screenshot 2023-02-01 at 12 42 01 PM

Login to Jenkins using the below URL:
http://:8080 [You can get the ec2-instance-public-ip-address from your AWS EC2 console page]

Note: If you are not interested in allowing All Traffic to your EC2 instance 1. Delete the inbound traffic rule for your instance 2. Edit the inbound traffic rule to only allow custom TCP port 8080

After you login to Jenkins, - Run the command to copy the Jenkins Admin Password - sudo cat /var/lib/jenkins/secrets/initialAdminPassword - Enter the Administrator password



