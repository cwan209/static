pipeline {
    agent any
    stages {
        stage('Lint HTML') {
            steps {
                sh 'echo "linting started"'
                tidy -q -e *.html
            }
        }
        stage('Upload to AWS') {
            steps {
                withAWS(credentials: 'aws-static', region: 'us-west-2') {
                    sh 'echo "uploading started"'
                    s3Upload(file:'index.html', bucket:'lukechenluwang-jenkins-pipeline', path:'index.html')
                    sh 'echo "uploaded"'
                }
            }
        }
    }
}