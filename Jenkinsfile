pipeline {
    agent any
    tools {
      maven 'maven3.8'
      jdk 'jdk11'
      ansible 'ansible2'
    }
    stages {
        stage('Clean') {
            steps {
                sh "mvn clean"
            }
        }
        stage('Test') {
            steps {
                sh "mvn test"
            }
        }
        stage('Package') {
            steps {
                sh "mvn package"
            }
        }
	stage('Deploy') {
            steps {
                ansiblePlaybook credentialsId: 'apache-id', disableHostKeyChecking: true, installation: 'ansible2', inventory: 'inventory.txt', playbook: 'apache.yml'
            }
        }

    }
}
