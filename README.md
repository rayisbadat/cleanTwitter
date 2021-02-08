How To  Use
-----------
* Get a Twitter API key
* Copy settings.ini.example to settings.ini and update with Consumer and Access keys
* To blockchain (aka block all followers of a user) `./cleanTwitter.py --blockchain targetUserName`
* To unretweet a retweet `./cleanTwitter.py --unretweet UUID`
* To unlike a like `./cleanTwitter.py --unretweet UUID`
* I feed those UUIDs in by requesting my data from twitter and using jq to parse the data and feed it into a loop.  Not the most efficent method.
* To get the UUID from your twitter data download ::

    echo "[{ $( sed '1d' tweet.js)"  | jq '.[].tweet.id' > /tmp/tweets.list
    while read ID ; do python3 cleanTwitter.py --unretweet "${ID//\"}"; done < /tmp/tweets.list 



Acknolwedgements
----------------
* I learend , and copied a lot of initial code, from https://github.com/magnusnissel/cleantweets project and from the tweepy docs.

