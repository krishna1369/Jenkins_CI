#Steps 
1. Login to AWS Account
2. Create key pair
3. Create Security Group
     a. Jenkins, Nexus & Sonarqube
4. Create Ec2 Instances with userdata
     a. Jenkins, Nexus & Sonarqube
5. Post Installation
     a. Jenkins setup & plugins
     b. Nexus setup & repository setup
     c. Soanrqube login test
6. Git
     a. Integrate github repo with VsCode and test it
7. Build job with Nexus integration
8. Github Webhook
9. Sonarqube server integration stage
10. Nexus Artifact upload stage
11. Slack Notification


## Create Security Groups
### Jenkins SG
ssh - Port 22,
Jenkins - port 8080
Nexus - port 8080(through nexus to jenkins)

### Nexus 
ssh - port 22
Nexus - port 8081( through my ip)
nexus - port 8081( through jenkins sg)

### Sonar (port 9000)
ssh - port 22
sonarqube - port 80 (through my ip)
sonar - port 80 ( through jenkins sg)








