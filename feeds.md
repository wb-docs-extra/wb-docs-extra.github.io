---
layout: page
title: Feeds
---


###### Extra provides the following types of feeds:

+ __atom__ - http://en.wikipedia.org/wiki/Atom_(standard)
+ __kargo__ - vendor specific, mobile optimized feed (custom RSS).  Includes full content of the item when available.
+ __rss__ - http://en.wikipedia.org/wiki/RSS
+ __mrss__ - http://en.wikipedia.org/wiki/Media_RSS

*Unless otherwise noted, if the URI pattern contains `{feed_type}` then any of the above types will work.*


###### Content Types:

+ __photos__ - May include links to Extra photo galleries, Instagram, etc.
+ __posts__ - Currently renders only Extra articles.  *May include other content types in the future.*
+ __videos__ - May include Extra Kaltura videos, YouTube videos or playlists and Vine videos.

*Unless otherwise noted, if the URI pattern contains `{content_type}` then any of the above types will work.*


###### Paging:

Feeds that support pagination will have an `atom:link` with the next link to follow, e.g.
`<link rel="next" type="application/atom+xml" href="{next_link}"/>`



***



## Available Feeds


###### All Content
+ `https://feeds.extratv.com/{feed_type}`
+ `https://feeds.extratv.com/{content_type}/{feed_type}`


###### Latest News
This is the Extra home page feed.

+ `https://feeds.extratv.com/latest-news/{feed_type}`
+ `https://feeds.extratv.com/latest-news/{content_type}/{feed_type}`


###### Filtered by Hashtag
+ `https://feeds.extratv.com/tags/{hashtag}/{feed_type}`
+ `https://feeds.extratv.com/tags/{hashtag}/{content_type}/{feed_type}`


###### Filtered by List
+ `https://feeds.extratv.com/lists/{list}/{feed_type}`
+ `https://feeds.extratv.com/lists/{list}/{content_type}/{feed_type}`


###### Syndication Partners
Renders 25 of the latest posts and does not support pagination.

+ `https://feeds.extratv.com/partners/{partner}/{feed_type}`



***



## ETags

All feeds will return an ETag that can be used to conditionally fetch a feed.  For example,
passing a header `If-None-Match: ETAG` will return a 304 status code if the content has not
been modified.  See [HTTP ETag](http://en.wikipedia.org/wiki/HTTP_ETag).

__CURL Example:__
{% highlight bash %}
# Get the ETag for the feed
etag=$(curl -s -I "https://feeds.extratv.com/rss" 2>|/dev/null | awk '/^ETag: / {print $2}' | sed 's/\"//g')
etag=`echo -n "${etag//[[:space:]]/}"`

# Verify the ETag, should return "HTTP/1.0 304 Not Modified"
eval "curl -s -I -H 'If-None-Match: \"$etag\"' \"https://feeds.extratv.com/rss\""


{% endhighlight %}
