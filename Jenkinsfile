pipeline{
  agent {
    docker {
      //image 'maven:3.5.2-jdk-8-alpine'
      image 'registry-dev:443/jenkins-sfc_maven:latest'
      args '-v /root/.m2:/root/.m2'
    }
  }
  stages{
    stage('Build') {
      steps {
        sh 'whoami'
        sh 'mvn -B -DskipTests clean package'
      }
    }
    stage('Test'){
      steps {
          sh 'mvn test'
      }
      post {
        always {
          junit 'target/surefire-reports/*.xml'
        }
      }
    }
  }
}
