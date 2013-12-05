# Comment Blacklist for WordPress

Sometimes a simple solution is a better solution.

Over the past couple of years, I have identified over 6,800 phrases, patterns, and keywords commonly used by spammers and comment bots in usernames, email addresses, link text, and URIs. This blacklist is still a work in progress and there is certainly room for optimization. Suggestions and bug reports are certainly appreciated. Please use the [issue tracker](https://github.com/splorp/wordpress-comment-blacklist/issues) to let me know.

### How Do I Use It?

Copy the list of keywords found in the [blacklist.txt](https://raw.github.com/splorp/wordpress-comment-blacklist/master/blacklist.txt) file, paste it into the [Comment Blacklist](http://codex.wordpress.org/Combating_Comment_Spam#Comment_Blacklist) field of your WordPress [Discussion Settings](http://codex.wordpress.org/Settings_Discussion_Screen) panel, and click the “Save Changes” button.

That’s it.

### Does It Really Work?

I don’t blame you if you’re skeptical about how well this blacklist works compared to a commercial solution like [Akismet](http://akismet.com/). Because I am subjectively including keywords based on comment spam submitted to my own sites, there is a chance that the blacklist will “overclean” your comment queue. Consider that fair warning.

However, [Jason Cosper](https://github.com/boogah) reports that he used an earlier version of the blacklist on a client’s WordPress installation containing 800,000 or so comments. The blacklist flagged 40% of those comments as “spammy”. As a sanity check, he then exported those flagged comments to a local WordPress install and subsequently had Akismet do its thing. According to Jason, there were [“zero false positives.”](https://twitter.com/boogah/status/292031513590128640)

Still need convincing? The blacklist was featured over at [WP Daily](http://wpdaily.co/) in [John Saddington](http://john.do
/)’s enticingly titled post, [Die Spam! Blacklist That Shiz with This Gist!](http://wpdaily.co/comment-blacklist-gist/)

### Technical Considerations

WordPress stores the contents of the [Comment Blacklist](http://codex.wordpress.org/Combating_Comment_Spam#Comment_Blacklist) setting in a MySQL column named `blacklist_keys`. Defined as a `longtext` [data type](http://dev.mysql.com/doc/en/blob.html), this column can contain up to 4,294,967,295 bytes (approximately 4GB) of text. There is no chance of us running out of room to expand the blacklist any time soon.

### Known Issues

**URL Shorteners**

As mentioned above, the keywords in the blacklist are based on spam submitted to my own sites. Spammers often utilize the obscuring capabilities of URL shorteners to hide their nefarious links. Therefore, I have included a handful of URL shortener domains in the blacklist. For all practical purposes, there’s no need for a comment to include a shortened URL, as unmodified links can be easily formatted using HTML. You may want to remove the following keywords from the blacklist if you find that your visitors are using shortened URLs on a regular basis.

+ bit.ly
+ clck.ru
+ is.gd
+ tinyurl.com
+ tiny.cc
+ tr.im

**Non-English Comments**

This blacklist has been created for use on English language sites. There are several dozen terms and phrases included in the blacklist that may flag legitimate comments posted in other languages. If you commonly receive comments in other languages (specifically those containing CJK, Hiragana, Katakana, or Cyrillic characters), you may want to remove or modify those sections of the blacklist.

**User Agent Strings**

According to the WordPress [Discussion Settings Screen](http://codex.wordpress.org/Settings_Discussion_Screen) documentation, a comment will be marked spam if any of the [Comment Blacklist](http://codex.wordpress.org/Combating_Comment_Spam#Comment_Blacklist) keywords are found in the comment content, name, URL, email, or IP address fields. Surprisingly, WordPress also applies the blacklist against the [user agent](http://en.wikipedia.org/wiki/User_agent) string.

For example, in an earlier version of the blacklist the keywords `/4.` and `/5.` had been included to flag URLs with sequentially numbered pages with various file extensions. Unfortunately, these two benign-looking keywords also flagged comments containing common user agent strings, such as `Mozilla/4.0` and `Chrome/5.0`. In other words, nearly every single comment was flagged as spam, regardless of its content or whether the commenter had been previously approved.

### Mad Props

I would like to thank [Mika Epstein](https://github.com/ipstenu), [Claudio Schwarz](https://github.com/purzlbaum), and [Volker Schmidt](https://github.com/volkerjschmidt) for their suggestions, testing, and reports from the field.

### History

+ 20131105 — Migrated project to [GitHub](https://github.com/splorp/wordpress-comment-blacklist)
+ 20131020 — Blacklist contains over 6,000 entries
+ 20130911 — Blacklist contains over 5,000 entries
+ 20130715 — Blacklist contains over 4,000 entries
+ 20130226 — Blacklist contains over 3,000 entries
+ 20130130 — Added documentation
+ 20130130 — Mentioned on [WP Daily](http://torquemag.io/comment-blacklist-gist/)
+ 20120529 — Blacklist contains over 2,000 entries
+ 20120217 — Blacklist contains over 1,000 entries
+ 20111122 — Released as a [Gist](https://gist.github.com/splorp/1385930) with just over 140 entries


### Questions?

Contact me on Twitter.

[@splorp](https://twitter.com/splorp)