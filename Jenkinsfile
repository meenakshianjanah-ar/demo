pipeline {
  agent any
  stages {
    stage('Checkout') {
      steps {
        checkout scm
      }
    }
    stage('Build') {
      steps {
        sh 'mkdir -p out'
        sh 'javac -d out src/HelloWorld.java'
      }
    }
    stage('Run') {
      steps {
        sh 'java -cp out HelloWorld'
      }
    }
  }
  post {
    always {
      archiveArtifacts artifacts: 'out/**', fingerprint: true
    }
  }
}
