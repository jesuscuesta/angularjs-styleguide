# HTTP/2 - Best practices on web applications

# Will We Have To Change Our Websites?

**HTTP/2 is backwards-compatible with HTTP/1.1**, so it would be possible to ignore it completely and everything will continue to work as before. The protocol change is completely transparent to users. Many readers of this article will have been using a protocol other than HTTP/1.1 for years. If you have a Gmail account and use Chrome to access it you will have been using SPDY and then HTTP/2 without knowing anything about it.

However, many of the things you think of as being best practices can be detrimental to performance under HTTP/2. Over time, as more servers update to use HTTP/2 and more people have browsers that support HTTP/2, your website, at one time well optimized according to best practices, will start to seem slower than websites optimized for the new protocol.

# What Do We Need To Change To Embrace HTTP/2? 

efore making changes to your website specifically for HTTP/2, you’ll also need to consider whether your visitors tend to have browsers that support it. Owners of websites that attract a lot of people using very up-to-date browsers will be able to make that switch sooner than owners whose logs show a majority of users on older browsers. To reflect this, I’ll also give you some suggestions on how to work in this transition time.

## 1. Make the move to TLS link

For a lot of websites the hardest thing about moving to HTTP/2 may not be HTTP/2 at all, but instead the requirement to run the site over a secure connection. If you are developing a new site or updating an old one your first move should be to make sure that you launch on or move to https as soon as possible. This is important not just for HTTP/2, Google uses secure connections as a ranking signal, and browsers are starting to flag non-https websites as ‘not secure’. In the future you will find that some powerful HTML5 features, such as geolocation, are unavilable without a secure connection.
If you have a site that is currently http only then my suggestion would be to prioritize a move to https first and then decide on your HTTP/2 strategy.

## 2. Turning multiple image files into sprites link

In HTTP 1.1, retrieving one large image is much more efficient for the browser than making a lot of requests for small ones. This is because multiple requests queue up behind each other. To work around this, we have been advised to turn our little icons into a sprite file.

The resulting sprite is returned with one HTTP request, preventing the problem of multiple requests being queued. However, even if the visitor is on a page that shows only one of those icons, they will still have to download a much larger file than they need to in order to see that one image.

With the **multiplexing ability of HTTP/2**, this queuing of resources is no longer an issue. Serving the small images individually will be better in many cases; you will only need to serve what is required for the page that the visitor is on. Creating a sprite will still be warranted in some cases; HTTP requests are only one aspect of performance. Combining some images together in a sprite might achieve better compression and, thus, a smaller download size overall, especially if all of those images are used on the page being loaded. However, it will no longer be the case that a sprite is always the best choice.

## 3. Inlining images using data uris link

Another workaround for the problem of multiple HTTP requests in HTTP/1.1 is to inline images in CSS using data URIs. Embedding images in this way will make a style sheet much larger. If you have combined this with another optimization technique for concatenating assets, then a visitor will likely download all of this code even if they never visit the pages where the images are being used.
With HTTP requests being very cheap in HTTP/2, this “best practice” will hinder rather than help performance.

## 4. Concatening CSS and Javascript

As the final step in our build process, many of us will concatenate all of the small CSS and JavaScript files used on our website. We often want to keep these separated while developing to make it easier to manage these resources — but we know that delivering one file to the browser is more efficient for performance than delivering five. Once again, we are trying to limit HTTP requests.

If you are doing this, then a visitor who lands on your home page might download all of the CSS and JavaScript required for your website, even if they never use most of it. As a developer, you can get around this problem by carefully selecting and including specific files for each area of the website in your build process, but that can be quite a lot of work.

An additional issue with concatenation is that everything will need to be purged from the cache at once. You can’t give some files that never change a long expiry date while giving often changing parts of the code base a shorter date. It all has to be expired if even one line of CSS, used on a single page, is changed.

I imagine you see where this is going! **HTTP requests are cheap in the world of HTTP/2**. Organizing your assets during development according to the pages on which they will be used will be far better. You can then serve up only the code that the visitor needs. Downloading a lot of tiny style sheets won’t matter. You could also organize based on how frequently things change; assets with longevity could then be cared for longer.

## 5. Splitting resources between hosts: Sharding Link

With HTTP/1.1, you are restricted to the number of open connections. If loading a large number of resources is unavoidable, one method to get around this restriction is to retrieve them from multiple domains. This is known as domain sharding. This can achieve better loading times, yet can cause problems itself, not to mention the development overhead of preparing this for your website.

**HTTP/2 removes this need for domain sharding** because you can request as many resources as you need. In fact, this technique will likely hurt performance because it creates additional TCP connections and hinders HTTP/2 from prioritizing resources.

# Conclusion
Build your application prepare for http and http/2. Polymer does something similar with bundle and unbundle version. Apply both techniques of optimization on each version of your web application to get ready when http/2 is stablished and commonly used.
