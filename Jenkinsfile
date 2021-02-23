pipeline{
   agent {
    docker {
      image 'maven:3.6.3-jdk-11'
      args '-v /root/.m2:/root/.m2'
    }
  }
  stages {
          stage("build & SonarQube analysis") {
            agent any
            steps {
              withSonarQubeEnv('sonar-server') {
                sh 'java -version'
                sh 'mvn sonar:sonar \
  -Dsonar.projectKey=first-sonar \
  -Dsonar.host.url=http://localhost:9000 \
  -Dsonar.login=001c7c998253b7531f3a20da49814c91a70dbb6f'
              }
            }
          }
    }
}
