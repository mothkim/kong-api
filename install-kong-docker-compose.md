# Install Kong API Gateway with docker-compose #

## Prepare Environment 
- Install Docker
- Install docker-compose

1. Create file docker-compose.yaml
```sh
vi docker-compoose.yaml
```

2. Data to docker-compose.yaml file & Save & Exit
```sh
version: "3.7"
volumes:
  kong_data: {}
  
networks:
 kong-net:
services:
#######################################
  # Postgres: The database used by Kong
#######################################
  kong-database:
    image: postgres:9.6
    container_name: kong-postgres
    restart: on-failure
    networks:
      - kong-net
    volumes:
      - kong_data:/var/lib/postgresql/data
    environment:
      POSTGRES_USER: kong
      POSTGRES_PASSWORD: ${KONG_PG_PASSWORD:-kong}
      POSTGRES_DB: kong
    ports:
      - "5432:5432"
    healthcheck:
      test: ["CMD", "pg_isready", "-U", "kong"]
      interval: 30s
      timeout: 30s
      retries: 3
#######################################
  # Kong database migration
#######################################
  kong-migration:
    image: ${KONG_DOCKER_TAG:-kong:latest}
    command: kong migrations bootstrap
    networks:
      - kong-net
    restart: on-failure
    environment:
      KONG_DATABASE: postgres
      KONG_PG_HOST: kong-database
      KONG_PG_DATABASE: kong
      KONG_PG_USER: kong
      KONG_PG_PASSWORD: ${KONG_PG_PASSWORD:-kong}
    depends_on:
      - kong-database
#######################################
  # Kong: The API Gateway
#######################################
  kong:
    image: ${KONG_DOCKER_TAG:-kong:latest}
    restart: on-failure
    networks:
      - kong-net
    environment:
      KONG_DATABASE: postgres
      KONG_PG_HOST: kong-database
      KONG_PG_DATABASE: kong
      KONG_PG_USER: kong
      KONG_PG_PASSWORD: ${KONG_PG_PASSWORD:-kong}
      KONG_PROXY_LISTEN: 0.0.0.0:8000
      KONG_PROXY_LISTEN_SSL: 0.0.0.0:8443
      KONG_ADMIN_LISTEN: 0.0.0.0:8001
    depends_on:
      - kong-database
    healthcheck:
      test: ["CMD", "kong", "health"]
      interval: 10s
      timeout: 10s
      retries: 10
    ports:
      - "8000:8000"
      - "8001:8001"
      - "8443:8443"
      - "8444:8444"
#######################################
  # Konga database prepare
#######################################
  konga-prepare:
    image: pantsel/konga:latest
    command: "-c prepare -a postgres -u postgresql://kong:${KONG_PG_PASSWORD:-kong}@kong-database:5432/konga"
    networks:
      - kong-net
    restart: on-failure
    depends_on:
      - kong-database
#######################################
  # Konga: Kong GUI
#######################################
  konga:
    image: pantsel/konga:latest
    restart: always
    networks:
        - kong-net   
    environment:
      DB_ADAPTER: postgres
      DB_URI: postgresql://kong:${KONG_PG_PASSWORD:-kong}@kong-database:5432/konga
      NODE_ENV: production
    depends_on:
      - kong-database
    ports:
      - "1337:1337"
```

3. Run Kong API Gateway with docker-compose
```sh
docker-compose up -d
or
docker compose up -d
```

4. Check kong start
```sh
docker ps
```

5. Register kong with konga on web browser

- Open web browser & input url : http://localhost:1337
- Set : User/Password/Email
- Login

6. set Kong Admin URL
```sh
Name : kong
Kong Admin URL : http://kong:8001/
```

Reference : 
TH : https://medium.com/@toniceee45/%E0%B8%A7%E0%B8%B4%E0%B8%98%E0%B8%B5%E0%B8%A5%E0%B8%87-kong-gateway-api-%E0%B8%9A%E0%B8%99-docker-52345457c55f
Pantsel : https://gist.github.com/pantsel/73d949774bd8e917bfd3d9745d71febf 