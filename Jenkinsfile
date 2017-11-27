pipeline {
    agent any

    stages {
        stage('Git') {
            steps {
                git credentialsId: 'a4e0d304-6bbb-4313-bb7b-a9f2304f7bfa', url: 'git@github.com:tomasz-safuryn/nginx-docker.git'
            }
        }
        stage('Update') {
            steps {
                echo 'Updating..'
		sh 'bash ./update.sh'
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
