# Docker Compose for Laravel with Node.js
A pretty simplified Docker Compose workflow that sets up a LEMP network of containers for local Laravel development. You can view the full article that inspired this repo [here](https://dev.to/aschmelyun/the-beauty-of-docker-for-local-laravel-development-13c0).


## Usage

To start Docker needs to be installed on your system, so create the project in Laravel or copy (or git clone) your project to the root of the directory.

I renamed the directory of your Laravel project to src, or change in docker-compose.yml in volumes what is the name of the directory that your project is in.

Then, in your terminal (inside the directory where the docker-compose.yml file is) go up your containers with the following command: `docker-compose up -d --build`.

Everything running perfectly (if you don't have the images installed on your system, this process will download them), the following ports and commands will be available to you:
- **nginx** - `:8080`
- **mysql** - `:3306`
- **php** - `:9000`

<br/>

- **php composer**: `docker-compose run --rm composer update`
- **artisan**: `docker-compose run --rm artisan migrate` 
- **npm**: `docker-compose run --rm npm install` and `docker-compose run --rm npm run dev`

## Persistent MySQL Storage

The data saved in MySQL will be kept in the directory **dados-mysql**, so that when the container is destroyed, the data will still be on your system.


1. Create a `my_custom_name` directory in the project root or whatever.
2. Under the mysql service in your `docker-compose.yml` file, add the following lines:

```
volumes:
  - ./path_custom/my_custom_name:/var/lib/mysql
```
