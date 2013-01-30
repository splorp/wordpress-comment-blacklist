# Comment Blacklist Keywords for Wordpress

Created for those times when a simple solution is often a better solution. Over the past couple of years, I have identified nearly 3,000 phrases, patterns, and keywords commonly used by spammers and comment bots in usernames, email addresses, link text, and URIs. This blacklist is a continuous work in progress and there is certainly room for optimization.

If you’re a bit skeptical on how well this blacklist works compared to a commercial solution like Akismet, I don’t blame you. Because of the way I have subjectively included keywords, there is a chance that the blacklist will “overclean” your comment queue.

However (Jason Cosper)[https://github.com/boogah] reports that he used this blacklist on a client’s WordPress installation containing upwards of 800,000 comments. The blacklist flagged 40% of those comments as “spammy” which he exported to a local install and subsequently ran through Akismet. There were (no false positives)[https://twitter.com/boogah/status/292031513590128640].

As featured on WP Daily: (Die Spam! Blacklist That Shiz with This Gist!)[http://wpdaily.co/comment-blacklist-gist/]