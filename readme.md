# Comment Blacklist Keywords for Wordpress

Sometimes a simple solution is a better solution.

Over the past couple of years, I have identified nearly 3,000 phrases, patterns, and keywords commonly used by spammers and comment bots in usernames, email addresses, link text, and URIs. This blacklist is still a work in progress and there is certainly room for optimization. Suggestions are always appreciated.

If you’re a bit skeptical on how well this blacklist works compared to a commercial solution like [Akismet](http://akismet.com/), I don’t blame you. Due to the way I have subjectively included keywords based on comment spam submitted to my own sites, there is a chance that the blacklist will “overclean” your comment queue. Consider that fair warning.

However, [Jason Cosper](https://github.com/boogah) reports that he used the blacklist on a client’s WordPress installation containing 800,000 or so comments. The blacklist flagged 40% of those comments as “spammy”. As a sanity check, he then exported those flagged comments to a local install and subsequently ran them through Akismet. According to Jason, there were [“zero false positives.”](https://twitter.com/boogah/status/292031513590128640)

Booyah.

Still need convincing? The blacklist was recently written up by [John Saddington](http://john.do/) over at [WP Daily](http://john.do/) in the enticingly named post [Die Spam! Blacklist That Shiz with This Gist!](http://wpdaily.co/comment-blacklist-gist/)