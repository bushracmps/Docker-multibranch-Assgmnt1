pipeline {
	agent {
		label {
		label "slave1"
		customWorkspace "/root/docker"
		}
	    }
	stages {
		stage ("install docker"){
		steps {
			sh ''' 
			yum install docker -y
			systemctl  start docker
			systemctl enable docker
			'''
			}
				}
		stage ("docker build-23Q1") { 
			steps { 
				sh '''
				rm -rf *
				git clone https://github.com/bushracmps/Docker-multibranch-Assgmnt1.git
				docker pull httpd
    			
				chmod -R 777 /Docker-multibranch-Assgmnt1/multibranch-project/index.html
				docker run -itdp 80:80 --name 23Q1 httpd
				docker cp /Docker-multibranch-Assgmnt1/multibranch-project/index.html master:/usr/local/apache2/htdocs
  				'''
				}
				}
          }
 }      
