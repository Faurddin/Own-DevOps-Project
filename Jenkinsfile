pipeline{
	agent any
	triggers { 
		githubPush()
	}
	stages{
		stage('clone git hub'){
			steps{
				git branch: 'main', url:'https://github.com/Faurddin/Own-DevOps-Project.git'
			}
		}
        stage('docker build'){
            steps{
                sh' docker build -t flask .'
            }
        }
		stage('docker push'){
			steps{
				sh''' 
				docker login -u faurddin -p Docker@02
				docker tag flask faurddin/flask
				docker push faurddin/flask
				'''
			}
		}
		stage('K8s Deployment'){
			steps{
				sh' kubectl create deployment deployment.yml'
			}
		}
		stage('minikube url'){
			steps{
				sh' minikube service flask --url'
			}
		}
	}
}
