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
		sh 'update.sh'
            }
        }
        stage('Build') {
            steps {
                echo 'Building..'
		sh 'dockerfiles'
		sh 'cloudbuild >cloudbuild.yaml'
		sh 'gcloud alpha container builds create . \
                       --project="orbitera-dev" --config=cloudbuild.yaml --verbosity=info --timeout=1h \
                       --gcs-source-staging-dir="gs://cpe-docker-testing/staging" \
                       --gcs-log-dir="gs://cpe-docker-testing/logs"'
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
