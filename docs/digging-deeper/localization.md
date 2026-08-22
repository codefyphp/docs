---
title: Localization
sidebar_title: Localization
summary: Localize CodefyPHP applications with translation helpers, locale configuration, Gettext POT catalogs, and translated PO language files.
keywords: php-localization,gettext,codefyphp-translation
order: 25
---

Codefy uses the [php-gettext/gettext](https://github.com/php-gettext/Gettext) library for translating strings. All location files 
are located in the `./locale` directory, organized by locale (folder). For convenience, a localization service provider 
(`Codefy\Framework\Providers\ConfigServiceProvide`) is included so that you don't have to instantiate or register the 
needed translation functions. To translate strings, you can use a program called [Poedit](https://poedit.net/). Poedit is available 
for macOS, Linux and Windows.

## Translation Helpers

There are several translation helpers you can use for different situations throughout your application:

 - `Codefy\Framework\Helpers\trans` - Translates a string. (Wrapper for [`t__`](helpers/t__.md) with the `locale_domain` key set in `./config/app.php`.)
 - `Codefy\Framework\Helpers\trans_attr` - Escapes a translated string to make it safe for HTML attribute. (Wrapper for [`esc_attr__`](helpers/esc_attr__.md).)
 - `Codefy\Framework\Helpers\trans_html` - Escapes a translated string to make it safe for HTML output. (Wrapper for [`esc_html__`](helpers/esc_html__.md).)

## Configure The Locale

The default language for the application is stored in the `./config/app.php` configuration file's `locale` 
option. You are free to modify this value to suit the needs of your application.

## Translating Your Application

If you want to translate your application, you can do so by creating and editing localization files.

### Localization Files

There are three types of Localization files you need in order to translate your application:

* __POT files:__ a template file with all your original strings
* __PO files:__ editable file with the translations to one language (one file per language)
* __MO files:__ compiled versions of the PO files, actually used by the application

### POT (Portable Object Template) files

The POT file contains the original strings (in English) in your application. Here is an example POT file entry:

    msgid ""
    msgstr ""
    "X-Domain: codefy\n"

There are many other entries in the `POT` file besides the three above, but what's important to point out is the 
`X-Domain` entry. This is the same domain used when using one of the translation helpers. Without the `X-Domain` entry, 
the strings will not get translated. You may need to edit this in your `POT` file, especially if you want to change the 
`domain` to something other than `codefy`

### Translate PO File

To create a new translation, you will need to make a copy of `./locale/codefy.pot`. Let's say that you want to translate your 
application into *Spanish*. Rename and move your copy of `codefy.pot` to `./locale/es/codefy-es.po`. Open your new .po file in Poedit, 
update from source code if needed, translate the strings, save, and a new `./locale/es/codefy-es.mo` file will get created. 
Any changes you make to your .po file, the .mo fie will get updated when you save your changes. When you change the locale string 
in `./config/app.php` from `en` to `es`, you should see your strings translated into *Spanish*.
