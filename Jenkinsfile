pipeline {
   agent any
tools {
    maven 'Maven 3.6.3'
}
   stages {
      stage('clean workspace') {
         steps {
            cleanWs()
         }
      }
      
      stage('checkout'){
          steps{
              dir('code'){
                  git 'https://github.com/babusatti/my-apprepo.git'
              }
          }
      }
      stage('build'){
          steps{
              script{
                  sh label: '', script: '''cd code
mvn clean install'''
              }
          }
      }
      stage('Deployment'){
          steps{
              script{
                  sshPublisher(publishers: [sshPublisherDesc(configName: 'dev1', transfers: [sshTransfer(cleanRemote: false, excludes: '', execCommand: 'ls -lrt', execTimeout: 120000, flatten: false, makeEmptyDirs: false, noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: 'deploy/dev2/pc', remoteDirectorySDF: false, removePrefix: 'code/target', sourceFiles: 'code/target/*.jar')], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: true)])
              }
                  
          }
      }
   }
  
}



==================================

pipeline {
   agent any

   stages {
      stage('clean workspace') {
         steps {
            cleanWs()
         }
      }
      
      stage('checkout code'){
          steps{
              dir('code'){
                  git branch: 'develop', url: 'https://github.com/babusatti/yorrepo.git'
              }
              dir('script'){
                  git branch: 'master', url: 'https://github.com/babusatti/yourrepo.git'
              }
          }
      }
          
          
      stage('build'){
          steps{
             
                  sh '********call gradle wrapper srcipt****'
              
          }
      }
      stage('scripts'){
          steps{
              sh '********permission-confog.pro-any other****'
          }
      }
      stage('Artifactory'){
          steps{
              script{
                 sh '********uploadglobal.sh****'
              }
                  
          }
      }
      stage('email') {
            steps {
                
               emailext attachmentsPattern: '**/*.png', body: 'Please find the sonar reports', recipientProviders: [developers(), requestor()], subject: 'Sonar-Reports', to: 'sattibabu0247@gmail.com'
            }
            
        }
   }
  
}
