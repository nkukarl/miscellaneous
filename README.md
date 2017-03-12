# miscellaneous

### Clone or download
```shell
git clone https://github.com/RealFireball/boca-api.git
```

Change directory into boca-api.

### Install nvm
```shell
curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.1/install.sh | bash
```

**Note:** If you get `nvm: command not found` after running the installing script,
your system may not have a [.bash_profile file] where the command is setup.
Simply create one with `touch ~/.bash_profile` and run the install script again.

If the above does not fix the problem, open your `.bash_profile` and add the following:

```shell
source ~/.bashrc
```

To verify the nvm has been installed, do:

```shell
command -v nvm
```

which should output `nvm` if the installation was successful.

### Install node and npm
```shell
node install 6.9.5
```

To verify node is installed properly, do:

```shell
node -v # should output v6.9.5
npm -v # should output 3.10.10.
```

**Note:** NPM is bundled with node as the package manager
for node modules.

### Install Docker
Follow instructions on the official website:

[Install Docker](https://docs.docker.com/engine/installation/)

[Install Docker for Mac](https://docs.docker.com/docker-for-mac/install/)

### Docker container
To run a MySQL container, do:

```shell
docker run --detach --name=boca-mysql --env="MYSQL_ROOT_PASSWORD=root" --publish 6603:3306 mysql
```

You will get an output of the container ID, indicating
the container is successfully running in the background.

To verify the status of the container, do:

```shell
docker ps -a
```

Once `boca-mysql` container is created, you can use:

```shell
docker start boca-mysql
```

to start the container.

Similarly, you can use:

```shell
docker stop boca-mysql
```

to stop the container.

### Configure boca-mysql
To log into MySQL as the Root User, do:

```shell
mysql -uroot -p
```

When prompted, enter the password: `root`. You will then be
presented with the MySQL monitor display.

To create database and server connector user, do:

```shell
CREATE DATABASE boca_api;
CREATE USER 'boca_api'@'%' IDENTIFIED BY 'boca_api';
GRANT ALL ON boca_api.* TO 'boca_api'@'%';
GRANT ALL PRIVILEGES ON *.* TO 'root'@'%' IDENTIFIED BY 'root';
```

**NOTE:** In `boca-api/server/datasource.local.js`, `username` and
`password` are both defaulted to `boca_api`.

### Download node modules
To download node modules, do:

```shell
npm install
```

### Database preparation
To create create tables and insert predefined data, do:

```shell
npm run reset-db
```

This will also create testing accounts for you to login and
test the application, e.g.,

```shell
email: admin@test.me ('admin' can be replaced with 'doctor', 'nurse', 'patient' and etc)
password: TestMePlease
```

### Run
To start application, do:

```shell
npm start
```

Default host server: http://localhost:3001

### Reference
[Docker Setup](https://severalnines.com/blog/mysql-docker-containers-understanding-basics)
[MySQL Setup](https://github.com/docker-library/mysql/issues/230)
