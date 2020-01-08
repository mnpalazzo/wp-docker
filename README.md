# Docker Wordpress
Local Wordpress development enviornment and setup using Docker and Docker Compose.

This Docker image uses the following containers:
* MySQL
* Wordpress
* WP CLI
* phpMyAdmin

## Requirements
Make sure you have the latest version of **Docker** and **Docker Compose** installed.

Clone this repository or copy the files from this repository into your new site directory.

## Configuration
Edit the `.env` file to change the default database configuration.

## Installation
Open a terminal and `cd` to the folder that contains `docker-compose.yml` and run:
```
docker-compose up
```

This creates the following folders `src` in your directory:
* `db` - stores db exports
* `logs` - stores server log files
* `src/themes` - used for theme development
* `src/plugins` - used for plugin development

Contains should now be built and running.

Wordpress installation is running on `localhost:80`.  
phpMyAdmin is running on `localhost:8080`.


## Usage

### Starting Containers
```
docker-compose up -d
```

### Stoping Containers
```
docker-compose stop
```

### Removing Containers
To stop and remove all containers
```
docker-compose down
```
If you need to remove the database volume as well use:
```
docker-compose down -v
```

### Exporting Database
Run the following command to export the db.  
The file will export to the `db` folder
```
./export.sh
```

### Developing Themes
The `src/themes` folder is an alias of wordpress's theme directory. Develop any new themes here.

### Developing Plugins
The `src/plugins` folder is an alias of wordpress's plugin directory. Develop any new plugins here.

## Containers

### WP CLI
Because docker is creating an image of the wordpress installation you must use the following command instead of `wp`.
```
docker-compose run --rm wpcli [command]
```

### phpMyAdmin
To access phpMyAdmin visit `localhost:8080`.  
Default user is `wordpress` and password is `password`.  
This can be changed in the `.env` file.