pipeline {
    agent any
    stages {
        stage('SCM') {
        steps {
            git branch: 'main', url: 'https://github.com/coirne/Projet_final_test_flask.git'
              }
        }
        
        stage('Start manager'){
          agent {
              docker { 
                  args '-u 0:0'
                  image 'ahmed24khaled/ansible-management'
                  reuseNode true
              }
              
          }
          steps {
                sh 'ls /_ansible'
                sh 'echo "172.17.0.2 ecdsa-sha2-nistp256 AAAAE2VjZHNhLXNoYTItbmlzdHAyNTYAAAAIbmlzdHAyNTYAAABBBDmqkTYoZkaSWo/mjuQgkiAwXCpfT6FYUOypwBxZ5Id8E9p0vsUxn57Skk+2ce2ujWQLLMZ+LOaMoBdgbMADOAs=" > /root/.ssh/known_hosts'
                sh 'ansible-playbook -vvvv -i /var/jenkins_home/workspace/Projet_final_test_flask/hosts  /var/jenkins_home/workspace/Projet_final_test_flask/playbook.yml'
          }
    }
}  
}
