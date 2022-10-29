# Comment Blacklist for WordPress

**Sometimes simple is better.**

Since 2011, I have painstakingly identified, compiled, and optimized over 47,000 phrases, patterns, and keywords commonly used by spammers and comment bots in usernames, email addresses, link text, and URIs. As with all compilations, this blacklist is a work in progress and there will always be room for improvement and optimization.

Suggestions and bug reports are certainly appreciated. Please use the [issue tracker](https://github.com/splorp/wordpress-comment-blacklist/issues) to let me know.

## How Do I Use It?

**Manual Installation**

Copy the list of keywords found in the [blacklist.txt](https://raw.githubusercontent.com/splorp/wordpress-comment-blacklist/master/blacklist.txt) file, paste it into the [Comment Blacklist](https://codex.wordpress.org/Combating_Comment_Spam#Comment_Blacklist) field of your WordPress [Discussion Settings](https://wordpress.org/support/article/settings-discussion-screen/) panel, and click the “Save Changes” button.

That’s it.

Repeat this procedure each time you want to install an updated version of the blacklist.

**Automatic Updates Via Plugin**

If you prefer a more hands-off approach, there are several plugins that will check whether the [master blacklist](https://raw.github.com/splorp/wordpress-comment-blacklist/master/blacklist.txt) has changed and then automatically install the most recent version. How handy is that?

+ [Block List Updater](https://wordpress.org/plugins/blacklist-updater/) by [Pluginkollektiv](https://pluginkollektiv.org/)
+ [Comment Blacklist Manager](https://wordpress.org/plugins/comment-blacklist-manager/) by [Andrew Norcross](https://github.com/norcross)
+ [Comment Blacklist Updater](https://wordpress.org/plugins/comment-blacklist-updater/) by [Apasionados](https://apasionados.es/)
+ [Shield Security](https://wordpress.org/plugins/wp-simple-firewall/) by [Shield Security](https://getshieldsecurity.com/)
+ [WP Toolbelt](https://github.com/BinaryMoon/wp-toolbelt) by [Ben Gillbanks](https://github.com/BinaryMoon)
+ [Zero Spam for WordPress](https://wordpress.org/plugins/zero-spam/) by [Highfivery](https://www.highfivery.com/)

For users of the [Gravity Forms](https://www.gravityforms.com/) custom form builder, [Gravity Forms Blocklist](https://gravitywiz.com/documentation/gravity-forms-blocklist/) is an add-on that takes advantage of the automatic blacklist updates provided by one of the aforementioned plugins.

## Does It Really Work?

I don’t blame you if you’re skeptical about how well this blacklist works compared to a commercial solution like [Akismet](https://akismet.com/). Because I am subjectively including keywords based on comment spam submitted to my own sites, there is a chance that the blacklist will “overclean” your comment queue.

Consider that fair warning.

However, [Jason Cosper](https://github.com/boogah) reports that he used an earlier version of the blacklist on a client’s WordPress installation containing 800,000 or so comments. The blacklist flagged 40% of those comments as “spammy”. As a sanity check, he then exported those flagged comments to a local WordPress install and subsequently had Akismet do its thing. According to Jason, there were [“zero false positives.”](https://twitter.com/boogah/status/292032803359584256)

Still need convincing? The blacklist was featured over at [WP Daily](https://torquemag.io/2013/07/torque-and-the-wp-daily-archives/) (now [Torque](https://torquemag.io/)) in [John Saddington](https://john.do/)’s enticingly titled post, [Die Spam! Blacklist That Shiz with This Gist!](https://torquemag.io/2013/01/comment-blacklist-gist/)

## Technical Considerations

WordPress stores the contents of the [Comment Blacklist](https://codex.wordpress.org/Combating_Comment_Spam#Comment_Blacklist) setting in the options table as `blacklist_keys`. Defined as a `longtext` [data type](https://dev.mysql.com/doc/refman/8.0/en/blob.html), this MySQL column can contain up to 4,294,967,295 bytes (approximately 4GB) of text. There is no chance of us running out of room to expand the blacklist any time soon.

There has been some talk about storing the `blacklist_keys` option in [an entirely separate table](https://core.trac.wordpress.org/ticket/30932).

## Known Issues, Limitations & Other Gotchas

**URL Shorteners**

As mentioned above, the keywords in the blacklist are based on spam submitted to my own sites. Spammers often utilize the [obscuring capabilities of URL shorteners](http://certmag.com/spammers-storm-url-shortening-services/) to hide their nefarious links. Therefore, I have included a handful of [URL shortener domains](https://raw.githubusercontent.com/splorp/wordpress-comment-blacklist/master/reference/shorteners.txt) in the blacklist. For all practical purposes, there’s no need for a comment to include a shortened URL, as unmodified links can be easily formatted using HTML. If you find that your visitors are using shortened URLs on a regular basis, you may wish to remove some or all of [these domains](https://raw.githubusercontent.com/splorp/wordpress-comment-blacklist/master/reference/shorteners.txt) from the blacklist.

**WordPress Links**

Spammers will also utilize links that include URLs that are specific to WordPress installations. These links often point at compromised admin files, themes, or plugins. In most cases, there’s no need to include a URL that deep-links into the bowels of a WordPress site. However, you may want to remove the following keywords from the blacklist if your visitors are commenting on topics related to WordPress site, plugin, or theme development.

+ /wp-admin
+ /wp-content
+ /wp-image
+ /wp-include
+ /wp-json
+ /wp-list
+ /wp-plugin
+ /wp-site

**Non-English Comments**

This blacklist has been created for use on English language sites. There are several dozen terms and phrases included in the blacklist that may flag legitimate comments posted in other languages. If you commonly receive comments in other languages (specifically those containing Chinese, Japanese Hiragana and Katakana, Korean, Thai, or Cyrillic characters), you may want to remove or modify those sections of the blacklist.

**HTML Tag Attributes**

The blacklist is not applied against HTML tag attributes found in comments, only the values assigned to those attributes. This means that you cannot include the attribute name, equal sign, or the quote marks as part a keyword. For example, the keyword phrase `title="Discount` will not match anything, even if that exact bit of text exists within the content of an HTML formatted comment. A keyword consisting of `Discount` should be used instead. Other HTML attributes commonly allowed in WordPress comments such as `href`, `cite`, `rel`, and `datetime` are also ignored.

**User Agent Strings**

According to the WordPress [Discussion Settings Screen](https://wordpress.org/support/article/settings-discussion-screen/) documentation, a comment will be marked spam if any of the [Comment Blacklist](https://codex.wordpress.org/Combating_Comment_Spam#Comment_Blacklist) keywords are found in the comment content, name, URL, email, or IP address fields. Surprisingly, WordPress also applies the blacklist against the [user agent](https://en.wikipedia.org/wiki/User_agent) string.

For example, an earlier version of the blacklist contained the keywords `/4.` and `/5.` to flag URLs with sequentially numbered pages with various file extensions. Unfortunately, these two benign-looking keywords also flagged comments containing common user agent strings, such as `Mozilla/4.0` and `Chrome/5.0`. In other words, nearly every single comment was flagged as spam, regardless of its content or whether the commenter had been previously approved.

**IPv6 Localhost**

Since the blacklist is applied to commenter’s IP address, we need to be aware of strings that might match seemingly generic, but valid addresses.

For example, in an earlier version of the blacklist the keyword `::` had been included, as it appeared occasionally in mangled comment text and URLs. However, double colons are also part of the [IPv6 localhost](http://en.wikipedia.org/wiki/Localhost) IP address `::1`. If you happened to be testing a WordPress installation on a system using IPv6 addresses, every single comment would have been flagged as spam.

## Mad Props

*“So much for using Akismet.”*

Thanks to [Mika Epstein](https://github.com/ipstenu), [Ben Gillbanks](https://github.com/BinaryMoon), [Paul Goodchild](https://twitter.com/PaulGoodchild), [Sergej Müller](https://github.com/sergejmueller), [Andrew Norcross](https://github.com/norcross), [Clifford Paulick](https://github.com/cliffordp), [Fabrizio Salmi](https://github.com/fabriziosalmi), [Volker Schmidt](https://github.com/volkerjschmidt), and [Claudio Schwarz](https://github.com/purzlbaum) for their various contributions, suggestions, and reports from the field.

Likewise, [Chris Burton](https://chrisburton.me/) deserves a virtual fist bump for the above quote.

I’d also like to acknowledge [John Hughes](https://themeisle.com/blog/stop-comment-spam-on-wordpress/), [Paul Taubman](http://ineedhelpwithwordpress.com/fight-comment-spam/), [Christina Robinson](https://thelovelygeek.com/3-ways-combat-spam-wordpress-blog/), [My Brain Lounge](https://mybrainlounge.wordpress.com/2014/09/21/how-i-stopped-wordpress-comment-spam/), [Roger Williams Media](https://rogerwilliamsmedia.com/forget-akismet-just-add-github-comment-blacklist/), [eComStyle.de](https://ecomstyle.de/blog/easycontact-einfachere-kontaktaufnahme-zeitgemaesser-spamschutz/), [FliegenToeter](https://fliegentoeter.eu/wordpress-abspecken-cpu-nutzung-minimieren-server-entlasten-ladezeit-verkuerzen/), [WPCoder](https://web.archive.org/web/20150428074751/http://cup.wpcoder.de/wordpress-antispam-guide/), [Nguyễn Đình Quân](https://www.narga.net/stop-wordpress-spam-comments-trackbracks/), and [Torque](https://torquemag.io/2013/01/comment-blacklist-gist/) for mentioning and linking to this project.

## History

See the [history](https://github.com/splorp/wordpress-comment-blacklist/blob/master/history.md) for a chronological list of changes, bug fixes, and other milestones.

## License

Copyright © 2011–2022 Grant Hutchinson

This project is licensed under the short and sweet [MIT License](https://opensource.org/licenses/MIT). This license allows you to do anything pretty much anything you want with the contents of the repository, as long as you provide proper attribution and don’t hold anyone liable.

Please refer to the [license](https://github.com/splorp/wordpress-comment-blacklist/blob/master/license.txt) included with the source for more information.

## Questions?

Contact me via [email](mailto:grant@splorp.com) or [Twitter](https://twitter.com/splorp).
