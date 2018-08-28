node {
    stage("Code Checkout") { // for display purposes
      // Get some code from a GitHub repository
        git credentialsId: 'magcloudhub', url: 'https://github.com/magcloudhub/CR-OnBoarding.git'
                           }
              }
    
    //stage('SonarQube Analysis') {
      //def job = build job: 'SonarJob'
      //withSonarQubeEnv("SonarQube") {
    // withMaven(jdk: 'java-1.8.0-openjdk-amd64 ', maven: 'apache-maven-3.5.2') {
      //  sh 'mvn clean org.jacoco:jacoco-maven-plugin:prepare-agent package sonar:sonar ' +
        //  ' -Dsonar.host.url=https://sonarcloud.io '+
         // ' -Dsonar.organization=magcloudhub ' +
         //' -Dsonar.login=14c72f2b1ec1fe86f3de48d9e2e7fe8ee3ebe804 ' 
       // }
      //}
    // }//
               // }
  
    stage("build docker image"){
            sh "docker-compose build"
            }
 
    stage("env cleanup"){
            sh "docker image prune -f"
            }

    stage("Launch service"){
            sh "docker-compose stop"
            sh "docker-compose up -d"
            }
  
    stage("Launch Info"){
            echo "service running on ${ip}"
            }
