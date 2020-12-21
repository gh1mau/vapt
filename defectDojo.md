### defectDojo docker setup</u>



#### <mark><u>Install docker:</u></mark>



`sudo apt update`



Next, install a few prerequisite packages which let apt use packages over HTTPS:

`sudo apt install apt-transport-https ca-certificates curl software-properties-common`



Then add the GPG key for the official Docker repository to your system:

`curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -`



Add the Docker repository to APT sources:

`sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu bionic stable"`



Next, update the package database with the Docker packages from the newly added repo:

`sudo apt update`



Make sure you are about to install from the Docker repo instead of the default Ubuntu repo:

`apt-cache policy docker-ce`



Finally, install Docker:



`sudo apt install docker-ce`



Docker should now be installed, the daemon started, and the process enabled to start on boot. Check that it’s running:

`sudo systemctl status docker`



##### <u>Install docker compose</u>



`sudo curl -L https://github.com/docker/compose/releases/download/1.27.4/docker-compose-uname -s-uname -m -o /usr/local/bin/docker-compose`



Next we’ll set the permissions:

`sudo chmod +x /usr/local/bin/docker-compose`



Then we’ll verify that the installation was successful by checking the version:

`docker-compose --version`



##### <u>Setup defectDojo docker</u>

Clone defectDojo repo:

`git clone https://github.com/DefectDojo/django-DefectDojo`



Building:

`cd django-DefectDojo`
`sudo docker-compose up`



Running the container:
`sudo docker-compose up`



Remove the container:

`sudo docker-compose down`



Create admin user for defectDojo:
`sudo docker-compose exec uwsgi /bin/bash -c 'python manage.py createsuperuser`



localhost:8080 or x.x.x.x:8080 to access defectDojo






