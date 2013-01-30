# Comment Blacklist Keywords for Wordpress

Sometimes a simple solution is often a better solution.

Over the past couple of years, I have identified nearly 3,000 phrases, patterns, and keywords commonly used by spammers and comment bots in usernames, email addresses, link text, and URIs. This blacklist is still a work in progress and there is certainly room for optimization. Suggestions are always appreciated.

If you’re a bit skeptical on how well this blacklist works compared to a commercial solution like [Akismet](http://akismet.com/), I don’t blame you. Simply because of the way I have subjectively included keywords, there is always a chance that the blacklist will “overclean” your comment queue. Consider that fair warning.

However, [Jason Cosper](https://github.com/boogah) reports that he used this blacklist on a client’s WordPress installation containing upwards of 800,000 comments. The blacklist flagged 40% of those comments as “spammy”. He then exported those flagged comments to a local install and subsequently ran them through Akismet. There were [“zero false positives.”](https://twitter.com/boogah/status/292031513590128640)

Booyah.

Still need convincing? The blacklist was recently featured on WP Daily: [Die Spam! Blacklist That Shiz with This Gist!](http://wpdaily.co/comment-blacklist-gist/)