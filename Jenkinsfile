pipeline {
    agent any
    stages {
        stage('Build Jar') {
              steps {
                bat 'mvn clean package -DskipTests'
            }
        }
        stage('Build Image') {
            steps {
            bat "docker build -t=partha59docker/selenium-docker ."

            }
        }
        stage('Push Image') {
            steps {
			       withCredentials([usernamePassword(credentials: 'dockerhub' , passwordVariable: 'pass', usernameVariable: 'user')]) {
			       bat "docker login --username=${user} --password=${pass}"
			       bat "docker push partha59docker/selenium-docker:latest"
			    }
            }
        }
    }
}