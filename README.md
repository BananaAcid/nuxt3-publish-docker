# nuxt3-publish-docker
Nuxt3 publish using docker - creating a docker container

## what it is
Anything needed to create a container with a Universal SSR nuxt3 app.

## how it works
1. build the nuxt3 app in a seperate image
2. create the final image, using the `.output` folder, start command set to the server script

## how to use

### requirements!
Your app should be in an `./app` folder next to this projects `./docker` folder, having a common project root.

Project structure:
```
Project
|- app/
|  `- app.vue 
`- docker/  <- this project
```

### how to get started
Clone this project into your project root, change into `./docker` (modify the config) and `npm start` - the terminal will show '0.0.0.0:80' wich correspondents to 'http://localhost:3000' with the default compose file.

### config
The `./docker/` folder contains a `package.json` with all required scripts and the image name config (`name`, `config.publisher` and `version`).

2 volumes are assumed (`data` and `config`) which you should set to your exposed folders in the `Dockerfile` and `docker-compose.yaml`.

### npm scripts
You can use `npx ntl` to see and select the commands. `npm start` to build and start the container.

- `start` -> runs `build` and `test`
- `build` ->  builds the image
- `test` -> uses the compose file to start a container based on that built image
- `export` -> exports the docker image from docker to a tar-file

utilities:
- `echo-name` -> shows the image name, that will be used
- `build-files-only` -> builds the `/.output` folder for inspection


License: ISC
