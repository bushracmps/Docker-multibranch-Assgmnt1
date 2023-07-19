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
		stage ("docker build-23Q3") { 
			steps { 
				sh '''
				rm -rf *
				git clone https://github.com/bushracmps/Docker-multibranch-Assgmnt1.git -b 23Q3
				docker pull httpd
    				docker rm 23Q3
				chmod -R 777 /tmp/multibranch-project/index.html
				docker run -itdp 8081:80 --name 23Q3 httpd
				docker cp /tmp/Docker-multibranch-Assgmnt1/index.html 23Q3:/usr/local/apache2/htdocs
  				'''
				}
				}
		
			}
		}
