.. contents::

Introduction
--------------

``collective.scriptedredirect`` allows you to write HTTP 302 Moved Temporary and HTTP 301 Moved Permanently
logic for your `Plone CMS <http://plone.org>`_ site with Python scripting.

Benefits
---------

* The redirect logic is front-end web server independent: no need to touch variouos configuration files of Apache, Varnish or Nginx)

* Python allows to write more complex logic for redirects easier - no regular expressions!

* Python scripts in Plone have access to more complete state information:
  user logged in status, permissions, etc.

Usage
-----

Installation
++++++++++++++++

Add add-on in *buildout.cfg*::

    eggs =
        ...
        collective.scriptedredirect

Run buildout.

Install *Scripted redirects in Python* in Site Setup > Add-ons.

Doing redirects through the web
++++++++++++++++++++++++++++++++++++

Edit *redirect_handler* in Zope Management Interface in your site root.

.. image :: http://cloud.github.com/downloads/collective/collective.scriptedredirect/Screen%20Shot%202012-09-25%20at%201.28.18%20AM.png

In the case of accident use ``?no_redirect`` HTTP query parameter to override
the redirecter and fix your site.


Doing redirects through the web
++++++++++++++++++++++++++++++++++++

Register a browser view called ``redirect_handler`` to write
the redirect code in addon Python code. ``redirect_handler`` view
is always preferred over ``redirect_handler`` script.




Internals
-----------

``collective.scriptedredirect`` hooks itself to Zope's pre-traversal hook and is
triggered before the request traverses into your Plone site in Zope application server.

Author
------

`Mikko Ohtamaa <http://opensourcehacker.com>`_