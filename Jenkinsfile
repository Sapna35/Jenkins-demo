pipeline{
  agent any

  stages{
    stages('Checkout'){
      steps{
        git branch: 'main', url:'https://github.com/Sapna35/Jenkins-demo.git
      }
    }
    stages('Build'){
      steps{
        sh 'mvn clean package'
      }
    }
    stages('Deploy'){
      steps{
        sshagent(['app-server-key']){
          sh'''
          scp -o
          StrictHostKeyChecking=no target/*.jar
          ${APP_USER}@{APP_SERVER} :/home/ubuntu/
          ssh
          ${APP_USER}@${APP_SERVER} "pkill -f java || true && nohup java -jar /home/ubuntu/*.jar > app.log 2>&1 &"
          '''
        }
      }
    }
  }
}
