# Continuous Integration (CI) on AWS Cloud:
1. Bitbucket
    - Create account & repository on bitbucket
    - SSH authentication from local to bitbucket account
    - Migrate vprofile project source code from github to bitbucket
2. Code Artifact
   - Create code artifact respository
   - Look at the settings for pom.xml & settings.xml
   - Understand buildspec.yml file for code analysis build job
3. Sonar cloud setup
   - Create account and set project details
4. Parameter store
    - Store sonar cloud details into parameter store
    -  mention parameter store details in buildspec.yml file
5. AWS Code build job
    - Understand buildspec.yml file for code build job
    - Update pom.xml & settings.xml for code artifact repo detail
    - Create a Build job for sonar code analysis
    - Execute & Test
6. Build job for artifact
    - Understand buildspec.yml file
    - Create s3 bucket for artifact storage
    - Create AWS code build job
    - Execute & test
7. Code Pipeline 
    - Create SNS notifications
    - Create aws codepipeline
    - Execute & test


# Continuous Delivery
#### Steps
1. Update github webhook with new jenkins ip
2. Copy Docker files from vprofile repo to our repo
3. Prepare two seprate jenkinsfile for staging & prod in source code
4. AWS steps
   - IAM, ECR Repo setup
5. Jenkins Steps
   - Install Plugins
       - Amazon ecr
       - Docker, Docker build & publish
       - Pipeline: aws steps
6. Install docker engine & awscli on jenkins
7. Write Jenkins for Build & publish image to ECR
8. ECS setup
    - Cluster, task definition, Service
9. Code for Deploy Docker image to ECS
10. Repeat the steps for ECS cluster
