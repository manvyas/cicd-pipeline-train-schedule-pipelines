pipeline {
  agent any
    stages {
      stage('build') {
        steps {
          withCredentials([usernamePassword(credentialsId:'deploy_server',usernameVariable:'USERNAME',passwordVariable:'USERPASS')]) {
           sshPublisher(
             failOnError: true,
             continueOnError: false,
             publishers: [
               sshPublisherDesc(
                 configName: 'staging',
                 sshCredentials: [
                                    username: "$USERNAME",
                                    encryptedPassphrase: "$USERPASS"
                                ],
         
                   transfers: [
                                    sshTransfer(
                                        sourceFiles: 'C:/Program Files (x86)/Jenkins/workspace/train_schedule',
                                        removePrefix: 'C:/Program Files (x86)/Jenkins/workspace',
                                        remoteDirectory: '/tmp',
                 )
               ]
             )
          ]
         )
          }
       }
      }
     }
   }
