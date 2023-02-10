pipeline {
    agent any
    stages {
    //     stage('Go-Test') {
	//  agent {
    //         docker {

    //           image 'maven:latest'
    //         }
    //        }
    //         steps {
    //             sh '''
    //             ls 
    //             pwd
    //             '''
    //         }
    //     }
    //     stage('Java-Test') {
	//  agent {
    //         docker {

    //           image 'maven:latest'
    //         }
    //        }
    //         steps {
    //             sh '''
    //             ls 
    //             pwd
    //             '''
    //         }
    //     }
         stage('SonarQube analysis') {
            agent {
                docker {
                  image 'sonarsource/sonar-scanner-cli:4.7.0'
                }
               }
               environment {
        CI = 'true'
        //  scannerHome = tool 'Sonar'
        scannerHome='/opt/sonar-scanner'
    }
            steps{
                withSonarQubeEnv('Sonar') {
                    sh "${scannerHome}/bin/sonar-scanner"
                }
            }
        }

        stage('sonarqube') {
            steps {
                sh '''
                ls 
                pwd
                '''
            }
        }
    
        stage('Go-Build') {
            steps {
                sh '''
                ls 
                pwd
                '''
            }
        }
        stage('Java-Build') {
            steps {
                sh '''
                ls 
                pwd
                '''
            }
        }
        stage('Build-Images') {
            steps {
                sh '''
                ls 
                pwd
                '''
            }
        }
        stage('Build-Images-2') {
            steps {
                sh '''
                ls 
                pwd
                '''
            }
        }
        stage('Push to Dockerhub') {
            steps {
                sh '''
                ls 
                pwd
                '''
            }
        }
    
    }

   post {
   
   success {
      slackSend (channel: '#development-alerts', color: 'good', message: "SUCCESSFUL: Application S4-EKTSS  Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]' (${env.BUILD_URL})")
    }

 
    unstable {
      slackSend (channel: '#development-alerts', color: 'warning', message: "UNSTABLE: Application S4-EKTSS  Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]' (${env.BUILD_URL})")
    }

    failure {
      slackSend (channel: '#development-alerts', color: '#FF0000', message: "FAILURE: Application S4-EKTSS Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]' (${env.BUILD_URL})")
    }
   
    cleanup {
      deleteDir()
    }
}
}
