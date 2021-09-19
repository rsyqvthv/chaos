# Google searching



## notes

`michael jackson` 

- Google is case insensitive
- Search operators are case sensitive
- Without using any operators, Google will show pages with all words first, trying to find the words in order
- Google excludes common words (known as stop words) like 'I', 'the', 'a' etc
- Pay attention to operators that must be used alone

## operators

`pic +farm` required

`pig -bacon` excluded

`cat OR dog`, `cat | dog`

`“michael jackson”`

`(ipad OR iphone) apple` 

`apple AROUND(4) iphone` “apple” and “iphone” must be present in the content and no further than four words apart.

`the fix ~tips` also return with ‘help’, ‘guide’, ‘tutorial’ etc.

`looking for *` returns ‘looking for dogs’ or ‘looking for cats’

`apple CEO _ jobs` ‘_’ Not exactly a search operator, but acts as a wildcard for Google Autocomplete.

==`computer $500..$1000`== .. meansi range of numbering or ==`wwdc video 2010..2014`== Search for a range of numbers, date

`ideas date:6` search for ‘new’ page added to Google in X months

~~`ideas daterange:2453006-2453371` note: date use julian day format, date range of dded page. `kitty daterange:2008-01-20..2009-01-20` date range search [^daterange] , but google has took this function away.[^took away daterange]~~ ==use tool > anytime > custom range==

~~`phonebook:tim cook`~~

~~`#apple` Searches #hashtags. Introduced for Google+~~

`filetype:pdf`

`map:silicon valley` Force Google to show map results for a locational search.

~~`loc:”san francisco” apple` Find results/news from a given area.~~

`site:bbc.co.uk`

~~`link:bbc.co.uk`~~

`related:bbc.co.uk`

`cache:apple.com` return most recent cached version of a web page

~~`info:bbc.co.uk`~~

`define:Google`

`stocks:goog`

`weather:london`

`music:transformers`

`movie:transformers`

~~`inpostauthor:”steve jobs”`  only worked in Google Blog search~~

~~`allinpostauthor:steve jobs` Similar to “inpostauthor,” but removes the need for quotes~~

~~`inposttitle:apple`~~

`apple source:the_verge` Find news results from a certain source in Google News.

flight info, input from and  to airport code: `jfk lax` or `LHR PEK`

## seo

`intitle:google search`

`intext:google search`

`inurl:google search`

`inanchor:google search`

### must use alone

> allin+title/text/url/anchor

`allintitle:google search`

`allintext:google search`

`allinurl:google search`

`allinanchor:google search`

## calculation

`3+2` returns 5
`4-1` returns 3
`6*8 `returns 48
`15/5` returns 3
`3^2` returns 9 (3 raised to power 2)
`5%2` returns 1 (the remainder after division)

`sqrt(49)` returns 7
if you need non-square roots you can use for example `3th root of 27`.

sin, cos, arctan, tan... Trigonometry
`sin(pi/2)`
`tan (2/3*pi)`

Returns natural (base e) logarithm:`ln(e^5)`

Returns base 10 logarithm: `log(100)`

Returns n factorial: `3!`
Numbers can be entered also in hexadecimal, octal and binary base, using 0x, 0o and 0b prefixes, for example `5 +0xf+0b1001`

## conversions

convert radians to degrees: `pi/2 in degrees` 
convert degrees into radians: `90 degrees in radians`

`16 in hex
16 in binary
16 in octal
0xf in decimal`

`100miles in km`
`1m in mm
200000 km in light-second`

`100mph in kph
1 month in seconds
280 kelvin in celsius
50 fahrenheit in celsius`

`3 € in $` or `3 euros in dollars`

`3 teaspoons in oz`
`1 cup + 1 tablespoon in teaspoon` with calculation

## usage example

Find indexation errors,  to check results

- `site:mysite.com`
- `site:mysite.com/blog`
- `site:yourblog.com/category`
- `site:yourblog.com inurl:tag`

none-https

- `site:mysite.com -inurl:https`

find duplicate content

- `site:mysite.com “original content”` vs `-site:mysite.com "original content"`
- `intitle:"my content title" -site:mysite.com -pinterest` 
- `intext:”my original content piece” -site:mysite.com`

find odd files on your domain

- `site:mysite filetype:pdf`

Find guest post opportunities

- `fitness (intitle:"write for us" OR inurl:"write-for-us")`

> “become a contributor"
> “contribute to”
> “write for me” (yep—there are solo bloggers seeking guest posts, too!)
> “guest post guidelines”
> inurl:guest-post
> inurl:guest-contributor-guidelines
> etc.

Find resource page opportunities

- `intitle:fitness AND intitle:"resouces" AND inrul:resources)`

Find sites that feature infographics

- `fitness intitle:infographic inurl:infographic`

Find more link prospects… AND check how relevant they really are

- `related:mysite.com/blog`

then

- `site:a-site.com` note down results [all]
- `site:a-site.com key` note down results [key]
- [key] / [all] vs 0.5

Find social profiles

- `firstname lastname (site:twitter.com|site:facebook.com|site:linkedin.com)`

Find internal linking opportunities

- `site:mysite.com -site:mysite.com/pagename intext:"pagename"`

Find PR opportunities by finding competitor mentions

- `(intext:”competitor”) -site:competitor.com -site:mysite.com` vs `(intext:"mysite") -site:mysite.com`
- `allintitle:review (competitor1 OR competitor2)`

Find sponsored post opportunities

- `fitness intext:"sponsored post" inurl:"category/sponsored-post"`

Find Q+A threads related to your content

- `site:quora.com intitle:(SEO | "link building" | "keyword research")`

Find how often your competitors are publishing new content

- `site:www.competitor.com/blog` note down result
- `site:www.competitor.com/blog` with time period, note down the result
- compare the total results and time period results with self.

Find sites linking to competitors

- `links:competitor.com` do works, but not acurate.

## reference

[^ advanced google search]: http://jwebnet.net/advancedgooglesearch.html
[^daterange]: https://support.google.com/gsa/answer/2686926
[^tookawaydaterange]: https://support.google.com/googlenews/thread/688982
[^ 42 Advanced Operators]:https://ahrefs.com/blog/google-advanced-search-operators/