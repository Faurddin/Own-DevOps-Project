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
		stage('docker run'){
			steps{
				sh' docker run -d -p 5000:5000 flask flask'
			}
		}
	}
}
