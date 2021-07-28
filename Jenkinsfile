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
tools {
    maven 'Maven 3.6.3'
}
   stages {
      stage('clean workspace') {
         steps {
            cleanWs()
         }
      }
      
      stage('checkout code'){
          steps{
              dir('code'){
                  git 'https://github.com/babusatti/my-apprepo.git'
              }
              dir('script'){
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
