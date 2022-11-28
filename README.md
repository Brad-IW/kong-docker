# Kong Docker

## Installation Guide

This guide assumes that [Docker](https://docs.docker.com/get-docker/) has already been installed and initialised. 

1. Clone this repo and extract the files.
2. Open a terminal and navigate to the kong-docker folder.
3. Run `docker compose up` 
    
    Once the compose file has finished its start up procedure it will ask for an optional license key. At this point Kong is ready and the GUI will be accessible on port 8002.

## Test Plan

This optional test plan will take you through creating a basic service and route. This ensures that Kongs main components have been started and are working correctly. The plan assumes that the actions below are performed on a local machine running the docker containers, however this can easily be changed by swapping all instances of `localhost` to the ip address of the machine running docker.

1. Open the Kong Manager by typing `localhost:8002` into your web browser of choice. 
2. On the 'Workspaces' page scroll down and click on the 'default' workspace. 
3. Click services and create a new service.
   - Give the service a name e.g. 'my-service'
   - Select Using URL and add `https://httpbin.org/anything` to the URL parameter.
4. Click the create button.
5. Go to the routes page and create a new route. 
   - In the service dropdown select the service we just created (my-service)
   - Give the route a name e.g. 'my-route'
   - In the Method(s) field add `GET`
   - In the Path(s) field add `/example`
6. Click the create button.

   We have now created a service which is accessible using the example route. This can be accessed by either opening `localhost:8000/example` in your web browser, or running `curl localhost:8000/example` (`curl 127.0.0.1/example` on Windows) in your terminal. If all steps were done correctly this should return a JSON response which echos back the information sent in the request.