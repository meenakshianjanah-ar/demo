pipeline {
  agent any
  tools {
    jdk 'JDK11'   // Jenkins will use the JDK we configure in "Manage Jenkins"
  }
  stages {
    stage('Checkout') {
      steps {
        checkout scm
      }
    }
    stage('Build') {
      steps {
        sh 'mkdir -p out'
        sh "${JAVA_HOME}/bin/javac -d out src/HelloWorld.java"
      }
    }
    stage('Run') {
      steps {
        sh "${JAVA_HOME}/bin/java -cp out HelloWorld"
      }
    }
  }
  post {
    always {
      archiveArtifacts artifacts: 'out/**', fingerprint: true
    }
  }
}

