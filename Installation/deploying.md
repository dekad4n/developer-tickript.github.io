# Deploying the Backend
As Sabanci University students, the Sabanci University's IT team has given as a container in which we could deploy our backend. This process only works for the ones who are trying to deploy their application through Sabanci University network.

We will cover every step we did to deploy our backend.

## 1. Install OpenVPN
The service is only accessible when one logged in to Sabanci University network. Therefore, the one should use the Sabanci University network or should use OpenVPN to connect Sabanci University network.

Install OpenVpn from [this link](https://mysu.sabanciuniv.edu/it/en/openvpn-access).
Then open it and enter your su-username and password.

## 2. Login through SSH
Prerequisites: a command line in which ssh service is usable.

1. Open a prefferred command line.

2. It team should have given you a DNS, a username and password. Enter it to command line like this:
```
ssh username@DNS
```
3. Then, enter your password.

## 3. Using already installed Podman
It team provides podman to you. You would try a basic command like:
```
podman run -d -p 8080:8080 dockerhubusername/container_name:version
```
It works and when you try your api, it will response to you. However, avoid this, since logging-out causes stop of the container. Do these instead:

1. Open a screen session (write screen to logged in container):
```
screen
```
2. Write podman commands now:
```
podman run -d -p 8080:8080 dockerhubusername/container_name:version
```
3. Press ctrl+a then d

4. Write exit to logged in container.

Now, your backend is always awake.

## Why not to use systemctl, loginctl, nohup or tmux
systemctl, loginctl or tmux requires sudo permission. We do not have that.

Nohup closes after closing the current login session (terminal with writing exit or forcing to close).