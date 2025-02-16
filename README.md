# Website Navigation Editor Open Project

The goal of this project is to create an `Open Website Navigation Editor` (web directory). 
You can easily edit the website directory and share it to [Roam Browser](https://play.google.com/store/apps/details?id=com.roam.app.android "Google Search")  (Android version by now, iOS is comming for future) or any other browsers that are compatible with the Roam Browser navigation standard.


# Requirements
## Server
A Linux server, such as AWS EC2, with low configuration requirements.  
Recommended specifications:  
- 2 CPU cores  
- 4 GB of RAM  
- At least 10 GB of storage

## Domain & DNS
You can register a domain at any domain provider, and we recommend to resolve DNS record by cloudflare with a free plan.

# Deployment on EC2 by docker compose (Example: amazon linux 2)

## Install docker and docker compose

Install docker by aws yum repository:

```
sudo yum install -y docker
```

Or install and start docker with docker install script manually:

```
curl -fsSL https://get.docker.com | sh
sudo systemctl start docker
```

After installing Docker, enable the Docker service to start automatically upon system reboot:

```
sudo systemctl enable docker
```

Install docker compose plugin:

```
sudo mkdir -p /usr/local/lib/docker/cli-plugins
sudo curl -L https://github.com/docker/compose/releases/latest/download/docker-compose-$(uname -s)-$(uname -m) -o /usr/local/lib/docker/cli-plugins/docker-compose
sudo chmod +x /usr/local/lib/docker/cli-plugins/docker-compose
```

Verify Docker Compose installation:

```
docker compose version
```

## Run

Git clone this project to your server:
```
sudo git clone https://github.com/koonox/nav-editor.git
```

Run by docker compose:

```
sudo docker compose up -d 
```

If run sucess, nav-editor will listen to default port `80`

Open your browser (e.g., Chrome) and visit the following URL to access the nav-editor:

`https://your_server_ip`

Default username and password:
- username: `admin`
- password: `123456`

> You must set port `80` can access in inbound rules of security rules

Finally you can resolve your domain to your IP, and you can access nav-editor project like:

`https://your_domain.com`