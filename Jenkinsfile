pipeline {
  agent any
    stages {
      stage('build') {
        steps {
          withCredentials([usernamePassword(crdentialsId:'deploy_server',usernameVariable:'USERNAME',passwordVariable:'PASSWORD')])
           sshPublisher(
             failOnError: true
             continueOnError: false
             publishers: [
               sshPublisherDesc(
                 configName: 'staging'
                 sshCredentials: [
                                    username: "$USERNAME",
                                    encryptedPassphrase: "$USERPASS"
                                ],
                 transfers: [
                   execCommand: 'echo Hello World'
                   ]
         }
       }
     }
   }
