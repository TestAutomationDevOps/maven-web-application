pipeline
{
    agent any
  
    tools
    {
      maven 'Maven_8.6.4'
    }
  
    environment
    {
       Build_Number = "${BUILD_NUMBER}"
    }
  
  stages
  {
     stage('Git Checkout')
    {
       steps()
      {
          git 'https://github.com/TestAutomationDevOps/maven-web-application.git'
      }
    }
    
    stage('Build Project')
    {
       steps()
      {
          sh 'mvn clean package'
      }
    }
    
    stage('Build Docker Image')
    {
       steps()
      {
          sh 'docker build -t 873892298042.dkr.ecr.ap-south-1.amazonaws.com/mavenwebapplication:$Build_Number .'
      }
    }
  }
}
