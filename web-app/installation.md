# Docker Installation

If you have successfully installed the API, you have to install the web-app.
Move to the parentdirectory of your API-Installation by typing

```bash
   $ cd ..
   ```
, clone the repo of Human Connection by typing

 ```bash
   $ git clone https://github.com/Human-Connection/WebApp.git

   ```
and change to its directory with

```bash
   $ cd WebApp
   ```
.
The following command, again, needs root-privileges, on Linux-Systems we strongly recommend the use of sudo, on Windows-Systems you will need admin-rights or you should use the LSS (Linux Sub System).

Determine the web-app of Human Connection by running 

```bash
$ sudo docker-compose up
```
After this is done, reload your installation in your browser: [http://localhost:3030](http://localhost:3030), contributions at [http://localhost:3030/contributions](http://localhost:3030/contributions) or users at [http://localhost:3030/users](http://localhost:3030/users).

Congratulations! Now your web-app of Human Connection is running too. :-)


# Local Installation

Run:

```bash
# install dependencies
$ yarn install

# serve with hot reload at localhost:3000
$ yarn run dev

# build once and launch server
$ yarn run build
$ yarn run start
```

For detailed explanation on how things work, checkout the [Nuxt.js docs](https://github.com/nuxt/nuxt.js).

## Env Vars

> More information on environment variables can be found in the [documentation \(WIP\)](https://docs.human-connection.org/environments/docker-test-production/docker-configuration.html)

#### Test Logins

| Role | E-Mail | Password |
| :--- | :--- | :--- |
| Admin | test@test.de | 1234 |
| Moderator | test2@test2.de | 1234 |
| User | test3@test3.de | 1234 |

#### Access over WiFi

In order to make your web app accessible from your local WiFi you have to
configure `WEBAPP_HOST`, `WEBAPP_BASE_URL` and `API_HOST` depending on your
IP address within that network. E.g. on Linux you can check your IP address with
`ip addr`. Here's an example `.env` file for an IP address `192.168.178.42`:

```sh
# .env 
WEBAPP_HOST     = 192.168.178.42
WEBAPP_BASE_URL = http://192.168.178.42:3000
API_HOST        = 192.168.178.42
```

You can use this configuration e.g. to test the webapp from your mobile phone.


#### Styleguide

The Developer Style Guide provides important infos about components and styles. To start it simply type:

```bash
$ yarn run styleguide
```

When built you can open it at [http://localhost:6060](http://localhost:6060)

#### Backpack

We use [backpack](https://github.com/palmerhq/backpack) to watch and build the application, so you can use the latest ES6 features \(module syntax, async/await, etc.\).

