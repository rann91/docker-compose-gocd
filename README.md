Customized Docker Compose template for [GoCD](https://gocd.org). Contains Letsencrypt to access the GUI through HTTPS. This template is meant to be used with [nginx-proxy](https://github.com/jwilder/nginx-proxy). Use [this template](https://github.com/rann91/docker-compose-nginx-proxy) to setup nginx proxy quickly.

## Usage
Copy the default .env file and configure environment variables. Then simply run the deploy script:
```
./deploy
```

To run the containers with HTTPS, run the deploy script in production mode, which contains the Letsencrypt configuration:
```
./deploy prod
```

### SSH
To use SSH, which is required for Git, you need to generate a SSH key inside the project directory. The `.ssh` folder will be mounted inside the GoCD containers for the `go` user. To be able to use Git with SSH, you also need to set the correct file permissions for the `go` user. To do this, follow these instructions:
1. Log in to the bash terminal inside the server container as root user:
    ```
    docker exec -it gocd-server bash
    ```
2. Change the ownership of the `.ssh` folder so the `go` user gets the ownership:
    ```
    chown -R go /home/go/.ssh
    ```
3. Change write permissions of the `.ssh` folder:
    ```
    chmod 700 /home/go/.ssh
    ```
4. Change the write permissions for the files inside the `.ssh` folder:
    ```
    chmod 600 /home/go/.ssh/*
    ```

That's it! You should be good to go.