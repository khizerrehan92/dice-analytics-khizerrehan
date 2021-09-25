FROM    node:14.17.2-stretch-slim
LABEL   name="Express Application" \   
        maintainer="Khizer Rehan" \
        summary="A Simple Express App generated from express-generator"
EXPOSE  3000
WORKDIR /express-app
# Install app dependencies
# A wildcard is used to ensure both package.json AND package-lock.json are copied
# where available (npm@5+)
COPY package*.json ./
RUN npm install
COPY  . .
CMD [ "npm", "start" ]
