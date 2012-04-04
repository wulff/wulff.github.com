---
layout: post
title: Debugging Drupal
teaser: A short guide to the Devel module and Drupal for Firebug.
permalink: tutorials/debugging-drupal.html
language: en
categories: tutorials
tags: debugging drupal tutorial
---

# {{ page.title }}

This page gives a brief overview of some of the tools you can use to make Drupal development and debugging easier.

It covers the Devel contrib module, the Drupal for Firebug contrib module and Firefox extension, the FirePHP library, and the combination of NetBeans and Xdebug.

This guide has a [companion module](http://drupal.org/project/devel_demo) available at Drupal.org. Post corrections or additions in the [issue queue](http://drupal.org/project/issues/devel_demo?categories=All).

## Devel module

In addition to the core module, the Devel package contains some other useful modules:

* Devel generate: Generates dummy users, nodes, and taxonomy terms.
* Theme developer: Displays theme API information for theme developers. (Note that this module doesn’t work if Drupal for Firebug is enabled.)

These modules are not covered in this guide. See the Drupal handbook for more information.
Installation

* Download and install the latest version of the Devel module from Drupal.org.
* Go to Administer → Build → Modules and enable the Devel module.

### dpm()

Prints a variable to the ‘message’ area of the page using drupal_set_message(). You can use this function to keep track of one or more variables when you’re working on the code running your site. Because the Devel module now comes with Krumo, the output is compact and unobtrusive.

    dpm($input, $name = NULL)

If, for some reason, you are not using Krumo, you can use the $name parameter to distinguish between different calls to dpm().

You can see example output in the screenshot “dpm()” below.

[![dpm() screenshot](/img/tutorials/devel-dpm.png)](/img/tutorials/devel-dpm.png)

### dvm()

Uses var_dump() to print a variable to the ‘message’ area of the page using drupal_set_message(). The output of this function is harder to read than the Krumo-based output of dpmt(), but it can be useful if you need to copy and paste it to another application.

    dvm($input, $name = NULL)

If, for some reason, you are not using Krumo, you can use the $name parameter to distinguish between different calls to dvm().

You can see example output in the screenshot “dvm()” below.

[![dvm() screenshot](/img/tutorials/devel-dvm.png)](/img/tutorials/devel-dvm.png)

### dpr()

Pretty-prints a variable to the browser (without using krumo). The output is displayed in the page header, making this a good choice if your theme doesn’t print the $messages variable.

    dpr($input, $return = FALSE, $name = NULL)

Set the second parameter to TRUE if you want to return a string instead of printing it.

You can use the $name parameter to distinguish between different calls to dpr().

You can see example output in the screenshot “dpr()” below.

[![dpr() screenshot](/img/tutorials/devel-dpr.png)](/img/tutorials/devel-dpr.png)

### dvr()

Uses var_dump() to pretty-print a variable to the browser (without using krumo). The output is displayed in the page header, making this a good choice if your theme doesn’t print the $messages variable.

    dvr($input, $return = FALSE, $name = NULL)

Set the second parameter to TRUE if you want to return a string instead of printing it.

You can use the $name parameter to distinguish between different calls to dvr().

You can see example output in the screenshot “dvr()” below.

[![dvr() screenshot](/img/tutorials/devel-dvr.png)](/img/tutorials/devel-dvr.png)

### kpr()

Pretty-prints a variable to the browser using krumo. The output is displayed in the page header, making this a good choice if your theme doesn’t print the $messages variable. Since it uses Krumo, it has the added advantage that the output is very compact and unobtrusive.

    kpr($input, $return = FALSE, $name = NULL)

Set the second parameter to TRUE if you want to return a string instead of printing it.

You can see example output in the screenshot “kpr()” below.

[![kpr() screenshot](/img/tutorials/devel-kpr.png)](/img/tutorials/devel-kpr.png)

### dargs()

Prints the arguments passed into the current function. In this case, the arguments are ‘foo’, and ‘42’. You can use this function if you’re not completely sure of the arguments received by a specific Drupal hook or function in the code you’re working on.

    dargs()

You can see example output in the screenshot “dargs()” below.

[![dargs() screenshot](/img/tutorials/devel-dargs.png)](/img/tutorials/devel-dargs.png)

### dd()

Logs any variable to a file named “drupal_debug.txt” in the site’s temp directory. All output from this function is appended to the log file, making it easy to see how the contents of a variable change as you modify your code.

If you’re using Mac OS X you can use the Logging Console to monitor the contents of the log file.

If you’re using a flavor of Linux you can use the command “tail -f drupal_debug.txt” to watch the data being logged to the file.

    dd($data, $label = NULL)

You can see example output in the screenshot “dd()” below.

### ddebug_backtrace()

Prints the function call stack.

    ddebug_backtrace()

You can see example output in the screenshot “ddebug_backtrace()” below.

[![ddebug_backtrace() screenshot](/img/tutorials/devel-ddebug_backtrace.png)](/img/tutorials/devel-ddebug_backtrace.png)

### db_queryd()

This function is the debugging version of db_query(), which prints the query and any error messages to the browser. This function is useful if you want to monitor a few database queries but don’t need Devel module’s list of all database queries used to build the current page.

    db_queryd($query, $args = array())

You can see example output in the screenshot “db_queryd()” below.

[![db_queryd() screenshot](/img/tutorials/devel-db_queryd.png)](/img/tutorials/devel-db_queryd.png)
