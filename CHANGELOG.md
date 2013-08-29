### 24 Mar 10

*   Updated to latest AtD/Core module:

        *   Added L10n string _menu_title_confused_word_ to localize "Did you mean..."
    *   Fixed two cases of parent variable polution (two for loops not declaring their vars)
    *   Fixed bug preventing subsequent occurences of one error (w/ the same context) from highlighting
    *   Error highlighter now uses beginning of word boundary to accurately find error location in text
    *   Fixed bug preventing misspelled words in single quotes from being highlighted

### 15 Feb 10

*   Fixed a highlighting issue
*   Fixed I18n issue with AtD/Core module
*   Fixed a bug where AtD Core was ignoring show types setting

### 14 Jan 10

*   Made plugin localizable. Just need string translations now :)
*   Plugin now uses AtD Core UI module. Created a make.sh script to combine Core UI script and editor plugin src. Will also minify them if jsmin is in the current path.

### 11 Dec 09

*   Error highlighting is better at not highlighting a suggestion within a word
*   Plugin now checks if a global constant, AtD_proofread_click_count exists. If it does--it increments it with each use.

### 12 Nov 09

*   Updated docs/examples to reflect AtD support for diacritical marks (accented words)
*   Plugin is now smarter about determining if no writing errors were highlighted and notifies the user when appropriate.

### 3 Nov 09

*   Overhauled readme, change log, and added a demo.html file.
*   Fixed a bug where highlighted errors could step on eachother (sometimes).

### 8 Sept 09

*   More updates than you can shake a stick at.

### 18 Jun 09

*   (18 Jun 09) Added a atd_strip_on_get option.  Some applications like WordPress grab the editor
  content occasionally for an auto save.  In these cases the app plugin needs to
  strip the AtD tags and this option should be set to false.*   (19 Jun 09) fixed syntax error in IE and Safari (that FF chose to ignore)...

### 1 Jun 09

*   (31 May 09) updated plugin to treat -- as a separator.
*   (31 May 09) fixed plugin not turning off progress thingie when an AJAX error occurs
*   (29 May 09) fixed plugin not highlighting anything when string field of an error response is empty.
*   (25 May 09) fixed a bug causing underline and some other styles to get mangled in Wordpress.  Oops. :)
*   (24 May 09) fixed a bug with token text containing encoded HTML elements
  rather than the text its meant to represent (i.e. &quote; over a ").
  This caused highlighting to mess up in some cases.
*   (24 May 09) fixed a bug preventing mispelled words with a hyphen from getting  highlighted.
*   (24 May 09) fixed a bug where [hookword] [word 1] was causing other phrases with the
  pattern [hookword] [word 1][rest of word] to get highlighted
*   (17 May 09) multiword phrases now properly set the "previous" token used as a hook for
  checking if the next word/phrase has an error associated with it.  Naturally this fixes
  a bug where an error following a highlighted phrase isn't highlighted.

### 15 May 09

*   Rewrote the word highlighting code, the new stuff is easier to mantain and much cleaner. This plugin is no longer such a bad hack.  It's still a hack though.
*   Added the atd_ignore_strings option and the atd_ignore_enable option.

### Release 14 Apr 09

*   updated readme to show correct fom for atd_rpc_url.  The variables requires a ?url= at the end.

