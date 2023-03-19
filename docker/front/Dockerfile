FROM alpine:3.16 as BUILD

RUN apk add --no-cache git nodejs npm

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


