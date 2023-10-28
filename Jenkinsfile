pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo 'Hello to Git Hub World'
            }
        }
        
        stage('Build') {
            steps {
                echo 'Build'
            }
        }
        
        stage('Deploy') {
            steps {
                echo 'Deploying'
                withCredentials([[
                    $class: 'AmazonWebServicesCredentialsBinding',
                    credentialsId: 'MyAWS',
                    accessKeyVariable: 'AWS_ACCESS_KEY_ID',
                    secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']]){
                        sh(script: 'aws s3 cp  /var/jenkins_home/workspace/JenkinsPipeline/index.html s3://test-jenkins-foxhound/')
                }
            }
        }
        
        stage('Test') {
            steps {
                echo 'Testing'
            }
        }
        
        stage('Release') {
            steps {
                echo 'Releasing'
            }
        }
    }
}
