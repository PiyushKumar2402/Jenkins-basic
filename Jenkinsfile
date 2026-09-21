pipeline {
    parameters{
        choice(
            name: 'ENVIRONMENT',
            choices: ['Development','Production'],
            description: 'Select deployment environment'
            )
    }
    agent {
        label 'built-in'
    }
// if we have multiple linux commands then specify it as sh ''' and when it ends then again ''' this is how it works
//so there are basically two types of env variables same as in coding global and local
//which are made on top are available to everyone which are made in satges are only available to specific persons
    environment{
        APP_NAME= "MyApplication"
    }
    stages {
        stage('Build') {
            steps {
                sh '''
                    echo "Starting Build"
                    pwd
                    ls
                    echo "Build complete"
                '''
            }
        }

        stage('Test') {
            steps {
                sh 'pwd'
            }
        }
        stage('Credentials Test'){
            steps{
                script{
                    withCredentials([
                        string(
                            credentialsId:'demo-secret',
                            variable:'MY_SECRET'
                        )
                        ]){
                        sh 'echo "Secret is avaiable to jenkins"'
                        } 
                    }
                }
            }

        stage('Deploy') {
           when {
               expression{
                   params.ENVIRONMENT == 'Production'
               }
           }
            steps{
                echo "Deploying to production"
            }
        }
    }// this starts before the last curly braces of the pipeline being finished and post means after everything 
    post{
        success{
            echo "pipeline build successfull"
        }
        failure{
            echo "pipeline failed"
        }
        always{
            echo "pipeline finished"
        }
    }
}
