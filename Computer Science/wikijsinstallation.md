# Wiki JS Installation

These are the steps I took to attempt to install Wiki JS on my Raspberry Pi, though I later realized that the Postgres installation was unneccessary, and that I could not continue past the Segmentation Fault.

Compiled using [simplilearn's tutorial for installing Docker](https://www.simplilearn.com/tutorials/docker-tutorial/raspberry-pi-docker), [the official Postgres on Debian tutorial](https://www.postgresql.org/download/linux/debian/), [pimylifeup's Raspberry Pi focused Postgres guide](https://pimylifeup.com/raspberry-pi-postgresql/), as well as [the computingforgeeks tutorial of installing postgres on Debian](https://computingforgeeks.com/how-to-install-postgresql-db-on-debian/)

1. Update Raspberry Pi
In terminal:

	sudo apt update
	sudo apt upgrade -y

2. Install PostgresSql
A. Prepare installation

	sudo sh -c 'echo "deb https://apt.postgresql.org/pub/repos/apt $(lsb_release -cs)-pgdg main" > /etc/apt/sources.list.d/pgdg.list'
	wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo apt-key add -
	sudo apt-get update
	sudo apt-get -y install postgresql

B. Configure Installation
	sudo su postgres
	createuser pi -P --interactive
	Password: vetdoor7990, Superuser yes
	psql
	CREATE DATABASE pi;
	exit

3. Install Docker
Docker has a great install script that you can get from this curl command:

	curl -fsSL https://get.docker.com -o get-docker.sh

Definitely couble check that it hasnt been altered, but once approved, you can just run it.

	sudo sh get-docker.sh

We also want to make sure our standard user has rights to run containers, 

	sudo usermod -aG docker Pi

At this point, we have to reboot to get docker initialized. You can test this by running

	docker version 

If you haven't rebooted, you will see the data for the client, but the server info will trigger a permission denied message.

4. Write the docker compose file

	mkdir ~/wikijs
	cd ~/wikijs
	sudo nano ~/wikijs/docker-compose.yml

This starts you writing the settings for the docker container we will use for wikijs

	version: "3"
	services:

	  db:
		image: postgres:15-alpine
		environment:
		  POSTGRES_DB: wiki
		  POSTGRES_PASSWORD: wcp2019!
		  POSTGRES_USER: wikijs
		logging:
		  driver: "none"
		restart: unless-stopped
		volumes:
		  - db-data:/var/lib/postgresql/data

	  wiki:
		image: ghcr.io/requarks/wiki:2
		depends_on:
		  - db
		environment:
		  DB_TYPE: postgres
		  DB_HOST: db
		  DB_PORT: 5432
		  DB_USER: wikijs
		  DB_PASS: wcp2019!
		  DB_NAME: wiki
		restart: unless-stopped
		ports:
		  - "80:3000"

	volumes:
	  db-data:

close the text editor (Is it VIM or Emacs? IDK) with CTRL+X, Y, then the Enter key

5. Start up wiki JS
To start the docker container:

	docker compose up -d

This, of course, is where the segmentation fault occurs. 