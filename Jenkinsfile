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
		stage ("docker build-23Q1") { 
			steps { 
				sh '''
				sudo rm -rf *
				sudo git clone https://github.com/bushracmps/Docker-multibranch-Assgmnt1.git -b 23Q1
                                sudo docker pull httpd
				sudo docker run -itdp 80:80 --name 23Q1 httpd
    				sudo chmod 777 /root/docker/Docker-multibranch-Assgmnt1/index.html
				sudo docker cp /root/docker/Docker-multibranch-Assgmnt1/index.html 23Q1:/usr/local/apache2/htdocs
  				'''
				}
				}
				
		stage ("Change detect"){

			steps{
				sh '''
				sudo cd /root/docker
				sudo mkdir velocity
				sudo cd velocity/
				sudo git init
                                sudo chmod -R 777 /root/docker/velocity
				sudo echo "Hello All " >> /root/docker/velocity/index.html
				sudo chmod 777 /root/docker/velocity/index.html
                                sudo git checkout -b 23Q4
				sudo git add index.html
				sudo git commit -m "Change detected" 23Q4
				sudo git remote add origin https://github.com/bushracmps/Docker-multibranch-Assgmnt1.git
				sudo git push origin 23Q4
				'''
			}
					}
          }
		post { 
        		success {
				sh '''
				 sudo docker stop 23Q1
				sudo docker rm 23Q1
				sudo docker run -itdp 70:80 --name c1 httpd
				'''

        			}
    		     }
 }      
