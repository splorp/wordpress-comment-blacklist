# Comment Blacklist for WordPress

Sometimes a simple solution is a better solution.

Over the past couple of years, I have identified over 6,200 phrases, patterns, and keywords commonly used by spammers and comment bots in usernames, email addresses, link text, and URIs. This blacklist is still a work in progress and there is certainly room for optimization. Suggestions are always appreciated.

### How Do I Use It?

Copy the list of keywords found in the [blacklist.txt](https://raw.github.com/splorp/wordpress-comment-blacklist/master/blacklist.txt) file, paste it into the [Comment Blacklist](http://codex.wordpress.org/Combating_Comment_Spam#Comment_Blacklist) field of your WordPress [Discussion Settings](http://codex.wordpress.org/Settings_Discussion_Screen) panel, and click the “Save Changes” button.

That’s it.

### Does It Really Work?

I don’t blame you if you’re skeptical about how well this blacklist works compared to a commercial solution like [Akismet](http://akismet.com/). Because I am subjectively including keywords based on comment spam submitted to my own sites, there is a chance that the blacklist will “overclean” your comment queue. Consider that fair warning.

However, [Jason Cosper](https://github.com/boogah) reports that he used the blacklist on a client’s WordPress installation containing 800,000 or so comments. The blacklist flagged 40% of those comments as “spammy”. As a sanity check, he then exported those flagged comments to a local WordPress install and subsequently had Akismet do its thing. According to Jason, there were [“zero false positives.”](https://twitter.com/boogah/status/292031513590128640)

Still need convincing? The blacklist was featured over at [WP Daily](http://wpdaily.co/) in [John Saddington](http://john.do
/)’s enticingly titled post, [Die Spam! Blacklist That Shiz with This Gist!](http://wpdaily.co/comment-blacklist-gist/)

### Technical Considerations & Known Issues

WordPress stores the contents of the [Comment Blacklist](http://codex.wordpress.org/Combating_Comment_Spam#Comment_Blacklist) setting in a MySQL column named `blacklist_keys`. Defined as a `longtext` [data type](http://dev.mysql.com/doc/en/blob.html), this column can contain up to 4,294,967,295 bytes (approximately 4GB) of text. There is no chance of us running out of room to expand the blacklist any time soon.

However, nothing is perfect and WordPress is no exception. Apparently the comment blacklist has an issue with using `/5.` as a keyword. Including this keyword in your blacklist will cause all comments to be flagged as spam, regardless of their content or whether the commenter has been previously approved. It’s just weird.

### Mad Props

I would like to thank [Mika Epstein](https://github.com/ipstenu), [Claudio Schwarz](https://github.com/purzlbaum), and [Volker Schmidt](https://github.com/volkerjschmidt) for their suggestions, testing, and reports from the field.

### Questions?

Contact me on Twitter.

[@splorp](https://twitter.com/splorp)