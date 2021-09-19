# twitter searching

## logic

`watching now` containing both "watching" and "now"

`"happy hour"` Finds tweets: containing the exact phrase "happy hour."

`love OR hate` Finds tweets: containing either "love" or "hate" (or both).

### Negation

`beer -root` Finds tweets: containing "beer" but not "root."

### combine

`from:NASA filter:media -filter:images`

`(puppy OR kitten) AND (sweet OR cute) -filter:nativeretweets min_faves:10`

`space (big OR large) list:nasa/astronauts (source:twitter_for_iphone OR source:twitter_web_client) filter:images since:2011-01-01 -#asteroid`

## symbols

`$twtr` containing a cashtag, useful for following stock information

`#haiku` Finds tweets: containing the hashtag "haiku."

## people

`from:alexiskold` Finds tweets: sent from person "alexiskold."

`to:techcrunch` Finds tweets: sent to person "techcrunch."

`@mashable` Finds tweets: Referencing person "mashable."

`list:NASA/space-tweets` sent from a Twitter account in the NASA List space-tweets

## geo

`"happy hour" near:"san francisco"` Finds tweets: containing the exact phrase "happy hour" and sent near "san francisco."

`near:NYC within:15mi` Finds tweets: sent within 15 miles of "NYC."

## timeline

`superhero since:2010-12-27` Finds tweets: containing "superhero" and sent since date "2010-12-27" (year-month-day).

`ftw until:2010-12-27` Finds tweets: containing "ftw" and sent up to date "2010-12-27."

## feelings

`movie -scary :)` Finds tweets: containing "movie", but not "scary," and with a positive attitude.

`flight :(` Finds tweets: containing "flight" and with a negative attitude.

`traffic ?` Finds tweets: containing "traffic" and asking a question.

## actions

`puppy min_retweets:5` containing "puppy" with a minimum of 5 Retweets

`puppy min_faves:10` containing "puppy" with a minimum of 10 likes

`puppy min_replies:100`containing "puppy" with a minimum of 100 replies

## urls

`hilarious filter:links` Finds tweets: containing "hilarious" and linking to URLs.

`puppy url:twitter` containing "puppy" and a URL with the word "twitter" anywhere within 
it

`news source:twitterfeed` Finds tweets: containing "news" and entered via TwitterFeed  (common sources are "tweetdeck", "twitter_for_iphone", "twitter_for_android" and "twitter_web_client")

## filter

`politics filter:safe` containing "politics" with Tweets marked as potentially sensitive 
removed

`breaking filter:verified` containing the word "breaking" from verified users only

`puppy filter:nativeretweets` Retweets containing "puppy"

`puppy filter:retweets`old style Retweets ("RT") and quoted Tweets containing "puppy"

### media

`kitten filter:media` containing "kitten" and an image or video

`kitten filter:native_video` containing "kitten" and an uploaded video, Amplify video or Periscope

`kitten filter:periscope` containing "kitten" and a Periscope video URL

`kitten filter:images` containing "kitten" and links identified as photos

`kitten filter:twimg` containing "kitten" and a pic.twitter.com link representing one or more photos

