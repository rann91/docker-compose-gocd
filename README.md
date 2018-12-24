Customized Docker Compose template for [GoCD](https://gocd.org). This template is meant to be used with [nginx-proxy](https://github.com/jwilder/nginx-proxy). Use [this template](https://github.com/rann91/docker-compose-nginx-proxy) to setup nginx proxy quickly.

## Getting started
Copy the default .env file and configure environment variables. Then simply run docker-compose:
```
docker-compose up -d
```

### SSH
To use SSH, which is required for Git, you need to generate a SSH key inside the project directory. The `.ssh` folder will be mounted inside the GoCD agent container for the `go` user. When you get file permission errors, set the correct permissions for the `.ssh` folder:

```
chown -R 1000 .ssh
chmod -R 600 .ssh
```
