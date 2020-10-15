pipeline {
    agent any
    tools {
        maven 'Maven 3.3.9'
        jdk 'jdk8'
    }
    stages {
        stage ('Initialize') {
            steps {
                sh '''
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${M2_HOME}"
                '''
            }
        }

        stage ('Build') {
            when {
                expression { 
                    BRANCH_NAME == 'master'
                }   
            }
            steps {
                sh 'mvn -Dmaven.test.failure.ignore=true install' 
            }
            post {
                always {
                    echo "Hola"
                }
                success {
                    junit 'target/surefire-reports/**/*.xml' 
                }
            }
        }
    }
}
