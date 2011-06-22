wikistream is a barebones webapp for helping visualize current editing
activity in wikipedia. It uses node.js, socket.io and redis to sit in the
wikimedia IRC chat rooms (where updates are published), and makes them available
on the Web in realtime.

Installation:

* install [redis](http://redis.io)
* install [node](http://node.io)
* install [npm](http://npmjs.org/)
* npm install

Next you'll want to use and/or adjust the default configuration:

    cp config.json.example config.json

You may want to adjust the ircNick that is in the example to something unique,
so that you will be able to join the channels without a collision. Also you 
can adjust the wkipedia language channels that are being monitored.

To run the app you'll first need to fetch wikipedia updates from IRC and 
feed them to redis:

    node updates.js

next, start the webapp;

    node app.js

and point your browser at:

    http://localhost:3000/

An upstart script is included, which you should be able to install and use:

    cp wikistream.conf /etc/init/wikistream.conf
    start wikistream

    cp wikistream-irc.conf /etc/init/wikistream-irc.conf
    start wikistream-irc

Author: Ed Summers (ehs@pobox.com)

License: Public Domain
