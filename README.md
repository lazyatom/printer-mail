Wee Mail
========

A very simple message application demonstrating how to work with the Wee Printer API.


Getting started
---------------

First, install all the dependencies:

    $ bundle install
    $ bundle exec foreman start

To use this, a printer owner must visit `http://localhost:4545/register` (or whatever host the application is deployed to). On that page, they should enter a nickname, and the URL endpoint for their printer. For example, the nickname could be `lazyatom`, and the printer URL may be something like `http://wee-printer.gofreerange.com/print/1b6c9ad3e1a4d1d34e86f2b550e3a97f`.

Then, they can share the url `http://localhost:4545/send/lazyatom` (or whatever the nickname was) with their friends.

Those friends with the URL can send messages to the printer by completing the "From" and "Message" fields, and hitting "Send"; the message will be printed out on the recipient's printer shortly afterwards.


How it works
------------

Wee printer works by sending URLs to a printer endpoint. The Wee Printer backend then requests the page at that URL, renders it and makes it available for the printer.

In this case, when a message is created, a URL of the form `http://localhost:4545/messages/:id` is sent to the backend when a message is created.

This page is styled using the default `print` stylesheet from http://wee-printer.gofreerange.com, which helps ensure that the layout will work well on the fixed, small width of the printer (384px).


More background
---------------

Why do I have to enter a printer URL?

Well, the idea is that printers don't all need to be connected to a single central backend server. You can run your own Wee Printer backend server for yourself, or for you and your friends. Or you could run your own backend server behind your firewall. Or you can use a hosted one, like the original server at http://wee-printer.gofreerange.com. It's up to you.

Similarly, many difference publishers can be used to send content to a single printer. This demonstration "message" service isn't tied to any single backend, and you can run your own instance of this publisher yourself too if you like.