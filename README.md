Mycroft - The Campfire Bot Framework
=====================================

Description
-----------

Mycroft is an Campfire Bot Framework creating powerful Campfire bots, with minimal effort.


Installation
------------

### RubyGems

You can install the latest Mycroft gem using RubyGems

    gem install mycroft

### GitHub

Alternatively you can check out the latest code directly from Github

    git clone http://github.com/iamruinous/mycroft.git

Example
-------

Your typical Hello, World application in Mycroft would go something like this:

    require 'mycroft'

    bot = Mycroft::Bot.new do
      configure do |c|
        c.subdomain = "subdomain"
        c.rooms = ["My Room"]
      end

      on :message, "hello" do |m|
        m.reply "Hello, #{m.user.nick}"
      end
    end

    bot.start

More examples can be found in the `examples` directory.

Features
--------

### Documentation

Mycroft provides a documented API, which is online for your viewing pleasure
[here](http://rubydoc.info/gems/mycroft/frames).

### Object Oriented

Most Campfire bots are a mess of either procedural code, or little to no
extensibility. Mycroft is fully, beautifully Object Oriented, and uses that to
it's advantage in the simple, yet powerful plug in system.

### Threaded

Mycroft's plugins and handlers are executed in their own personal thread.
This means the main thread can stay focused on what it does best, providing
non-blocking reading and writing to an Campfire room. This will prevent your bot
from locking up when one of your plugins starts doing some intense operations.

### Plugins

That's right folks, Cinch provides a modular based plugin system. This is a
feature many people have bugged us about for a long time. It's finally here,
and it's as awesome as you had hoped!

This system allows you to create feature packed plugins without interfering with
any of the Cinch internals. Everything in your plugin is self contained, meaning
you can share your favorite plugins among your friends and release a ton of
your own plugins for others to use

Want to see the same Hello, World application in plugin form? Sure you do!

    require 'cinch'

    class Hello
      include Cinch::Plugin

      match "hello"

      def execute(m)
        m.reply "Hello, #{m.user.nick}"
      end
    end

    bot = Cinch::Bot.new do
      configure do |c|
        c.server = "irc.freenode.org"
        c.channels = ["#cinch-bots"]
        c.plugins.plugins = [Hello]
      end
    end

    bot.start

More information can be found in the {Mycroft::Plugin} documentation.

Authors
-------

* [Jade Meskill](http://jademeskill.com)

Contribute
----------

Fork the project, implement your feature in its own branch, and send
a pull request to one of the Mycroft collaborators. We'll check it
out.

### Contributors
- your name here
