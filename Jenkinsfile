pipeline {
    agent any
    stages {
        stage('Clone') {
            steps {
                checkout scm
                sh 'ls -la'
            }
        }
        stage('Build') {
            steps {
                sh 'python3 -m py_compile app.py'
            }
        }
        stage('Test') {
            steps {
                sh 'python3 -m unittest -v'
            }
        }
        stage('Artifact') {
            steps {
                sh 'tar -czf app-build.tar.gz app.py'
                archiveArtifacts artifacts: 'app-build.tar.gz', fingerprint: true
            }
        }
    }
}
