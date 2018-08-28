pipeline {
    stage('Code Checkout') { // for display purposes
      // Get some code from a GitHub repository
git credentialsId: 'magcloudhub', url: 'https://github.com/magcloudhub/CR-OnBoarding.git'
   }

    stage("static code analysis"){
            steps {
                withSonarQubeEnv('sonarqube') {
                    sh '/opt/sonar/bin/sonar-scanner -Dsonar.projectKey=ZervOnboarding -Dsonar.sources=api'
                }
            }
        }

        stage("build docker image"){
            steps {
                sh "docker-compose build"
            }
        }


        stage("env cleanup"){
            steps {
                sh "docker image prune -f"
            }
        }

        stage("Launch service"){
            steps {
                sh "docker-compose stop"
                sh "docker-compose up -d"
            }
        }

        stage("Launch Info"){
            steps {
                echo "service running on ${ip}"
            }
        }

    }
}

