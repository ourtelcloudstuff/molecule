pipeline {
    agent any  
             
         stages {
                  stage ('GIT checkout'){
                    steps {
                           checkout scm
                           }
                     }
                            stage ('Set env') {
                               steps {
                                      sh '''
                                      python -m virtualenv virtenv
                                      . virtenv/bin/activate
                                      python -m pip install molecule docker
                                      '''
                                     }
                                 }
                                      stage ('Test Infra'){
                                        steps {
                                               sh '''
                                               . virtenv/bin/activate
                                               cd roles/ansible-webhost/
                                               molecule test
                                               '''
                                               }
                                            }
                                            
 						stage ('Deploy Playbooks'){
                            	                steps {
                                                     sh 'sudo ansible-playbook deploy.yml'
			                            }
			                        }     
	          
                     }
	    
}
