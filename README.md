# PassWall Server

![GitHub](https://img.shields.io/github/license/pass-wall/passwall-server)
![GitHub issues](https://img.shields.io/github/issues/pass-wall/passwall-server)
[![Build Status](https://travis-ci.org/pass-wall/passwall-server.svg?branch=master)](https://travis-ci.org/pass-wall/passwall-server) 
[![Coverage Status](https://coveralls.io/repos/github/pass-wall/passwall-server/badge.svg?branch=master)](https://coveralls.io/github/pass-wall/passwall-server?branch=master)
[![Docker Pull Status](https://img.shields.io/docker/pulls/passwall/passwall-server)](https://hub.docker.com/u/passwall/)  
[![Deploy](https://www.herokucdn.com/deploy/button.svg)](https://heroku.com/deploy)

**PassWall Server** is the core backend for open source password manager PassWall platform. Using this server, you can safely store your passwords and access them from anywhere. 

## Clients
PassWall can be used by these clients or you can write your own client by using [API Documentation](https://documenter.getpostman.com/view/3658426/SzYbyHXj)     
[PassWall Web](https://github.com/pass-wall/passwall-web)  
[PassWall Desktop](https://github.com/pass-wall/passwall-desktop)  
[PassWall Mobile](https://github.com/pass-wall/passwall-mobile)  

The screenshot of Passwall Desktop working with Passwall Server is as follows  
![PassWall Desktop Screenshot](https://www.yakuter.com/wp-content/yuklemeler/PassWall-Desktop-Screenshot.png "PassWall Desktop")

## API Documentation
API documentation available at:   
[Click to see at Public Postman](https://documenter.getpostman.com/view/3658426/SzYbyHXj)   

## DEMO
Demo is available at: [Demo Server](https://passwall-demo.herokuapp.com)  
You can test it with clients or make requests with API tools like Postman with the credentials below:  
**Username:** passwall  
**Password:** password


## What's possible with PassWall Server?
Currently, this project is focused on storing URL, username and password which is basically called **Login** at PassWall.

An admin can;  
- View and search logins
- Create login with automatically generated strong password
- Update login
- Delete login
- Import logins from other password managers
- Export logins as CSV format

## Authentication
This server uses **JWT Token** to secure endpoints. So user must generate token with /auth/signin first. Then with generated token, all endpoints in API documentation can be reachable.  
  
User information for signin is in **config.yml** file.

## Environment Variables
These environment variables are accepted:

**Server Variables:**
- PORT
- PW_SERVER_USERNAME
- PW_SERVER_PASSWORD
- PW_SERVER_PASSPHRASE
- PW_SERVER_SECRET
- PW_SERVER_TIMEOUT  
  
**Database Variables**
- PW_DB_DRIVER
- PW_DB_DBNAME
- PW_DB_USERNAME
- PW_DB_PASSWORD
- PW_DB_HOST
- PW_DB_PORT

## Development usage
Install Go to your computer. Pull the server repo. Execute the command in server folder.

```
go run main.go
```

The server uses config file end environment variables. If you want to set variables manually, just change **config-sample.yml** to **config.yml** in **store** folder.

## Docker

```
docker-compose up --build
```
or
```
docker pull passwall/passwall-server
cp ./store/config-sample.yml ./store/config.yml
docker run --name passwall-server --rm -v $(pwd)/store:/app/store -p 3625:3625 passwall-server
```

## Import
There are different kinds of password managers. Almost all of them can export login information as CSV file. Here is an example CSV file (let's say example.csv).  
![example csv](https://www.yakuter.com/wp-content/yuklemeler/example-csv.png "Example CSV File")  
  
You need to fill the import form as below picture.  
![passwall-server import](https://www.yakuter.com/wp-content/yuklemeler/gpass-import-csv.png "Import Form and Request Example")
