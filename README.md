<h1 align="center">NamedZeus</h1>
<div align="center"><img src="images/zeus-logo-theme-red.png" /></div>

## A centralized host-based network policies enforcement system. 

In view of the great complexity in managing network rules and policies in firewalls for different hosts, the software aims to solve this pain, providing centralized management of these rules in groups and patterns, so that they are associated with servers hosting security services. same purpose in a simple and quick way. 

![DEMO](images/demo.png)

> You can get a free license in our website: <a href="https://namedzeus.com/pricing">GET FREE LICENSE</a>

### Dependencies

- *Docker v24.0 or higher.*
- *Docker Compose v2.13 or higher.*

## Install instructions

We offer two method to you get up and running the NameZeus into your infrastructure:

> *Notice that is an alpha version yet*

<details>
  <summary style="font-size: 20px;"><strong>Install using Docker Compose</strong></summary>

  #### 1° - Creating project folder

  ```bash
  mkdir -p /opt/namedzeus/secrets/
  ```

  #### 2° - Creating the secrets

  ```bash
  openssl rand -base64 32 > /opt/namedzeus/secrets/main_key
  openssl rand -base64 32 > /opt/namedzeus/secrets/pusher_key
  openssl rand -base64 32 > /opt/namedzeus/secrets/pusher_secret
  openssl rand -base64 32 > /opt/namedzeus/secrets/root_password
  openssl rand -base64 32 > /opt/namedzeus/secrets/namedzeus_password
  ```

  #### 3° - Adding the project composition

  ```bash
  cat > /opt/namedzeus/docker-compose.yml
  ```

  #### 4° - Running project

  ```bash
  docker compose -f /opt/namedzeus/docker-compose.yml up -d
  ```
</details>

<details>
  <summary style="font-size: 20px;"><strong>Install using Docker Swarm</strong></summary>

  #### 1° - Creating project folder

  ```bash
  mkdir -p /opt/namedzeus/
  ```

  #### 2° - Creating the secrets

  ```bash
  openssl rand -base64 32 | docker secret create main_key -
  openssl rand -base64 32 | docker secret create pusher_key -
  openssl rand -base64 32 | docker secret create pusher_secret -
  openssl rand -base64 32 | docker secret create root_password -
  openssl rand -base64 32 | docker secret create namedzeus_password -
  ```

  #### 3° - Adding the project composition

  ```bash
  cat > /opt/namedzeus/docker-swarm.yml
  ```

  #### 4° - Running project

  ```bash
  docker stack deploy -c /opt/namedzeus/docker-swarm.yml namedzeus
  ```
</details>
