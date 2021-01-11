### pwndoc docker setup (ubuntu 18.04)

1. [Install docker](https://github.com/gh1mau/vapt/blob/main/pwndoc.md#install-docker)

2. [Install docker-compose](https://github.com/gh1mau/vapt/blob/main/pwndoc.md#install-docker-compose)

3. [Setup pwndoc docker](https://github.com/gh1mau/vapt/blob/main/pwndoc.md#setup-pwndoc-docker)

4. [Troubleshooting](https://github.com/gh1mau/vapt/blob/main/pwndoc.md#troubleshooting)

---

#### <u>Install docker:</u>

1. ```
   sudo apt update
   ```

2. Next, install a few prerequisite packages which let apt use packages over HTTPS:
   
   ```
   sudo apt install apt-transport-https ca-certificates curl software-properties-common
   ```

3. Then add the GPG key for the official Docker repository to your system:
   
   ```
   curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
   ```

4. Add the Docker repository to APT sources:
   
   ```
   sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu bionic stable"
   ```

5. Next, update the package database with the Docker packages from the newly added repo:
   
   ```
   sudo apt update
   ```

6. Make sure you are about to install from the Docker repo instead of the default Ubuntu repo:
   
   ```
   apt-cache policy docker-ce
   ```

7. Finally, install Docker:
   
   ```
   sudo apt install docker-ce
   ```

8. Docker should now be installed, the daemon started, and the process enabled to start on boot. Check that it’s running:
   
   ```
   sudo systemctl status docker
   ```

---

#### <u>Install docker compose</u>

1. Download docker-compose:
   
   ```
   sudo curl -L https://github.com/docker/compose/releases/download/1.27.4/docker-compose-uname -s-uname -m -o /usr/local/bin/docker-compose
   ```

2. Next we’ll set the permissions:
   
   ```
   sudo chmod +x /usr/local/bin/docker-compose
   ```

3. Then we’ll verify that the installation was successful by checking the version:
   
   ```
   docker-compose --version
   ```

---

#### <u>Setup pwndoc docker</u>

1. Clone pwndoc repo:
   
   ```
   git clone https://github.com/pwndoc/pwndoc.git
   ```

2. Build and run Docker containers)
   
   ```
   cd pwndoc
   
   sudo docker-compose up -d --build
   ```

3. Display backend container logs:
   
   ```
   sudo docker-compose logs -f pwndoc-backend
   ```

4. Stop/ start the container:
   
   ```
   sudo docker-compose stop
   sudo docker-compose start
   ```

5. Remove container:
   
   ```
   sudo docker-compose down
   ```

6. Update pwndoc
   
       sudo docker-compose down
       git pull
       sudo docker-compose up -d --build

7. Application is accessible through 
   
   ```
   https://localhost:8443
   ```
   
   API is accessible through
   
   ```
    https://localhost:4242/api
   ```
   
   ```
    https://localhost:4242/api/users/init
   ```

8. Documentation:
   
   >  https://pwndoc.github.io/pwndoc/

---

#### <u>Troubleshooting</u>

1. If you got this error, it means the port that the container wants to use is already allocated, so we need to change it to other port number.
   
   ```
   ERROR: for pwndoc-frontend  Cannot start service pwndoc-frontend: driver failed programming external connectivity on endpoint pwndoc-frontend (239c1d41e7ed80679f62074add1795ecb7cfe0d75f50bb9c339c29c192b12a13): Bind for 0.0.0.0:8443 failed: port is already allocated
   ```
   
   Open docker-compose.yml:

> ```
>    pwndoc-frontend:
>        build: ./frontend
>        image: yeln4ts/pwndoc:frontend
>        container_name: pwndoc-frontend
>        restart: always
>        ports:
>          - 8443:8443
>        networks:
>          - backend
> ```

 Change the ports: 

> ```
>    pwndoc-frontend:
>        build: ./frontend
>        image: yeln4ts/pwndoc:frontend
>        container_name: pwndoc-frontend
>        restart: always
>        ports:
>          - 8888:8443
>        networks:
>          - backend
> ```

      

    And the application can be access through:

```
    https://<ip-address>:8888
```
