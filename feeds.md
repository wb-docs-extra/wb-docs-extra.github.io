---
layout: page
title: Feeds
---


###### Extra provides the following types of feeds:

+ __atom__ - http://en.wikipedia.org/wiki/Atom_(standard)
+ __kargo__ - vendor specific, mobile optimized feed (custom RSS).  Includes full content of the item when available.
+ __rss__ - http://en.wikipedia.org/wiki/RSS
+ __mrss__ - http://en.wikipedia.org/wiki/Media_RSS

*Unless otherwise noted, if the URI pattern contains `{feed_type}`, then any of the above types will work.*


###### Content Types:

+ __photos__ - May include links to Extra photo galleries, Instagram, etc.
+ __posts__ - Currently renders only Extra articles.  *May include other content types in the future.*
+ __videos__ - May include Extra Kaltura videos, YouTube videos or playlists and Vine videos.

*Unless otherwise noted, if the URI pattern contains `{content_type}`, then any of the above types will work.*


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
