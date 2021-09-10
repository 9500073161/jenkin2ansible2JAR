pipeline {
    agent any
    
    tools
    {
       maven "maven"
    }
     
    stages {
      stage('checkout') {
           steps {
                git branch: 'master', url: 'https://github.com/Yash-9/Congifxyz.git' 
          }
        }
         stage('Tools Init') {
                          steps {
                             script {
                                    echo "PATH = ${PATH}"
                                    echo "M2_HOME = ${M2_HOME}"
                                    def tfHome = tool name: 'Ansible'
                                    env.PATH = "${tfHome}:${env.PATH}"
                                    sh 'ansible --version'
                                    }
                                 }
                             }
     
        
         stage('Execute maven') {
           steps {
                 sh 'mvn package'             
                 }
        }              
         stage('Ansible Deploy') {
             
            steps {                          
                 sh "ansible-playbook webdeploy.yml -i localhost --user jenkins --key-file ~/.ssh/id_rsa"        
                  }
        }
    }
}
