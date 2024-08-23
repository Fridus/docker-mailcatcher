# mailcatcher docker image

Here is an unofficial Dockerfile for [mailcatcher][mailcatcher].

It is a very small image (~35 MB uncompressed) available on [docker hub][dockerhubpage] based on [Alpine Linux][alpinehubpage] and using the last available release from the official Github repo of [mailcatcher][mailcatcher].


## Changelog

- 2023-09-11 Upgrading Mailcatcher to 0.10.0 and Alpine Linux to 3.20
- 2023-09-11 Upgrading Mailcatcher to 0.9.0
- 2020-09-10 Upgrading Mailcatcher from 0.7.1 to 0.8.0.beta2
- 2019-04-12 Upgrading Mailcatcher from 0.7.0 to 0.7.1


## Usage

Get it:

    docker pull fridus/mailcatcher

Run it:

    docker run -d -p 1080:80 --name smtp fridus/mailcatcher

Link it:

    docker run -d --link smtp -e SMTP_HOST=smtp --name php56 tophfr/php:5.6
    
Then you can send emails from your app and check out the web interface: http://\<your docker host\>:1080/.


If you want to send emails from your host you can map the 25 port:

    docker run -d -p 1080:80 -p 1025:25 --name mail fridus/mailcatcher

then send yout emails through your docker host on port 1025 (or any port you want)


## Build

Just clone this repo and run:

    docker build -t fridus/mailcatcher .

or

    docker-compose build


  [mailcatcher]: http://mailcatcher.me/ "MailCatcher fake SMTP server with web interface" 
  [dockerhubpage]: https://hub.docker.com/r/fridus/mailcatcher/ "Mailcatcher docker hub page"
  [alpinehubpage]: https://hub.docker.com/_/alpine/ "A minimal Docker image based on Alpine Linux with a complete package index and only 5 MB in size!"
