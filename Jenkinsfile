pipeline {
    agent any
    tools {
        maven 'Maven 3.3.9'
        jdk 'jdk8'
    }
    environment {
        NEW_VERSION = '1.3.0'
        USERC = credentials('server-credentials');
        PWD = '1234'
    }
    /*
         environment {
        AWS_ACCESS_KEY_ID     = credentials('jenkins-aws-secret-key-id')
        AWS_SECRET_ACCESS_KEY = credentials('jenkins-aws-secret-access-key')
    }
    */
    stages {
        stage ('Initialize') {
            steps {
                sh '''
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${M2_HOME}"
                    echo "building version ${NEW_VERSION}"
                    echo "usuario credentials ${USERC}"
                    echo "usuarionombre credentials ${USERC_USR}"
                     echo "usuarionpass credentials ${USERC_PWD}"
                '''
            }
        }

        stage ('Build') {
         /*when {
                expression { 
                    BRANCH_NAME == 'master'
                }   
            }
          */  
            steps {
                sh 'mvn -Dmaven.test.failure.ignore=true install' 
            }
            post {
              /* always {
                    echo "Hola"
                }*/  
                success {
                    junit 'target/surefire-reports/**/*.xml' 
                }
            }
        }
    }
}
