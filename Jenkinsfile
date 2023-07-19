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
				git clone https://github.com/bushracmps/Docker-multibranch-Assgmnt1.git -b 23Q1
				docker pull httpd
				chmod -R 777 /root/docker/Docker-multibranch-Assgmnt1/index.html
				docker run -itdp 80:80 --name 23Q1 httpd
				docker cp /root/docker/Docker-multibranch-Assgmnt1/index.html 23Q1:/usr/local/apache2/htdocs
  				'''
				}
				}
          }
 }      
