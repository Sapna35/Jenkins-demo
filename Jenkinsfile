pipeline{
  agent any

  tools{
    maven 'Maven3'
    jdk 'Java17'
  }
  stages{
    stages('Checkout Code'){
      steps{
        git branch:'main',
          url:'github.com/Sapna35/Jenkins-demo.git'
      }
    }
    stages('Build with Maven'){
      steps{
        sh 'mvn clean package'
      }
    }
    stages('Test'){
      steps{
        echo"Running Tests..."
        }
      }
    stages('Deploy to Tomcat using Ansible'){
      steps{
        steps{
          ansiblePlaybook
          credentialsId: 'app-sh',
          Inventory: 'ansible/hosts',
          playbook: 'ansible/tomcat.yml'
           }
    }
  }
}

