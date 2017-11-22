pipeline {
    agent any

    stages {
        stage('Git') {
            steps {
                git credentialsId: 'd618fa96-7798-456c-81b3-19bf550077b5', url: 'git@github.com:tomasz-safuryn/nginx-docker.git'
            }
        }
        stage('Build') {
            steps {
		ls
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
