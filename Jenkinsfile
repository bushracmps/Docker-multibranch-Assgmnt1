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
  			 sudo rm -rf *
			sudo yum install docker -y
			sudo systemctl  start docker
			sudo systemctl enable docker
			'''
			}
				}
		stage ("docker build-23Q2") { 
			steps { 
				sh '''
				sudo rm -rf *
				sudo git clone https://github.com/bushracmps/Docker-multibranch-Assgmnt1.git -b 23Q3
				sudo docker pull httpd
    				
    				sudo docker rm 23Q3
				sudo docker run -itdp 90:80 --name 23Q3 httpd
    				sudo chmod -R 777 /root/docker/Docker-multibranch-Assgmnt1/index.html
				sudo docker cp /root/docker/Docker-multibranch-Assgmnt1/index.html 23Q3:/usr/local/apache2/htdocs
  				'''
				}
				}
          }
 }      
