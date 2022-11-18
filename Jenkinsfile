
pipeline {

	agent any

  
	stages {
		
		stage('Git ') {
            steps {
                echo 'pulling Main Project from git ...';
                git branch: 'main', credentialsId: 'git', url: 'https://github.com/amineturki/projet-cd.git'            }
        }
    
  /*     stage('Docker Build and Push') {
       steps {
         withDockerRegistry([credentialsId: "docker-hub", url: ""]) {
           sh 'sudo docker build -t amineturki/cd:latest .'
           sh 'docker push amineturki/cd:latest '
         }
       }
     }
	 */
	 	stage('Ansible playbook for test') {
            steps {
                sh 'ansible-playbook playbook-test.yml'
                         }
        }
     	
    


 

stage('Ansible playbook for building the app') {
            steps {
                sh 'ansible-playbook ansible/docker.yml -i ansible/inventory/hosts.yml'
                         }
        }

	 
	}
	}
