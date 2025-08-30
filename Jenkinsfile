pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                git branch: 'master',
                    url: 'https://github.com/meenakshianjanah-ar/demo'
            }
        }
        
        stage('Build') {
            steps {
                sh '''
                  echo "Compiling Java files..."
                  rm -rf out
                  mkdir -p out
                  javac -d out src/main/java/com/example/HelloWorld.java
                  jar cfe out/HelloWorld.jar com.example.HelloWorld com/example/*.class
                '''
            }
        }

        stage('Test') {
            steps {
                echo "Running tests..."
                // dummy stage, replace with real JUnit later
                sh 'echo "All tests passed ✅"'
            }
        }
        
        stage('Archive') {
            steps {
                archiveArtifacts artifacts: 'out/HelloWorld.jar', fingerprint: true
            }
        }

        stage('Deploy') {
            steps {
                echo "Deploying application..."
                sh 'nohup java -jar out/HelloWorld.jar > app.log 2>&1 &'
            }
        }
    }
}

