pipeline {
  agent any

  stages {
      stage('Build Artifact') {
            steps {
              echo "Pulling the MVN ptoject - starting form Github"
              sh "mvn clean package -DskipTests=true"
              archive 'target/*.jar'
            }
        }   
    }
}
