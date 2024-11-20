# Trigger-Based-Pipeline
Creating a Jenkins pipeline for CI/CD involves several steps, starting from installing Jenkins to configuring the pipeline to trigger based on events like code changes.
Step 1: Install Jenkins
```
#!/bin/bash
sudo wget -O /usr/share/keyrings/jenkins-keyring.asc \
  https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key
echo "deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc]" \
  https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt-get update
sudo apt install fontconfig openjdk-17-jre -y
sudo apt update
sudo apt-get install jenkins -y
```
Go to the Jenkins download page.
Choose your operating system and follow the specific installation steps.
Start Jenkins:

After installation, start Jenkins:
Linux: Run 
```
sudo systemctl start jenkins.
```
Windows: Jenkins will typically run as a Windows service after installation.
Access Jenkins:
Open a web browser and go to http://localhost:8080.
Enter the initial admin password, which is found in the Jenkins installation directory, to complete the setup.

Step 3: Install Docker
```
#!/bin/bash
# Add Docker's official GPG key:
sudo apt-get update
sudo apt-get install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

# Add the repository to Apt sources:
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update

# To install the latest version, run:
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

# Verify that the Docker Engine installation is successful by running the hello-world image.
sudo docker run hello-world
```

Step 3: Install Maven
Download Maven:
```
apt install maven
```
Download the latest version of Maven and follow the instructions to install it on your system.
Verify Installation:
Open a terminal (or command prompt) and type:
```
mvn -version
```
This should display the Maven version, Java version, and other environment information.

Step 4: Configure Jenkins for Maven
Open Jenkins and Configure Tools:
Go to Manage Jenkins > Global Tool Configuration.
Add Maven:
Scroll to the Maven section.
Click Add Maven and set a name (e.g., Maven3.6).
If Maven is not installed on the Jenkins server, you can check the option Install automatically to let Jenkins manage it.
Add Java (if not already configured):
Scroll to the JDK section and configure the Java Development Kit (JDK) similarly.
