pipeline
{
  agent any
  
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
  }
}
