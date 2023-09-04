pipeline{
    agent any
    environment {
        DIRECTORY_PATH = '/user/work/'
        TESTING_ENVIRONMENT = 'Ultimate testing environment'
        PRODUCTION_ENVIRONMENT = 'EC2 server 1' 
    }
    stages{
        stage('Build') {
            steps{
                echo 'Code compilation complete.'    
                echo 'Packaged to zip complete.'
            }
        }
        stage('Testing') {
            steps{
                echo 'Unit tests successful. no issues.'
                echo 'Integration tests successful. no issues.'
            }
            post{
                success{
                    emailext attachLog: true, attachmentsPattern: 'generatedFile.txt',
                    subject:'Unit and integration test status',                    
                    body:'test successful!!!'                                                           
                }
            }
        }
        stage('Code') {
            steps{
                echo 'Code analysis successful. no issues.'
            }
        }
        stage('Security') {
            steps{
                echo 'Security scan complete. no issues.'
            }
            post{
                success{
                    mail to:'rvajero@gmail.com',
                    subject:'Security test status',
                    body:'test successful!!!'
                }
            }
        }
        stage('Deploy') {
            steps{
                echo 'Deployment to EC2 server complete.'
            }
        }
        stage('Integration test') {
            steps{
                echo 'Integration test complete.'
            }
            post{
                success{
                    mail to:'rvajero@gmail.com',
                    subject:'Integration test status',
                    body:'test successful'
                }
            }
        }
        stage('Deploy to Production') {
            steps{
                echo "Deploying code to ${PRODUCTION_ENVIRONMENT}"
            }
            post{
                success{
                    mail to:'rvajero@gmail.com',
                    subject:'Deployment status',
                    body:'Deployment successful'
                }
            }
        }
    }
}
