FROM ubuntu:20.04 AS build

ARG DEBIAN_FRONTEND=noninteractive

RUN apt-get update &&\
    apt-get install -y git \
    nodejs \
    npm

## Cloning the repository
RUN git clone https://github.com/damienMS/doodlestudent.git

## Going to the front directory
WORKDIR /doodlestudent/front

## Installing the dependencies
RUN npm install

## Compiling the project
RUN npm run build

FROM nginx

## Copying the build from the build stage
COPY --from=build /doodlestudent/front/dist/tlcfront /usr/share/nginx/html


## Expose on port 80
EXPOSE 80


