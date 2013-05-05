# Comment Blacklist Keywords for WordPress

Sometimes a simple solution is a better solution.

Over the past couple of years, I have identified 3,500 phrases, patterns, and keywords commonly used by spammers and comment bots in usernames, email addresses, link text, and URIs. This blacklist is still a work in progress and there is certainly room for optimization. Suggestions are always appreciated.

### How Do I Use It?

Copy the list of keywords, paste it into the [Comment Blacklist](http://codex.wordpress.org/Combating_Comment_Spam#Comment_Blacklist) field of your WordPress [Discussion Settings](http://codex.wordpress.org/Settings_Discussion_Screen) panel, and click the “Save Changes” button.

That’s it.

### Does It Really Work?

I certainly don’t blame you if you’re skeptical about how well this blacklist works compared to a commercial solution like [Akismet](http://akismet.com/). Due to the way I have subjectively included keywords based on comment spam submitted to my own sites, there is a chance that the blacklist will “overclean” your comment queue. Consider that fair warning.

However, [Jason Cosper](https://github.com/boogah) reports that he used the blacklist on a client’s WordPress installation containing 800,000 or so comments. The blacklist flagged 40% of those comments as “spammy”. As a sanity check, he then exported those flagged comments to a local install and subsequently ran them through Akismet. According to Jason, there were [“zero false positives.”](https://twitter.com/boogah/status/292031513590128640)

Booyah.

### Still need convincing?

The blacklist was written up by [John Saddington](http://john.do/) over at [WP Daily](http://john.do/) in the enticingly named post [Die Spam! Blacklist That Shiz with This Gist!](http://wpdaily.co/comment-blacklist-gist/)

### Questions?

Contact me on Twitter.

[@splorp](https://twitter.com/splorp)