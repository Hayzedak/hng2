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
- if you are using your ubuntu on wsl or vagrant, add your ubuntu ip address to your to local machine to serve as local host e.g *172.30.226.117    localhost*.

5. test by going to your browser:
`localhost` => Frontend

`localhost/api` => Backend 

`localhost/docs` => Backend Docs

`localhost/redoc` => Backend Redoc

`localhost: 8080` => Adminer

`localhost: 8090` => Proxy Manger GUI

































Each directory has its own README file with detailed instructions specific to that part of the application.

## Getting Started

To get started with this template, please follow the instructions in the respective directories:

- [Frontend README](./frontend/README.md)
- [Backend README](./backend/README.md)

