### defectDojo docker setup (ubuntu 18.04)

#### <u>Install docker:</u>

1. ```bash
   sudo apt update
   ```

2. Next, install a few prerequisite packages which let apt use packages over HTTPS:
   
   ```bash
   sudo apt install apt-transport-https ca-certificates curl software-properties-common
   ```

3. Then add the GPG key for the official Docker repository to your system:
   
   ```bash
   curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
   ```

4. Add the Docker repository to APT sources:
   
   ```bash
   sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu bionic stable"
   ```

5. Next, update the package database with the Docker packages from the newly added repo:
   
   ```bash
   sudo apt update
   ```

6. Make sure you are about to install from the Docker repo instead of the default Ubuntu repo:
   
   ```bash
   apt-cache policy docker-ce
   ```

7. Finally, install Docker:
   
   ```bash
   sudo apt install docker-ce
   ```

8. Docker should now be installed, the daemon started, and the process enabled to start on boot. Check that it’s running:
   
   ```bash
   sudo systemctl status docker
   ```

#### <u>Install docker compose</u>

1. Download docker-compose:
   
   ```bash
   sudo curl -L https://github.com/docker/compose/releases/download/1.27.4/docker-compose-uname -s-uname -m -o /usr/local/bin/docker-compose
   ```

2. Next we’ll set the permissions:
   
   ```bash
   sudo chmod +x /usr/local/bin/docker-compose
   ```

3. Then we’ll verify that the installation was successful by checking the version:
   
   ```bash
   docker-compose --version
   ```

#### <u>Setup defectDojo docker</u>

1. Clone defectDojo repo:
   
   ```bash
   git clone https://github.com/DefectDojo/django-DefectDojo
   ```

2. Building:
   
   ```bash
   cd django-DefectDojo
   
   sudo docker-compose build
   ```

3. Running the container:
   
   ```bash
   sudo docker-compose up
   ```

4. Stop the container:
   
   ```bash
   sudo docker-compose stop
   ```

5. Create admin user for defectDojo:
   
   ```bash
   sudo docker-compose exec uwsgi /bin/bash -c 'python manage.py createsuperuser'
   ```

6. Application is accessible through: 
   
   ```
   http://x.x.x.x:8080
   ```

7. Update defectDojo:
   
   ```bash
   sudo docker-compose down
   
   sudo docker pull defectdojo/defectdojo-django:latest
   
   sudo docker pull defectdojo/defectdojo-nginx:latest
   
   sudo docker-compose stop
   
   sudo docker-compose up -d
   
   sudo docker-compose exec uwsgi /bin/bash -c 'python manage.py migrate'
   ```
