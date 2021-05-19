pipeline {

    agent {
        label "master"
    }

    environment {
        DOCKER_REGISTRY_URL = "localhost"
        APP_NAME = "hello-python"
        image_tag = "${DOCKER_REGISTRY_URL}/${APP_NAME}:${env.BUILD_NUMBER}"
        GIT_URL = "https://github.com/satishrawat/python-flask.git"
    }

    stages {
        stage("Fetch_Code") {
            steps {
                script {
                    // Let's clone the source
                    //git 'https://github.com/satishrawat/new-spring-bbot-sonar.git';
                    git([url: 'https://github.com/satishrawat/python-flask.git', branch: 'master', credentialsId: 'github'])
                }
            }
        }

        
        stage('Build image') {
            steps {
                echo 'Starting to build docker image'

                script {
                    dockerImage = docker.build("${image_tag}")
					
					
                }
            }
        }
        stage('Run_Application_in_Docker') {
            steps {
                echo 'Running Application in Docker'

                script {
                    //dockerImage = docker.build("${image_tag}")
                    sh "docker run -d -p 5000:5000 ${image_tag}"
					
					
                }
            }
        }
        }
    }

        
