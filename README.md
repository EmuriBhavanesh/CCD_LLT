# CCD_LLT


CCD LLT project

Pipeline Design

GitHub pushes trigger workflow.
Checkout Code
Configure AWS credentials from OIDC.
Login to AWS ECR
Multi-stage Docker image is built.
Image is pushed to AWS ECR.
IAM Role Design Setup a Role in IAM of AWS with Trust relationships pointing to the following.

githubusercontent token
github repo path with brancch information
AWS Identity provider Audience ID. The IAM role should be able to pull information from github using secure credentials and build an Image in the ECR.
Challenges Faced:

The AWS account provided by university didn't had role creating privilige in IAM, had to use our personal account.
selecting the appropriate policies which communicates with ECR to build image
selecting appropriate jar package in multi-stage docker file to deploy and build the image.
configuring yaml file for Github actions: need to run multiple times and re-run at failed stages to troubleshoot and streamline the script.
Multi-Stage build: working. After pushing the code build the JAR using the maven:3.9.2-eclipse-temurin-17 package Once after building the jar use eclipse-temurin:17-jdk-alpine to run that built jar to generate final image.
