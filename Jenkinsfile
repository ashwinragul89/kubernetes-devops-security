pipeline {
  agent any

  stages {
      stage('Build Artifact') {
            steps {
              echo "Pulling starting form Github"
              sh "mvn clean package -DskipTests=true"
              archive 'target/*.jar' 
            }
        }   
    }
}
