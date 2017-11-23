pipeline {
    agent any

    stages {
        stage('Git') {
            steps {
                git credentialsId: '4d3bc575-26a7-41af-81af-6bda61f7fd82', url: 'git@github.com:tomasz-safuryn/nginx-docker.git'
            }
        }
        stage('Update') {
            steps {
                echo 'Updating..'
            }
        }
        stage('Build') {
            steps {
                echo 'Building..'
		sh 'ls -al'
		sh 'dockerfiles'
		sh 'ls -al'
		sh 'cloudbulild >cloudbuild.yaml'
		sh 'ls -al'
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
