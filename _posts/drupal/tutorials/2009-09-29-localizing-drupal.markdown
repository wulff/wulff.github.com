---
layout: post
title: Localizing Drupal
teaser: A short guide to localizing Drupal using either the central localization server or local tools.
permalink: drupal/tutorials/localizing-drupal.html
language: en
categories: tutorials
tags: localizing drupal tutorial
---

There are basically three ways you can contribute to the Drupal localization effort:

1. Translate strings directly on [localize.drupal.org](http://localize.drupal.org/)
2. Download .po files from [localize.drupal.org](http://localize.drupal.org/) and work on them locally
3. Install the localization client and submit localized strings directly from your own site

This guide gives a brief introduction to all three cases.

See also:

* [Debugging Drupal](/drupal/tutorials/debugging-drupal.html)
* [Drupal on Ubuntu](/drupal/tutorials/localizing-drupal.html)

## Using the centralized localization server
 
You can access the Danish group on the centralized localization server at the following URL:

[http://localize.drupal.org/translate/languages/da](http://localize.drupal.org/translate/languages/da)

The front page shows the latest blog posts by the Danish team and gives you a quick overview of the current status of the translation.

[![Overview](/img/tutorials/localizing-drupal/01-da-overview.png)](/img/tutorials/localizing-drupal/01-da-overview.png){: .noborder}

At the time of writing 66 contributors have translated 40359 strings out of 361703 strings total.

An overview of all the projects available for translation can be found at:

[http://localize.drupal.org/translate/languages/da](http://localize.drupal.org/translate/languages/da)

[![Explorer projects](/img/tutorials/localizing-drupal/02-da-explore-projects.png)](/img/tutorials/localizing-drupal/02-da-explore-projects.png){: .noborder}

We maintain a much smaller list of [the modules we’re currently focusing on](/drupal/l10n/status.html).

## Adding translations
 
To start adding translations to a specific module, you must go to the *Translate* tab. Enter the name of the module you want to work with (e.g. *Panels*) and choose *Untranslated* from the status dropdown.

When you press *Filter* you will see a paginated list of all untranslated strings in the Panels module. Next to each original text is a textarea where you can enter you translation. If you are unsure about a translation, you can mark it as a *Suggestion for discussion* to indicate that you would like other translators to take a look at it before it’s accepted.

You can click the small magnifying glass to see a list of modules and versions where the source string is used. This can be helpful if you want to determine the context in which a specific string is used.

When you are done entering your translations, press *Save translations* to save them in the database. Your translations will be put in a queue for review by one of the translation maintainers.

[![Translate](/img/tutorials/localizing-drupal/03-da-translate.png)](/img/tutorials/localizing-drupal/03-da-translate.png){: .noborder}
[![Translate](/img/tutorials/localizing-drupal/04-da-translate-panels.png)](/img/tutorials/localizing-drupal/04-da-translate-panels.png){: .noborder}
[![Details](/img/tutorials/localizing-drupal/05-da-translate-details.png)](/img/tutorials/localizing-drupal/05-da-translate-details.png){: .noborder}

## Using a local editor

Copy goes here…

## Install and configure Poedit
 
Open a terminal window (*Applications → Accessories → Terminal*) and run the following command to install the latest version of Poedit:

    sudo apt-get install poedit

Poedit is now available in *Applications → Programming → Poedit*. Run Poedit now to perform the initial setup tasks.

[![Setup](/img/tutorials/localizing-drupal/06-poedit-setup.png)](/img/tutorials/localizing-drupal/06-poedit-setup.png){: .noborder}

Enter you name and e-mail address and continue to the *Editor* tab. When you work on translations of Drupal, you don’t need `.mo` files, so you can just uncheck *Automatically compile .mo file on save*.

[![Personalize](/img/tutorials/localizing-drupal/07-poedit-personalize.png)](/img/tutorials/localizing-drupal/07-poedit-personalize.png){: .noborder}
 [![Editor](/img/tutorials/localizing-drupal/08-poedit-editor.png)](/img/tutorials/localizing-drupal/08-poedit-editor.png){: .noborder}

Click *Add* on the *Translation memory* tab to add your language to the list. Poedit uses the translation memory to suggest translations of untranslated strings. This makes it easy keep translations of commonly used words consistent.

[![Translation memory](/img/tutorials/localizing-drupal/09-poedit-tm-add.png)](/img/tutorials/localizing-drupal/09-poedit-tm-add.png){: .noborder}

[![Translation memory](/img/tutorials/localizing-drupal/10-poedit-tm.png)](/img/tutorials/localizing-drupal/10-poedit-tm.png){: .noborder}

To get started, let’s seed the translation memory with the Danish translation of Drupal core. Go to the following URL to download the latest version:

[http://localize.drupal.org/translate/languages/da/export?project=drupal](http://localize.drupal.org/translate/languages/da/export?project=drupal)

Select release 6.14, *Translation* and *All in one file*. Save the resulting file in your home folder.

[![Export](/img/tutorials/localizing-drupal/11-tm-export.png)](/img/tutorials/localizing-drupal/11-tm-export.png){: .noborder}

Return to the *Translation Memory* tab in the Poedit preferences and click *Generate database*. Your home directory should already be on the list, so you can just click *Next*. If the `drupal-6.14-da.po` file is not on the list, click *Add files* to add it manually. Press *Finish* to scan the listed files for translations.

[![Generate database](/img/tutorials/localizing-drupal/12-poedit-generate.png)](/img/tutorials/localizing-drupal/12-poedit-generate.png){: .noborder}

[![Generate database](/img/tutorials/localizing-drupal/13-poedit-tm-generate-2.png)](/img/tutorials/localizing-drupal/13-poedit-tm-generate-2.png){: .noborder}

## Associating .po files with Poedit
 
In this part of the guide we’ll work with the Quotes modules. First go to the following URL to export the latest translation of the module:

[http://localize.drupal.org/translate/languages/da/export?project=quotes](http://localize.drupal.org/translate/languages/da/export?project=quotes)

Choose *All releases*, *Translation*, and *All in one file*. Save the resulting file on your desktop.

[![Export](/img/tutorials/localizing-drupal/14-translate-export.png)](/img/tutorials/localizing-drupal/14-translate-export.png){: .noborder}

First we need to associate `.po` files with the Poedit. This lets you double-click translation files to open them in Poedit instead of the default text editor.

Right-click the `quotes-all-da.po` file on your desktop, and choose *properties*. Go to the *Open With* tab and click *Add*. Expand *Use a custom command* and enter the full path to the Poedit binary:

    /usr/bin/poedit

[![Properties](/img/tutorials/localizing-drupal/15-po-properties.png)](/img/tutorials/localizing-drupal/15-po-properties.png){: .noborder}

[![Open with](/img/tutorials/localizing-drupal/16-po-open-with.png)](/img/tutorials/localizing-drupal/16-po-open-with.png){: .noborder}

Click add and select poedit as the default application for all files of type *translation file*.

[![Add application](/img/tutorials/localizing-drupal/17-po-add-application.png)](/img/tutorials/localizing-drupal/17-po-add-application.png){: .noborder}

[![Set as default application](/img/tutorials/localizing-drupal/18-po-default.png)](/img/tutorials/localizing-drupal/18-po-default.png){: .noborder}

Double-click `quotes-all-da.po` to open it in Poedit.

## Working with Poedit
 
When you open a `.po` file in Poedit, you will be presented with a list of all the strings in the file. Strings displayed in bold text have not yet been translated.

If you click on an item in the list, the source string will be shown in the top textarea, and if a translation exists, it will be displayed in the bottom textarea. If a string has not been translated, you can enter your translation in the bottom textarea.

[![Poedit](/img/tutorials/localizing-drupal/19-poedit-overview.png)](/img/tutorials/localizing-drupal/19-poedit-overview.png){: .noborder}

[![Translation memory](/img/tutorials/localizing-drupal/20-poedit-tm.png)](/img/tutorials/localizing-drupal/20-poedit-tm.png){: .noborder}

[![Translation memory](/img/tutorials/localizing-drupal/21-poedit-tm-2.png)](/img/tutorials/localizing-drupal/21-poedit-tm-2.png){: .noborder}

[![Fuzzy strings](/img/tutorials/localizing-drupal/22-poedit-fuzzy.png)](/img/tutorials/localizing-drupal/22-poedit-fuzzy.png){: .noborder}

## Keyboard shortcuts
 
Key            | Action
---------------|--------------------------------------------
ALT+C          | Copy the source string to the translation
CTRL+UPARROW   | Move to the previous string in the list
CTRL+DOWNARROW | Move to the next string in the list
ALT+U          | Toggle the fuzzy flag on the current string

## Using the localization client
 
### Install and configure the Localization client module

1. Download and install the latest version of the Localization client from Drupal.org
2. Go to *Administer → Build → Modules* and enable the Localization client module.
3. Go to *Administer → Site configuration → Languages* and add at least one language. Set one of the new languages as the default language.

Switch your site to a language other than English to activate the translation toolbar. On every page you visit, you’ll see a toolbar at the bottom of the screen, which you can use to translate strings appearing on the current page.

[![Languages](/img/tutorials/localizing-drupal/22-drupal-languages.png)](/img/tutorials/localizing-drupal/22-drupal-languages.png){: .noborder}
[![Localization client](/img/tutorials/localizing-drupal/23-drupal-l10n-client-1.png)](/img/tutorials/localizing-drupal/23-drupal-l10n-client-1.png){: .noborder}
[![Localization client](/img/tutorials/localizing-drupal/24-drupal-l10n-client-2.png)](/img/tutorials/localizing-drupal/24-drupal-l10n-client-2.png){: .noborder}

### Share your translations
 
From the *Languages* page, choose *Configure → Localization sharing* to enable translation sharing. Use the following URL to connect your site with the central Drupal localization server:

[http://localize.drupal.org/](http://localize.drupal.org/)

Next go to *My account → Edit* and find the *Localization client* fieldset. Click the link below the text field to obtain your API key. Enter the API key in the field and save your account.

[![Enable translation sharing](/img/tutorials/localizing-drupal/25-drupal-sharing-1.png)](/img/tutorials/localizing-drupal/25-drupal-sharing-1.png){: .noborder}

[![Enter API key](/img/tutorials/localizing-drupal/26-drupal-sharing-2.png)](/img/tutorials/localizing-drupal/26-drupal-sharing-2.png){: .noborder}
