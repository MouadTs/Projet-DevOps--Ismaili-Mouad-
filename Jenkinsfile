pipeline{
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/MouadTs/Projet-DevOps--Ismaili-Mouad-.git'
            }
        }
        stage('Build') {
            steps {
                echo 'Building...'
                sh 'javac App.java'
                sh 'java App'

            }
        }
        stage('Archive') {
            steps {
                archiveArtifacts artifacts: '**/*.java', allowEmptyArchive: true
            }
        }

    }
}