pipeline {
    agent any
    environment{
        DOCKERHUB_CREDS = credentials('DockerHub')
    }
    stages {
        stage('Clone Repo') {
            steps {
                checkout scm
                sh 'ls *'
            }
        }
        stage('Build Image') {
            steps {
                //Aquí debes poner tu repositorio de dockerhub
		sh 'docker build -t aluben2829/ejemplodockerhub_ricardobenito . '
            }
        }
        stage('DockerHUB Login') {
            steps {
                
                sh 'echo $DOCKERHUB_CREDS_PSW | docker login -u $DOCKERHUB_CREDS_USR --password-stdin'                
                }
            }
        stage('Docker Push') {
            steps {
		//Aquí debes poner tu DockerHub
		sh 'docker tag aluben2829/ejemplodockerhub_ricardobenito aluben2829/ejemplodockerhub_ricardobenito'
                sh 'docker push aluben2829/ejemplodockerhub_ricardobenito:tagname'
                }
            }
        }
    post {
		always {
			sh 'docker logout'
		}
	 }
    }

