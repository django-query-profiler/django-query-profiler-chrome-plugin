===================================
Django query profiler chrome plugin
===================================

This project contains the chrome plugin code for `django query profiler` -  code `here <https://github.com/django-query-profiler/django-query-profiler/>`__, docs `here <https://django-query-profiler.readthedocs.io/en/latest/>`__.
It reads the header set by the `django_query_profiler`, and adds to a html table in the plugin


Getting Started
===============

This is the `link <https://chrome.google.com/webstore/devconsole/24f090a4-0ba1-4744-b291-1c723f6b1e5d/abdcoolndccdlolelmkdobbcbcjnmblh/edit/package?hl=en>`_ to the chrome web store, for getting the plugin


How the plugin works
====================

manifest.json is the entry point for the chrome plugin.  It has two important attributes that define how the plugin works:

1. devtools_page:  This extends the browser's built-in devtools by adding another pane
    - we have to specify a html page here, and ours is devtools.html.  All this page does is include devtools.js

    - In devtools.js, we have the code to create a devtools panel, and add a listener `onRequestFinished`.  This
      listener gets called for every api, but acts on it ONLY when the api has the headers it is looking for (which
      we are setting in the middleware).  Once it finds them, it appends a row in the table (in the panel) -- which
      gets created in next step

2. options_ui: This specifies the contents of the plugin.
    - This page is defined as panel_table.html.  The file panel_table.html contains code to create an empty table.
      It is in this table that the listener adds rows to

    - We have defined two buttons in the panel - and panel_controls.js defines what functions should be called on
      button click


For contributors
================

The `django query profiler chrome plugin` is released under the BSD license, like `django query profiler` and Django itself.
If you like it, please consider contributing! How the code is organized, and how the profiler works is documented `here in readthedocs <https://django-query-profiler.readthedocs.io/en/latest/how_it_works.html>`__
