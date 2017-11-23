pipeline {
    agent any

    stages {
        stage('Git') {
            steps {
                git credentialsId: '4d3bc575-26a7-41af-81af-6bda61f7fd82', url: 'git@github.com:tomasz-safuryn/nginx-docker.git'
            }
        }
        stage('Build') {
            steps {
		sh 'ls -al'
                echo 'Building..'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
