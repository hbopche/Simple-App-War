pipeline {
    agent any
    
    tools
    {
       maven "Maven"
    }
     
    stages {
      stage('checkout') {
           steps {
             
                git branch: 'master', url: 'https://github.com/hbopche/Simple-App-War.git'
             
          }
        }
         stage('Build') {
           steps {
             
                sh 'mvn package'             
          }
        }
        stage('Ansible Deploy') {
            steps { 
               sh "ansible-playbook main.yml -i inventories/dev/hosts --user jenkins --key-file ~/.ssh/id_rsa"  
            }
        }
    }
}
