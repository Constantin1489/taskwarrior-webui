# Taskwarrior-webui-reverted-41fabce

This is a temporary solution to https://github.com/DCsunset/taskwarrior-webui/issues/68

This won't be updated because of respecting the [original Github project](https://github.com/DCsunset/taskwarrior-webui).

If there is a fix for the `41fabce` commit, I would mention it.

The forked repo I made is [here which is archived.](https://github.com/Constantin1489/taskwarrior-webui)

# Taskwarrior-webui

[![Docker Image Size](https://badgen.net/docker/size/dcsunset/taskwarrior-webui)](https://hub.docker.com/r/dcsunset/taskwarrior-webui)

Responsive Web UI for Taskwarrior based on Vue.js and Koa.js.

## Screenshots

![Screenshot 1](./screenshots/Screenshot1.png)

![Screenshot 2](./screenshots/Screenshot2.png)

## Features

* Responsive layouts
* Material Design UI
* PWA support
* Easy to deploy (using Docker)
* Support for multiple types of tasks
* Support for light and dark themes
* Sync with a taskserver


## Deployment

### Using docker (recommended)

First pull the docker image:

```
docker pull dcsunset/taskwarrior-webui
```

Then run it with the command:

```
docker run -d -p 8080:80 --name taskwarrior-webui \
	-v $HOME/.taskrc:/.taskrc -v $HOME/.task:/.task \
	dcsunset/taskwarrior-webui
```

## Configurations

The following environment variables may be set:
 * `TASKRC` - the location of the `.taskrc` file, `/.taskrc` by default when run in _production_ mode
 * `TASKDATA` - the location of the `.task` directory, `/.task` by default when run in _production_ mode

Remember to mount your files to **the corresponding locations** when you set `TASKRC` or `TASKDATA` to a different value.

### Manually deploy

First build the frontend:

```
cd frontend
npm install
npm run build
npm run export
```

Then build and start the backend:

```
cd backend
npm install
npm run build
npm start
```

Then install nginx or other web servers
to server frontend and proxy requests to backend
(you can refer to `nginx/nginx.conf`).

## Development

First start the server at backend:

```
cd backend
npm install
npm run dev
```

Then start the dev server at frontend:

```
cd frontend
npm install
npm run dev
```

Then the frontend will listen at port 8080.

## Contributing

Contributions are very welcome!
Please create or comment on an issue to discuss your ideas first before working on any PR.

I've been very busy recently and may not be able to handle every issue timely.
So I'm also looking for maintainers who are interested in this project.
Feel free to open an issue if you have any interest.

## FAQ

### Sync with a taskserver

This Web UI supports auto sync with a taskd server
by calling the `task sync` command periodically.
In order to use this function,
first you need to follow the [instructions](https://taskwarrior.org/docs/taskserver/setup.html)
to configure both the taskserver and client manually until the `task sync` can be executed successfully.
Then remember to map the client configurations (`.taskrc` and `.task`) into the container.


## License

GPL-3.0 License
