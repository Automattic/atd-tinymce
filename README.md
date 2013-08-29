atd-tinymce
===========

### After the Deadline for TinyMCE

[After the Deadline](http://www.afterthedeadline.com) is an [open source](http://open.afterthedeadline.com) software service that checks [spelling, style, and grammar.](http://www.afterthedeadline.com/features.slp).
This project contains an AtD TinyMCE Plugin and an example for using After the Deadline with [TinyMCE](http://tinymce.moxiecode.com).

### Quick Start

1.  Extract the contents of this zip file into the tiny_mce/plugins directory.
2.  You'll need to make up an API key. Ideally your application name followed by a string that is unique to this user is best. There is a performance benefit to using the same key for subsequent requests.
3.  You'll need to set three variables in your TinyMCE init:
4.  You'll need a proxy script on your server. Use the included proxy.php if you can. Otherwise you'll need to write your own.
5.  As a final note, make sure your webpage is encoded in UTF-8 format. AJAX requests use the encoding of the parent website and AtD expects UTF-8. This is important as AtD has better support for accented characters and we're working to support more languages.

### Examples

If you've unzipped this archive on a webserver with PHP installed, you should be able to access [demo.html](demo.html) directly and see everything work.

*   [demo.html](demo.html)

### Commercial use and running your own server

This software requires a running instance of an AtD server.  Automattic operates an instance that you can use for personal projects as long as you don't send too much traffic.  This library are configured to use this server by default.

For high volume and commercial uses of AtD, you must run your own server.  The code is available on Github: [After the Deadline Server](https://github.com/automattic/atd-server).  See the [After the Deadline Developer's page](http://open.afterthedeadline.com/) for more information, and check out the [AtD Developers Google Group](http://groups.google.com/group/atd-developers) for discussion and community support.  

When you run your own server, replace `service.afterthedeadline.com` with your server's hostname.

### Ignore Phrases Capability (Optional)

After the Deadline lets you specify a list of phrases it should not highlight. This is the AtD equivalent of add to dictionary functionality in other programs.
You can hardcode these values in the `atd_ignore_strings` value in TinyMCE init. 
The format is a comma separated list of phrases.  (See example below for more).

Users can choose to ignore phrases by selecting _Ignore always_ when clicking 
a highlighted phrase.  You have to enable this feature for the _Ignore always_
menu to show up.  Do so by setting the `atd_ignore_enable` to the string `"true"`
in TinyMCE init.

If you see _Ignore all_ when clicking an error then this feature is disabled.

#### Manage Ignored Phrases with Cookies

There is a caveat to this client side ignore capability.  You get to create the
user interface for unignoring rules.  The phrases are stored in a cookie named
`atd_ignore`.  This cookie was created with:

`tinymce.util.Cookie.setHash("atd_ignore", ...);`

The format of the cookie is _some+phrase=1&amp;someWord=1&amp;..._.  See the [TinyMCE API](http://tinymce.moxiecode.com/js/tinymce/docs/api/index.html#)
for [tinymce.util.Cookie](http://tinymce.moxiecode.com/js/tinymce/docs/api/index.html#class_tinymce.util.Cookie.html).

[support/atdphrases.js](support/atdphrases.js) and [support/unignore.html](support/unignore.html) are included in this archive to assist you.

#### Manage Ignored Phrases Yourself

The best option is to manage the ignored phrases preference on your server. We do this in our [WordPress 
plugin](http://wordpress.org/extend/plugins/after-the-deadline/). When we generate the TinyMCE init we pull the user's ignore preferences from our database and populate the `atd_ignore_strings` value with them.

The AtD TinyMCE plugin can be configured to make an AJAX call to your server when a user selects _Ignore Always_. To enable this set `atd_ignore_rpc_url` in the 
TinyMCE init. When set AtD will do a GET call to this URL with _the ignored phrase&key=api key_ appended.

### Error Categories

This TinyMCE plugin only shows grammar, spelling, and misused word errors by default.  All other categories of errors are filtered and you must explicitly
enable them in the TinyMCE init parameters by setting the `atd_show_types` variable.

`atd_show_types: "Bias Language,Cliches,Complex Expression,Diacritical Marks,Double Negatives,Hidden Verbs,Jargon Language,Passive voice,Phrases to Avoid,Redundant Expression",`

You may omit any of these categories.  Note that categories are separated by commas with no whitespace.  The category names are case sensitive and yes, voice is lowercase in Passive voice.

### Localization

To localize the strings in this extension, create an object with the localized strings. Here is an example:

<pre>var my_plugin_strings = {
   menu_title_spelling: "Spelling",
   menu_title_repeated_word: "Repeated	Word",
   menu_option_explain: "Explain...",
   menu_option_ignore_once: "Ignore suggestion",
   menu_option_ignore_always: "Ignore always",
   button_proofread_tooltip: "Proofread Writing"
   message_no_errors_found: "No writing errors were found.",
   message_server_error: "There was a problem communicating with the After the Deadline service. Try again in one minute."
};</pre>

Then make TinyMCE use these strings:

<pre>tinyMCE.addI18n('en.AtD', my_plugin_strings);</pre>

Note: I used _en.AtD_ to indicate _my_plugin_strings_ are an English translation of this AtD extension. For other languages use
_**lang**.AtD_ where _**lang**_ is the two letter language code value specified for _language_ in your TinyMCE init.

These string labels are compatible with the [AtD/jQuery extension](http://www.afterthedeadline.com/download.slp?platform=jQuery).

## License

[LGPL](http://www.opensource.org/licenses/lgpl-2.1.php)

This code is a hack on the spellcheck plugin from Moxiecode.  Thanks for the hard work guys.

## Contact

This code has always been open source.  We're putting it on Github so that you can feel free to fork it, hack it, and release your own version.

Join the [atd-developers](http://groups.google.com/group/atd-developers) list for community support.
