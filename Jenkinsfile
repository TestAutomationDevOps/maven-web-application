pipeline
{
	agent any
	
    tools
	{
		maven 'Maven_3.8.6'
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
				sh "docker build -t 873892298042.dkr.ecr.ap-south-1.amazonaws.com/java-maven-application:$Build_Number ."
			}
		}
		
		stage('Push Docker Image to AWS ECR')
		{
			steps()
			{
				sh "aws ecr get-login-password --region ap-south-1 | docker login --username AWS --password-stdin 873892298042.dkr.ecr.ap-south-1.amazonaws.com"
				sh "docker push 873892298042.dkr.ecr.ap-south-1.amazonaws.com/maven-web-application:$Build_Number"
			}
		}
		
		stage('Deploy')
		{
			steps()
			{
				withKubeConfig(caCertificate: '', clusterName: '', contextName: '', credentialsId: 'K8s', namespace: '', serverUrl: '')
				{
					sh 'kubectl delete deployment mavenwebapplication-deployment -n test || true'
					sh 'kubectl apply -f mavenwebappdeployment.yaml'
				}
			}
		}
	}
}
