pipeline {
    agent any
    tools { nodejs "mynodejs"}
    environment {
        Node_env="prod"
    }
    stages {
        stage('Git repo') {
            steps {
                git credentialsId: '0ea2ea28-3c5d-4241-b790-bfbdcd4947a5', url: 'https://github.com/snehal30mandlik/demo-git-pipeline.git'
                sh 'cat demo.txt'
            }
        }
        stage('Hello') {
            steps {
                echo Node_env
                echo 'Hello World'
            }
        }
        stage('mynodejs stage') {
            steps {
               sh 'npm install'
            }
        }
        stage('My-artifact') {
            steps {
               archiveArtifacts artifacts: '*', followSymlinks: false
            }
        }
        stage('My Secret') {
            steps {
               withCredentials([string(credentialsId: 'mysecret', variable: 'mysecret')]) {
    // some block
    echo mysecret
}
            }
        }
    }
}