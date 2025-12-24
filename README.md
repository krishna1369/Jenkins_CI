# Steps 
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


## 3.Create Security Groups
### Jenkins SG
ssh - Port 22,
Jenkins - port 8080,
Nexus - port 8080(through nexus to jenkins)

### Nexus 
ssh - port 22,
Nexus - port 8081( through my ip),
nexus - port 8081( through jenkins sg)

### Sonar (port 9000)
ssh - port 22,
sonarqube - port 80 (through my ip),
sonar - port 80 ( through jenkins sg)


## 5.Post Installation:
### Jenkins plugins
1. Maven Integration,
2. Github Integration,
3. Nexus Artifact Uploader,
4. SonarQube Scanner,
5. Slack Notification,
6. Build Timestamp,
7. Pipeline: Stage View

### 10.nexus Repository:
username: admin

Repository => Respositories => create Repository => 
1. Maven2(hosted) => Name:vprofile-release => Create Repository
2. Maven2(proxy) => Name:vpro-maven-central(download dependencies & stores) => create Repository
3. Maven2(hosted) => Name:vprofile-snapshot => version policy: snapshot => Create Repository
4. Maven2(group) => Name:vpro-maven-group => selected members(vpro-maven-central, vprofile-release, vprofile-snapshot)

#### Publish Artifact:
Browse => vrofile-release => QA/vproapp/{build_id}_{yyyy_MM_dd_HHMM}


### 9.SonarQube Code Quality:
default
username: admin
password: admin

Administrator => myaccount => security => generate token(Jekins)

Project settings:Quality gate => quality gate => create => Name:vprofileQG => Add condition => bugs (value) => Project settings:Quality gate => quality gate:vprofileQG(Name)

Project settings:Webhooks => create => 
```bash
Name:jenkinswebhook
URL:http://private_ip:8080/sonarqube-webhook
```

## 6.GitHub & VS code Integration:
1. Generate ssh key using ssh-keygen
2. Provide a public key in the github(settings/ssh & gpg keys)
3. In local path: ~/.ssh => vim config 
```bash
Host github.com-krishna1369
  User git
  IdentityFile ~/.ssh/krishna1369
  HostName github.com
```
4.  Go to the respect directory & clone it
```bash
git clone git@github.com-krishna1369:krishna1369/Jenkins-CI.git
```
5. Commit & push the changes.

### Tools & Credentials(Jenkins):
#### Tools:
Add JDK => Name:JDK17 => JAVA_HOME:/usr/lib/jvm/java-1.17.0-openjdk-amd64
Add Maven => Name:MAVEN3.9 => 3.9.9
Add SonarQube Scanner => Name:sonarscanner => SonarQube Scanner 4.7.0.2747

#### Credentials:
1. Nexus(username with password)
2. SonarQube(secret text)
3. Slack(secret text)

#### System
SonarQube servers => Env => Name:sonarserver => Server URL:http://private_IP => save
Build Timestamp => pattern:yyyy_MM_dd_HHmm => save


#### Configuration
workspace:vprofilecicd => credential:slacktoken => default channel:#jenkinscicd => save


## 8.Githubwebhook
Repo's settings => Webhook => Payload url:http://pub_ip/github-webhook/ => content type:application/json => event/trigger:just the push event => Add webhook

Jenkins server => Pipeline => Build trigger: github hook trigger for Gitscm polling => save


## 11.Slack
Create a workspace => vprofilecicd => devopscicd(team) => mail:bmk136912@gmail.com(add teammates) => channel:jenkinscicd 

Add Apps => Jenkins CI => channel:jenkinscicd => 
