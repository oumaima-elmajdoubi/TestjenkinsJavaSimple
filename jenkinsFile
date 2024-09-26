pipeline {
    agent any

    stages {
        stage('List files') {
            steps {
                bat 'dir'
            }
        }
        stage('Compile') {
            steps {
                bat 'javac -d out src/Main.java'
            }
        }
        stage('Test') {
            steps {
                bat 'java -classpath lib/* src/MainTest.java'
            }
        }
        stage('Run') {
            steps {
                bat 'java -cp out Main'
            }
        }
    }

    post {
        always {
            echo 'Pipeline completed.'
            archiveArtifacts artifacts: 'out/*.class', allowEmptyArchive: true
        }
        success {
            echo 'Build and tests were successful!'
        }
        failure {
            echo 'There was an error in the pipeline.'
        }
    }
}
