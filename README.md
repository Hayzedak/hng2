# Full-Stack FastAPI and React Template project

Welcome to the Full-Stack FastAPI and React template repository. This repository serves as a demo application for interns, showcasing how to set up and run a full-stack application with a FastAPI backend and a ReactJS frontend using ChakraUI.

## Project Structure

The repository is organized into two main directories:

- **frontend**: Contains the ReactJS application.
- **backend**: Contains the FastAPI application and PostgreSQL database integration.

## Manual deployment 

**1. Using ubuntu on your local machine**

 - update packages: `sudo apt update`
 - install git: `sudo apt install git`
 - clone the project repository: `git clone https://github.com/Hayzedak/hng2.git`

**2. Install prerequisites**

- install poetry: `curl -sSL https://install.python-poetry.org | python3 -`. 

  Add poetry to path using `nano ~/.bashrc` and  `export PATH="$HOME/.local/bin:$PATH"
`

  Save the file and reload the shell cofiguration file `source ~/.bashrc
`

- install postgreSQL: `sudo apt install postgresql`. Create PostgreSQL user and database using the information in the *./backend/.env* file.

- install Node.js and npm: `sudo apt update` `sudo apt install nodejs npm
`

**3. setting up backend**

- navigate to the backend directory: `cd backend`
- install dependencies using Poetry: `poetry install`
- set up database tables: `poetry run bash ./prestart.sh`
- run the backend server: `poetry run uvicorn app.main:app --reload`

**4. setting up frontend**

- navigate to the frontend diretory: `cd frontend`
- Install dependencies: `npm install`
- run the frontend development server: `npm run dev`
- if you are using your ubuntu on wsl or vagrant, add your ubuntu ip address to your to local machine host file to serve as local host e.g *172.30.226.117    localhost*.

**5. test by going to your browser:**

`localhost` => Frontend

`localhost/api` => Backend 

`localhost/docs` => Backend Docs

`localhost/redoc` => Backend Redoc

`localhost: 8080` => Adminer

`localhost: 8090` => Proxy Manger GUI


# Deploying to EC2

**1. install Docker:** 

Upadte package list

`sudo apt-get update`

Install required packages

`sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    software-properties-common`

Add official docker GPG key

`curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -` 

Add docker repository to APT sources

`sudo add-apt-repository \
    "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
    $(lsb_release -cs) \
    stable"`

Update package list again

`sudo apt-get update`

Install docker

`sudo apt-get install docker-ce`

Verify docker is insatlled correctly and active(running)
`sudo systemctl status docker`

Add your user to docker group to manage docker as non-root user

`sudo usermod -aG docker $USER`



**2. install Docker Compose:**

Download latest version odf docker compose

`sudo curl -L "https://github.com/docker/compose/releases/download/$(curl -s https://api.github.com/repos/docker/compose/releases/latest | grep -oP '"tag_name": "\K(.*)(?=")')" /usr/local/bin/docker-compose`

Add executable permissions

`sudo chmod +x /usr/local/bin/docker-compose`

Verify docker compose is installed

`docker-compose --version`


**3. Clone repository and update .env files:**

- clone the repository on EC2

- update your VITE_API_URL in the frontend .env file

VITE_API_URL=https://<your_domain>

**4. Build and run containers:**

- `docker-compose up -d`

**5. Configure Nginx Proxy Manager:**

- set up A records for your domain and sub-domains.

- open http://<your_domain:8090> and use default credentials to login

- set up proxy host for your backend and frontend. Map your domain name to the service name of the frontend container and the port the container is listening on internally.

Also, enable SSL certificate using Let's Encrypt and enable Force SSL.

- set up proxy host for your adminer. Mapping your sub domian name to the service name of the adminer container and port. example: db.<your_domain>

- set up proxy host for your Nginx proxy manager. Mapping your sub domian name to the service name of the NPM container and port. example: proxy.<your_domain>

**5. Testing application:**

- access your application:

*<your_domain>* => Frontend

*<your_domain/api>* => Backend

*<your_domain/docs>* => Backend docs

*<your_domain/redoc>* => Backend redoc

*<proxy.your_domain>* => proxy manager GUI

*<db.your_domain>* => Adminer


























Each directory has its own README file with detailed instructions specific to that part of the application.

## Getting Started

To get started with this template, please follow the instructions in the respective directories:

- [Frontend README](./frontend/README.md)
- [Backend README](./backend/README.md)

