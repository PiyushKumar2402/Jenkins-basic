pipeline {
    agent any
// if we have multiple linux commands then specify it as sh ''' and when it ends then again ''' this is how it works
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
            steps {
                echo 'Deploying application'
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
