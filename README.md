# Envoy proxy authorisation

## Implementation

### Step 1: 

Clone this repo.

### Step 2:

`cd` into the folder. run `docker-compose up -d`.

### Step 3:

After dockers have started, run `docker-compose ps` to see if the dockers are up.

```
PS C:\Users\212764778\Desktop\envoy-ext-authz-master\envoy-ext-authz-master> docker-compose ps

                Name                              Command               State                            Ports
---------------------------------------------------------------------------------------------------------------------------------------
envoy-ext-authz-master_authz_1         docker-entrypoint.sh npm start   Up      0.0.0.0:8080->8080/tcp
envoy-ext-authz-master_front-envoy_1   /usr/bin/dumb-init -- /bin ...   Up      10000/tcp, 0.0.0.0:8000->80/tcp, 0.0.0.0:8001->8001/tcp
envoy-ext-authz-master_service1_1      /bin/sh -c /usr/local/bin/ ...   Up      10000/tcp, 80/tcp
envoy-ext-authz-master_service2_1      /bin/sh -c /usr/local/bin/ ...   Up      10000/tcp, 80/tcp
```

### Step 4:

Open the postman app, run the request to `http://localhost:8000/service/1` without authentication, we'll be getting `State: 403 Forbidden` go to the authorisation tab and set it to `Basic Auth`, the `username` and `password` are set as hardcoded in the express, now try the `username` as `john` and `password` as `doe`.

Now run the request again to `http://localhost:8000/service/1`, you'll see 
```
Hello from behind Envoy (service 1)! hostname: 07b82a40f3de resolvedhostname: 172.21.0.3
```
Hostname and resolved hostname will be different in your system.

