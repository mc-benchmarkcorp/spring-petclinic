@Library ('shared-library') _
pipeline {
  agent {
    kubernetes {
      yaml libraryResource('podTemplates/podTemplate.yaml')
    }
    agent {
        docker {
            image 'maven:3-alpine' 
            args '-v /root/.m2:/root/.m2' 
    }
  }
    stages {
        stage('Build') { 
            steps {
                sh 'mvn -B -DskipTests clean package' 
            }
        }
    }
}
