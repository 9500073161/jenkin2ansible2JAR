pipeline {
    agent any
    
    tools
    {
       maven "maven"
    }
     
    stages {
      stage('checkout') {
           steps {
                git branch: 'main', url: 'https://github.com/Yash-9/Congifxyz.git' 
          }
        }
         stage('Tools Init') {
                          steps {
                             script {
                                     sh 'ansible --version'
                                    }
                                 }
                             }
     
        
         stage('Execute maven') {
           steps {
                 sh 'mvn build'             
                 }
        }              
         stage('Ansible Deploy') {
             
            steps {                          
                 sh "ansible-playbook webdeploy.yml -i localhost --user jenkins --key-file ~/.ssh/id_rsa"        
                  }
        }
    }
}
