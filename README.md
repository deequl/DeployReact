# DeployReact
How to deploy a react app on Ubuntu x64 host

First we have to download [puttygen](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html) and make publicKey and privateKey SSH to acces more secure to our server.
Then save publicKey generated on .txt file and privateKey on .ppk file.

## Connecting to host
(Previously on our host we've uploaded the public key)
Now we will download [putty-installer](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html) and configurate our profile.
* **Host Name (or IP address)**: Insert IP of the host.
* **Connection>Data** In Auto-login username put the user name. (by default is root)
* **Connection>SSH>Auth** Browse... our Private key file for authentication.
* **Session** In Saved Session put the session name and click Save.

Now It's all ready to connect, click Open button

## Configuring Host
### Firewall
This is a very important step we need to allow access to the service.
* By default firewall is inactive, we can check it  
```html
sudo ufw status
sudo ufw app list
```
let's active and config firewall running this commands
```html
sudo ufw allow 'Nginx Full'
sudo ufw allow 'OpenSSH'
sudo ufw enable
```
to see ufw documentation use.  ```ufw COMMAND```

### Setup NodeJS
We are using Nodejs for backend and we will serve the static files of the react application build. So Nodejs is required
We will use package management to install, here is command to install Node.js v9
```html
curl -sL https://deb.nodesource.com/setup_9.x | sudo -E bash -
sudo apt-get install -y nodejs
```
After successfully installing Node.js, we can check the version using ``` node -v ```
Visit [NodeJS](Visit https://nodejs.org/en/download/package-manager/) to see documentation.
