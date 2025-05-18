pipeline {
  agent any

  stages {
    stage('Build Artifact - Maven') {
      steps {
        sh "mvn clean package -DskipTests=true"
        archive 'target/*.jar'
      }
    }

    stage('Unit Tests - JUnit and Jacoco') {
      steps {
        sh "mvn test"
      }
      post {
        always {
          junit 'target/surefire-reports/*.xml'
          jacoco execPattern: 'target/jacocob.exec'
        }
      }
    }

    stage('Docker Build and Push') {
      steps {
          withDockerRegistry([credentialsId: "docker-hub", url: ""]) {
          sh 'printenv'
          sh 'sudo docker build -t ashwinragul21/devsecops/numeric-app:""$GIT_COMMIT"" .'
          sh 'docker push ashwinragul21/devsecops/numeric-app:""$GIT_COMMIT""'
       }
      }
    }
  }
}
