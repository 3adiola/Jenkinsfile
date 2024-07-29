pipeline {
    agent any

    parameters {
        choice(name: 'env', choices: ['prod', 'dev', 'test'], description: 'Environment')
    }
    
    stages {
        stage('One and Two') {
            parallel {
                stage('One') {
                    steps {
                        echo 'First'
                    }
                }
                stage('Two') {
                    steps {
                        echo 'Second'
                    }
                }
            }
        }
        stage('Three') {
            when {
                branch 'main'
            }
            steps {
                echo 'Third - when in main'
            }
        }
        stage('Four') {
            when {
                expression { return params.env == 'prod' }
            }
            steps {
                echo 'Fourth'
            }
        }
    }
    post {
        success {
            echo 'happy build'
        }
    }
}
