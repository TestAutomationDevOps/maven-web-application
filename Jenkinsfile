pipeline
{
  agent any
  
  tools
  {
    maven 'Maven_8.6.4'
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
          sh 'docker build -t testautomationdevops/maven-kubernetes:1 .'
      }
    }
    
  }
}
