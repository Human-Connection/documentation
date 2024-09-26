# Installation

## Setup the API via Docker

### Installation

Make sure you have a recent version of [Docker](https://www.docker.com/) and [Docker Compose](https://docs.docker.com/compose/) installed on your system.


If you have, clone the repo of Human Connection in a console(-window) by typing

 ```bash
   $ git clone https://github.com/Human-Connection/API.git
   ```
and change to its directory with

```bash
   $ cd API
   ```
.

The following command needs root-privileges, on Linux-Systems we strongly recommend the use of sudo, on Windows-Systems you will need admin-rights or you should use the LSS (Linux Sub System).

Determine now the installed version, running 

```bash
$ sudo docker-compose up --build
```
. You see no more changes in your terminal-window?
Congratulations: Your server is now running at [http://localhost:3030](http://localhost:3030) which you can load in your browser. Some contributions wait for you at [http://localhost:3030/contributions](http://localhost:3030/contributions).

For debugging you can run:

```bash
$ docker-compose run --rm --service-ports api yarn run dev:debug
```

And debug your app with [Chrome Dev Tools](chrome://inspect).

### Setting up the database seeder for local development 

Change the configuration in `config/local-development.json` or `config/local.json` and rerun `docker-compose up --build`.

If both files do no exist, create a `config/local.json` , copy the content of `config/local.example.json` into it and rerun `docker-compose up --build`.

Reference : https://github.com/lorenwest/node-config/wiki/Configuration-Files

#### Local Staging Environment

To get an environment which is close to production, run the following:

```bash
$ docker-compose -f docker-compose.yml -f docker-compose.staging.yml up --build
```

### Testing

Run the entire test suite with:

```bash
$ docker-compose run --rm api yarn run test
```

If you want you can run specific tests:

```bash
$ docker-compose run --rm api yarn run mocha
$ docker-compose run --rm api yarn run cucumber
```

## Setup the API locally

### Getting Started

> We recommend to install the project locally for the best development ease and performance.
>For windows users we recommend that either you use the docker setup or the linux sub system on windows when setting up the API

Getting up and running is as easy as 1, 2, 3, 4, 5 ... 6.

1. Make sure you have [NodeJS](https://nodejs.org/), [yarn](https://yarnpkg.com), [mongoDB](https://www.mongodb.com/download-center#community) installed.
2. Clone this repo

   ```bash
   $ git clone https://github.com/Human-Connection/API.git
   ```

3. Install your dependencies

   ```bash
   $ cd ./API
   $ yarn
   ```

##Setting up the database seeder for local development \(recommended\)

   Run

   ```bash
   $ cp config/local.example.json config/local.json
   ```

  or copy the content in config/local.example.json to config/local.json

4. Setup local mailserver \(optional\)

   > **Note:** _You only have to start that mailserver when you want to register, reset your password or test emails in any form, it does not affect the rest of the application._

   Install the [MailDev](https://github.com/djfarrelly/MailDev) server to catch all sent emails in a nice web interface.

   ```bash
   # install mail dev (only has to be done once)
   $ yarn global add maildev

   # start the server, it will output the web url
   # which normally is http://localhost:1080
   $ maildev
   ```

   You could also insert your smtp credentials into the local.json but that is not recommended as all emails would be sent to the given addresses which should not happen in development.

6. Start server

   You don't have a background process running for mongodb? Just open another terminal and run:

   ```bash
     # open up another terminal and run:
   $ yarn run mongo
   # or if you are on windows, run:
   $ yarn run mongo:win
   ```

   > **IMPORTANT for Windows users:**
   >
   > * make sure you have mongo bin directory added to your PATH

   Start the API server with the following commands:

   ```bash
   $ yarn dev

   # without hot reload
   $ yarn start
   # you can customize the environment like this:
   $ NODE_ENV=production yarn start
   ```

Now, your API should be running at [http://localhost:3030](http://localhost:3030). If you seeded your database, you will see some contributions at [http://localhost:3030/contributions](http://localhost:3030/contributions).

### Local Configuration

You can override any default configuration in `config/local.json`. You can find a list of availabe defaults in `config/default.json`. See [node-config documentation](https://github.com/lorenwest/node-config/wiki/Configuration-Files) for details.

E.g. if you want to access the server from your mobile over WiFi, you should replace `localhost` in your settings with your IP address in the local network:

```javascript
{
  "host": "192.168.188.22",
  "baseURL": "http://192.168.188.22:3030",
  "frontURL": "http://192.168.188.22:3000"
}
```

### Local Testing

Test Logins

| Role | E-Mail | Password |
| :--- | :--- | :--- |
| Admin | test@test.de | 1234 |
| Moderator | test2@test2.de | 1234 |
| User | test3@test3.de | 1234 |

Run the entire test suite with:

```bash
$ yarn run test
```

If you want you can run specific tests:

```bash
$ yarn run mocha
$ yarn run cucumber
```

## Scaffolding

Feathers has a powerful command line interface. Here are a few things it can do:

```bash
$ yarn global add feathers-cli             # Install Feathers CLI

$ feathers generate service               # Generate a new Service
$ feathers generate hook                  # Generate a new Hook
$ feathers generate model                 # Generate a new Model
$ feathers help                           # Show all commands
```

