- docker build -t khizerrehan92/node-express:v1 .
- docker run --rm -it --name express-app -p 9000:3000 -d khizerrehan92/node-express:v1
- docker exec -it express-app bash

### Install Curl inside docker 
- apt-get update; apt-get install curl