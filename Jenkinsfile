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
     // Phase 4 : Livraison / Notification Slack (Consigne 4)
    post {
        always {
            echo 'Fin du pipeline'
        }
        success {
            // Envoie un message vert si tout passe
            slackSend (color: '#00FF00', message: "SUCCÈS: Le Pipeline ${env.JOB_NAME} [${env.BUILD_NUMBER}] a réussi ! Pour voir les détails : ${env.BUILD_URL}")
        }
        failure {
            // Envoie un message rouge si ça échoue
            slackSend (color: '#FF0000', message: "ÉCHEC: Le Pipeline ${env.JOB_NAME} [${env.BUILD_NUMBER}] a échoué. Vérifiez la console : ${env.BUILD_URL}")
        }
    }
}