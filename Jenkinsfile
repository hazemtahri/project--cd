
pipeline {

	agent any

  
	stages {
		
		stage('Git ') {
            steps {
                echo 'pulling Main Project from git ...';
                git branch: 'main', credentialsId: 'git', url: 'https://github.com/hazemtahri/project--cd.git'            }
        }
    


 

stage('Ansible App build ') {
            steps {
                
                sh 'ansible-playbook ansible/build.yml -i ansible/inventory/hosts.yml'
                         }
        }

	   stage('Ansible Docker build and Start Container') {
            steps {
                sh 'ansible-playbook ansible/docker.yml -i ansible/inventory/hosts.yml'
                         }
        }
        stage('Ansible Tag Push to Dockerhub ') {
            steps {
                sh 'ansible-playbook ansible/docker-registry.yml -i ansible/inventory/hosts.yml'
                         }
        }
	}
	}