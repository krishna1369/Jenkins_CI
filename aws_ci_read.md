# Continuous Integration (CI) on AWS Cloud:
1. Bitbucket
    - Create account & repository on bitbucket
    - SSH authentication from local to bitbucket account
    - Migrate vprofile project source code from github to bitbucket
2. Code Artifact
    a. Create code artifact respository
    b. Look at the settings for pom.xml & settings.xml
    c. Understand buildspec.yml file for code analysis build job
3. Sonar cloud setup
    a. Create account and set project details
4. Parameter store
    a. Store sonar cloud details into parameter store
    b. mention parameter store details in buildspec.yml file
5. AWS Code build job
    a. Understand buildspec.yml file for code build job
    b. Update pom.xml & settings.xml for code artifact repo detail
    c. Create a Build job for sonar code analysis
    d. Execute & Test
6. Build job for artifact
    a. Understand buildspec.yml file
    b. Create s3 bucket for artifact storage
    c. Create AWS code build job
    d. Execute & test
7. Code Pipeline 
    a. Create SNS notifications
    b. Create aws codepipeline
    c. Execute & test


# Continuous Delivery
#### Steps
1. Update github webhook with new jenkins ip
2. Copy Docker files from vprofile repo to our repo
3. Prepare two seprate jenkinsfile for staging & prod in source code
4. AWS steps
   a. IAM, ECR Repo setup
5. Jenkins Steps
   a. Install Plugins
       i. Amazon ecr
       ii. Docker, Docker build & publish
       iii. Pipeline: aws steps
6. Install docker engine & awscli on jenkins
7. Write Jenkins for Build & publish image to ECR
8. ECS setup
   Cluster, task definition, Service
9. Code for Deploy Docker image to ECS
10. Repeat the steps for ECS cluster
