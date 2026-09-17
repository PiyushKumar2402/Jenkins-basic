pipeline {
    parameters{
        choice(
            name: 'ENVIRONMENT',
            choices: ['Development','Production'],
            description: 'Select deployment environment'
            )
    }
    agent any
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

        stage('Deploy') {
            environment{
                DEPLOY_SERVER= "production-server"
            }
            steps {
                sh '''
                echo "$APP_NAME"
                echo "$ENVIRONMENT"
                echo "$DEPLOY_SERVER"
                '''
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
