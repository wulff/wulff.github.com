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

[![dpm() screenshot](/img/tutorials/devel-dpm.png)](/img/tutorials/devel-dpm.png){: .noborder}

### dvm()

Uses var_dump() to print a variable to the ‘message’ area of the page using drupal_set_message(). The output of this function is harder to read than the Krumo-based output of dpmt(), but it can be useful if you need to copy and paste it to another application.

    dvm($input, $name = NULL)

If, for some reason, you are not using Krumo, you can use the $name parameter to distinguish between different calls to dvm().

[![dvm() screenshot](/img/tutorials/devel-dvm.png)](/img/tutorials/devel-dvm.png){: .noborder}

### dpr()

Pretty-prints a variable to the browser (without using krumo). The output is displayed in the page header, making this a good choice if your theme doesn’t print the $messages variable.

    dpr($input, $return = FALSE, $name = NULL)

Set the second parameter to TRUE if you want to return a string instead of printing it.

You can use the $name parameter to distinguish between different calls to dpr().

[![dpr() screenshot](/img/tutorials/devel-dpr.png)](/img/tutorials/devel-dpr.png){: .noborder}

### dvr()

Uses var_dump() to pretty-print a variable to the browser (without using krumo). The output is displayed in the page header, making this a good choice if your theme doesn’t print the $messages variable.

    dvr($input, $return = FALSE, $name = NULL)

Set the second parameter to TRUE if you want to return a string instead of printing it.

You can use the $name parameter to distinguish between different calls to dvr().

[![dvr() screenshot](/img/tutorials/devel-dvr.png)](/img/tutorials/devel-dvr.png){: .noborder}

### kpr()

Pretty-prints a variable to the browser using krumo. The output is displayed in the page header, making this a good choice if your theme doesn’t print the $messages variable. Since it uses Krumo, it has the added advantage that the output is very compact and unobtrusive.

    kpr($input, $return = FALSE, $name = NULL)

Set the second parameter to TRUE if you want to return a string instead of printing it.

[![kpr() screenshot](/img/tutorials/devel-kpr.png)](/img/tutorials/devel-kpr.png){: .noborder}

### dargs()

Prints the arguments passed into the current function. In this case, the arguments are ‘foo’, and ‘42’. You can use this function if you’re not completely sure of the arguments received by a specific Drupal hook or function in the code you’re working on.

    dargs()

[![dargs() screenshot](/img/tutorials/devel-dargs.png)](/img/tutorials/devel-dargs.png){: .noborder}

### dd()

Logs any variable to a file named “drupal_debug.txt” in the site’s temp directory. All output from this function is appended to the log file, making it easy to see how the contents of a variable change as you modify your code.

If you’re using Mac OS X you can use the Logging Console to monitor the contents of the log file.

If you’re using a flavor of Linux you can use the command “tail -f drupal_debug.txt” to watch the data being logged to the file.

    dd($data, $label = NULL)

### ddebug_backtrace()

Prints the function call stack.

    ddebug_backtrace()

[![ddebug_backtrace() screenshot](/img/tutorials/devel-ddebug_backtrace.png)](/img/tutorials/devel-ddebug_backtrace.png){: .noborder}

### db_queryd()

This function is the debugging version of db_query(), which prints the query and any error messages to the browser. This function is useful if you want to monitor a few database queries but don’t need Devel module’s list of all database queries used to build the current page.

    db_queryd($query, $args = array())

[![db_queryd() screenshot](/img/tutorials/devel-db_queryd.png)](/img/tutorials/devel-db_queryd.png){: .noborder}

## Drupal for Firebug

All the examples in this section assume that you are running a recent version of [Firefox](http://getfirefox.com/) with the [Firebug add-on](https://addons.mozilla.org/en-US/firefox/addon/1843).

Please note that Drupal for Firebug doesn’t seem to work with the Theme developer module from the Devel package.

### Installation

* Install the Drupal for Firebug module
* Install the DrupalForFirebug Firefox add-on. You can find a link to the current version on the Drupal for Firebug project page.

When you have installed the Firefox add-on, go to Administer → Build → Modules and enable the two Drupal for Firebug modules.

### In use

Once you have installed the add-on and enabled the modules, a new Drupal tab becomes available in Firebug. The following sections describe each subtab.

#### General

The general tab serves as a general log area for Drupal for Firebug. It tells you whether the site you’re looking at is running Drupal and has Drupal for Firebug installed and enabled.

If you want to keep your Drupal-related log messages out of the normal Firebug console, you can write messages to the Drupal for Firebug log with the firep() function:

    firep($item, $optional_title)

You can see example output in the screenshots “General: Off” and “General: On” below.

[![General: Off](/img/tutorials/dff-general-off.png)](/img/tutorials/dff-general-off.png){: .noborder}

[![General: On](/img/tutorials/dff-general-on.png)](/img/tutorials/dff-general-on.png){: .noborder}

#### SQL

To use the SQL tab you must first enable query info collection. Go to Administer → Site configuration → Devel settings and mark the checkbox labelled “Collect query info”.

The SQL tab now displays a list of all the database queries which have been made to build the current page. This is essentially the same output displayed by the Devel module when “Display query log” is enabled, but you can use the SQL tab if you don’t want the list of database queries cluttering up the page display.

You can see example output in the screenshot “SQL” below.
Forms

The Forms tab displays the form arrays used to build the forms on the current page. This can be useful when trying to identify the right array key to use when modifying or removing a form element.

You can see example output in the screenshot “Forms” below.
Users

The Users tab displays the $user object associated with the currently logged-in user, or with the anonymous user if the current session isn’t logged in.

In order to see the output for users other than the root user (UID = 1), you must grant the user the “Access Firebug Debug” permission.

You can see example output in the screenshot “Users” below.
Nodes

The Nodes tab displays information about every node loaded on the current page.

The output shows the contents of the node object after it has been loaded, after the view phase, and after the alter phase. This is useful for determining the point at which the contents of the node are being modified. Also, this is a handy way of obtaining an overview of the available node fields when developing custom node templates.

You can see example output in the screenshot “Nodes” below.
Views

The Views tab displays information about the views on the current page.

You can use this tab to gain an overview of the types of displays used, the base tables, and the pager settings of the different views.

You can see example output in the screenshot “Views” below.
Execute PHP

The Execute PHP tab lets you execute PHP code in the context of a fully bootstrapped Drupal instance. This can be useful when you want to check the output of functions which do not display any data in the frontend. Also, you can use it to make quick checks on the values of Drupal variables or global variables.

All the code you execute will behave as if it were implemented as a page callback for the path “admin/firebug/exec”.

Only users with the “Execute Firebug PHP” permission can use this tab.

You can see example output in the screenshot “Execute PHP” below.
