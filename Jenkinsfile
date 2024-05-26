pipeline {
    agent any

    tools {
        maven 'Maven 3.8.1' // Assurez-vous que Maven est installé et configuré dans Jenkins
    }

    environment {
        MAVEN_OPTS = '-Xms256m -Xmx512m'
    }

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/axelbernard20/spring-petclinic.git'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
        stage('Package') {
            steps {
                sh 'mvn package'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying...'
                // Ajouter des étapes de déploiement ici
            }
        }
    }

    post {
        always {
            junit '**/target/surefire-reports/*.xml'
            archiveArtifacts artifacts: '**/target/*.jar', allowEmptyArchive: true
        }
    }
}
