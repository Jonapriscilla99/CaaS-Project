# CI/CD Pipeline with Jenkins
# Objective
Setting up a Jenkins pipeline to automate the deployment of an EKS (Elastic Kubernetes Service) cluster involves creating a scripted pipeline & configure the pipleine in Jenkins that performs the necessary steps to deploy the EKS cluster using AWS CDK (Cloud Development Kit).
Let's break down the process.
# Prerequisites
1. # EC2 Instance & Necessary Installations:
   - Launched a T2 medium EC2 instance for deployment of eks cluster.
   - Installed AWS cli & configure the AWS with credentials. 
   - Installed CDK for the cdk script.
   - Installed docker,pulled jenkins image from docker hub inside docker.
2. # Install and Configure Jenkins:
   - Run Jenkins container on a server or a virtual machine. You can follow the installation instructions provided by Jenkins for your specific operating system.
   - Start the Jenkins service. After starting, Jenkins will be accessible through a web browser on port 8080 by default.
   - Access Jenkins through a web browser and follow the initial setup instructions, including obtaining the initial administrator password.
   - Configure the jenkins console with git & AWS plugins & let installed the necessary plugins by itself.
   - Inside manage jenkins>credientials>global, insert github & AWS credentials.
   - Mentioned the IAM role where the eks cluster would deploy by giving the necessary permissions.
3. # Install and prepare github Repository:
   - Made up the git repository named Caas project
   - Created a webhook to access external services & notify them when events happen in github.
   - Provide the jenkins URL to Webhook payload. 
   - Generate the classic token from the developer settings.
   - Made up the git repository named Caas project
   - Connect the github repository with the jenkins server.
4. # Create a Jenkins Pipeline Job:
   - In the Jenkins dashboard, click on "New Item" to create a new job.
   - Provide a name for the job (In my case its "CDK-project").
   - Choose the "Pipeline" type job.
   - To configure the job, insert the github repository URL under github project option & check the GitHub hook trigger for GITScm polling option under build triggers.
   - In the "Pipeline" section,choose "Pipeline script" from the "Definition" drop-down menu & write the pipeline script with contains only two stages i.e git clone & cdk deploy 
   - Apply & Save the changes.
5. # Upload the cdk script:
   - Upload the code on the github.
6. # Run the pipeline job:
   - run the pipeline job from jenkins server by simply click on 'build' option.
   - checkout & test the code from the github in jenkins.