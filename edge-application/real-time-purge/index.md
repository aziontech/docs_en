# Real-Time **Purge** {#real-time-purge-title}

[Edit on GitHub <svg width="14" height="14" xmlns="http://www.w3.org/2000/svg"><g fill="none" stroke="#F3652B"><path d="M4.81.71H.672v11.43H12.1V8.001" stroke-width=".8"/><path d="M6.87.786h5.155V5.94M6.31 6.5L12.026.786"/></g></svg>](https://github.com/aziontech/docs_en/edit/master/edge-application/real-time-purge/index.md)

Through Real-Time Purge you can instantly delete your content cache on Azion.

> 1. [Content update strategies](#Content-update-strategies)
> 2. [Real-Time Purge](#real-time-purge)
> 3. [Types of Purge](#Types-of-Purge)
> 4. [Purge methods](#Purge-methods)
> 5. [Purge objects with varying content](#Purge-objects-with-varying-content)
> 6. [Purge confirmation](#Purge-confirmation)
> 7. [Limits](#limits)

---

## 1. Content update strategies {#Content-update-strategies}

When you update content at its source, you must choose the best strategy for updating it in the Azion cache.

| Expiration time | Names of objects with version | Real-Time Purge |
|--------------------|-----------------------------|-----------------|
| When configuring your cache policy, you determine how long you want your objects to be cached in Azion. When you update your content at the source, Azion will be able to continue serving a cached copy of it for as long as you have defined it. | We recommend that, whenever possible, you use some versioning marker with the name of your objects. When you update it at the source, you increase the version in the name of the object, forcing each change of its content to be treated as a new object by Azion.| If you deem it necessary, you can instantly delete your content cache in Azion in both Edge Caching and L2 Caching. By doing this, you instruct Azion to fetch the most recent version of your content from the source.|


Whenever possible, use cache policies with long expiry times for your content, such as 1 year (setting the Maximum TTL field to 31,536,000 seconds). By doing this, you will be optimizing the performance of your content or application, improving the experience for your users, reducing your traffic with Azion and reducing the load at your source.

To version the name of your objects, you can use a sequential number, a timestamp or other mechanism that you think is most appropriate as a version marker. For example, instead of naming an image as image.jpg, you could call it image_1.jpg and, when you need to update it, increase the version to image_2.jpg. In this way, any update of your content will be treated as a new object by Azion, which guarantees you the following benefits:

*   It allows you to control which object a request should return, even if the user has the previous version locally saved in the browser cache or in some intermediate cache. Even if the Azion cache is removed, the user can still access the old version of their local caches, until the expiration time elapses.
*   Through Raw Logs, you can follow the served versions of your objects, making it easier to analyze the results of your changes.
*   Versioning makes it possible for you to serve different versions of your objects to different users.
*   It also simplifies the rollback process in case of problems with your update.

---

## 2. Real-Time Purge {#real-time-purge}

By providing a fast and predictable purge operation, Azion makes it possible for you to increase the expiry time (TTL) of your cached objects, or cache event-drive objects, improving the offload and performance of your content or application, in addition to reducing your traffic with Azion.

When using Real-Time Purge to manage the expiration of your content cache, you can also perform:

*   Dynamic content caching and API responses, without sacrificing the user experience, as Azion's Edge Caching and L2 Caching products will be updated with your latest content.
*   Better cache efficiency, ensuring greater control over how your objects are served by Azion.
*   Better and more predictable management of obsolete or outdated objects, assisting its developers in building reliable, resilient and better performing solutions.

In addition, we offer two interface options for performing object purge in Edge Caching and L2 Caching in cache: via [Real-Time Manager](https://manager.azion.com/) or via [Azion API]({% tl api_v3_real_time_purge %}).

To access Real-Time Purge via the web:

1.  Access Real-Time Manager.
2.  Enter the Real-Time Purge menu.
3.  Fill in the requested arguments and click on the Purge button.

---

## 3. Types of Purge {#Types-of-Purge}

You can purge the Edge Caching product as well as L2 Caching using the URL list as a parameter, or it can be done through a Wildcard expression or the Cache Keys list.

**URL Purge**

It allows for the purge of cached objects, giving a list of URLs as an argument. The URL format must be according to the standard: _scheme://host_ or just _host_, followed or not by a _/path_ and the  _?query-string_. By hiding the *scheme*, the contents of both "http" and "https" will expire.

A URL Purge is not recursive, which means that only the URLs entered will expire from the cache. The URLs are automatically converted to their respective Cache Keys, without considering any variation of content in the same URL. As this operation will not expire content variations based on cookies, device groups, image format or others, consider using the Cache Key Purge or Wildcard Purge for these situations. The expiration of content variations based on Query String can be performed using the URL Purge, since Query String is a component of the URL, as long as the arguments used for content variation are sent in the correct order in which they were presented. If you use the Query String Sort functionality, order the arguments in the request or consider using a Cache Key Purge or Wildcard Purge as an alternative.

If you use the asterisk (*) character in a URL Purge request, it will be treated as a character in the URL and not as a Wildcard.

Examples of a URL Purge:

~~~
www.yourdomain.com
static.yourdomain.com/include/site.css
static.yourdomain.com/include/site.js
dynamic.yourdomain.com/app.py?argument
~~~

**Wildcard Purge**

It allows for the purge of cached objects, giving a Wildcard expression as an argument. The Wildcard expression format must be according to the standard: _scheme://host_ or just _host_, followed or not by a /path and the ?query-string, with an asterisk character (*) in the path or query string.

The Wildcard expression is automatically converted to multiple objects in the same domain. To expire the content variations based on cookies, device groups or image format, for the same URL, use the URL with the expression “@@ *” at the end.

~~~
www.yourdomain.com/*
static.yourdomain.com/include/*.css
static.yourdomain.com/*/site.js
static.yourdomain.com/images/image_1.jpg?ims=*
dynamic.yourdomain.com/app.py@@*
~~~

You can even use multiple wildcards to select a complex pattern.
~~~
www.yourdomain.com/*/images*
static.yourdomain.com/*/*.css 
static.yourdomain.com/*/my-jscripts/*/*.js 
static.yourdomain.com/images/image_*.*?ims=*
dynamic.yourdomain.com/app*.*@@*
~~~


**Cache Key Purge**

It allows for the purge of cached objects, giving a list of Cache Keys as an argument.

A Cache Key is an index entry for an object in the Azion cache. The standard cache key format adopted by Azion uses the URL host and path to identify objects. You can specify an advanced cache key to identify different variations of an object, based on:

*   Query String or Query String Sort arguments.
*   Cookies (when using [Azion Application Acceleration]({% tl documentation_products_application_acceleration %})).
*   Device Groups (when using [Azion Adaptive Delivery]({% tl documentation_products_adaptative_delivery %})).
*   Image format according to browser support (when using [Azion Image Optimization]({% tl documentation_products_image_optimization %})).

To obtain the Cache Key, you must request the content using the Azion Debug Header (Pragma: azion-debug-cache), for example:

~~~
HEAD /path HTTP/1.1 Host: yourdomain.com Pragma: azion-debug-cache
~~~

The response will return a header with the cache key (X-Cache-Key), for example:

~~~
X-Cache-Key: yourdomain.com/path@@
~~~

Each variation of the object is represented by a separate cache key and is expired individually. For example, if there is an object variation by device group, each URL in each group will have a separate Cache Key with the separator “@@” and the name of the device group. To purge all variations, you must search for the cache key individually for each group.

Examples of Cache Key Purge:

~~~
www.yourdomain.com/@@ www.yourdomain.com/@@Mobile 
static.yourdomain.com/include/site.css 
static.yourdomain.com/include/site.js 
static.yourdomain.com/images/image_1.jpg?ims=880x@@ 
static.yourdomain.com/images/image_1.jpg?ims=880x@@webp
~~~

---

## 4. Purge methods {#Purge-methods}

**Delete**

The Delete method removes the object from the cache. In the next user's content request, an unconditional GET request will be made to the source.

This purge method prevents Azion from delivering an outdated object (_stale_), in the case that the source is inaccessible. Or instead of this, if the source is inaccessible, an error page will be delivered.

The use of the Delete method is indicated for:

*   Removing content from the Azion cache, after removing it from the source.
*   Forcing the removal and subsequent update of content for which the  _timestamp_ is not trusted.
*   Forcing the delivery of an error page in place of an outdated object (stale), if its source is inaccessible and Azion is unable to obtain the latest version of its content.

---

## 5. Purge objects with varying content {#Purge-objects-with-varying-content}

**Adaptive Delivery**

When using the Adaptive Delivery product, you will be using an advanced cache key. In addition to _host_ and _path_, the cache key will include the @@ separator followed by the device group name.

For example, for the same URL http://www.yourdomain.com/, using Adaptive Delivery, the cache keys could be:

~~~
www.yourdomain.com/@@
www.yourdomain.com/@@Mobile
www.yourdomain.com/@@Tablet
~~~

To purge objects with variations based on device groups, you can use a Cache Key Purge, reporting all the variations individually, or a Wildcard Purge, using @@* at the end.

Application Acceleration

When using cookie-based content variation, in addition to the host and path, the cache key will include the @@ separator followed by the name of the cookies used and values.

For example, for the same URL http://www.yourdomain.com/, using content variation based on the “user” cookie, the cache keys could be:

~~~
www.yourdomain.com/@@
www.yourdomain.com/@@user=user1 
www.yourdomain.com/@@user=user2
~~~

To purge objects with variations based on cookies, you can use a Cache Key Purge, reporting all the variations individually, or a Wildcard Purge, using @@* at the end.

When using Query String based content variation, in addition to the _host_ and _path_, will the cache key include the separator? and the query string arguments used. For example:

~~~
dynamic.yourdomain.com/product.py?id=1000 
dynamic.yourdomain.com/product.py?id=1001
~~~

To purge objects with variation based on query string, you could use a Cache Key Purge, reporting all the variations individually, or a Wildcard Purge, using ?* at the end, or a URL Purge, informing in the URL only the arguments used in the cache key. If you use Query String Sort, the arguments must be sent in the correct order.

**Image Optimization**

When using Image Optimization, you will be using an advanced cache key. In addition to _host_ and _path_, will the cache key include the separator? and the product arguments, in addition to the @@ separator for identifying image format variation supported by the browser.

Examples of cache keys using Image Optimization:

~~~
static.yourdomain.com/images/image.jpg@@ 
static.yourdomain.com/images/image.jpg@@webp 
static.yourdomain.com/images/image.jpg?ims=88x@@ 
static.yourdomain.com/images/image.jpg?ims=88x@@webp
~~~

To purge images processed by Image Optimization, you can use a Cache Key Purge, reporting all variations individually, or a Wildcard Purge, using * at the end.

**Sliced Files**

If you use cache optimization to deliver large files (_sliced files_), as in  _Progressive Download_ media, you will be using an advanced cache key. In addition to _host_ and _path_,  the cache key will include the @@ bytes = separator, for each slice of content.

Examples of cache keys using optimization for delivering large files:

~~~
static.yourdomain.com/midias/file.mp4@@bytes=0-1048575 
static.yourdomain.com/midias/file.mp4@@bytes=1048576-2097151
~~~

To purge objects using this optimization, you must use a Wildcard Purge, putting @@* at the end. You can also use the Cache Key Purge, as long as you enter the cache key for all _slices_ correctly.

Be careful when you purge individually for a _slice_ because if there is a change of content at the source, it may be inconsistent in the cache.

**Media Packager**

When using the Media Packager product to deliver your media in HLS, you will be using the dynamic packaging functionality, which automatically creates an m3u8 playlist and segments your media into ts chunks. The URL of your content will be created dynamically by Media Packager.

Examples of a cache key using Media Packager:

~~~
medias.yourdomain.com/your_id/_definst_/mp4:yourmedia.mp4/chunklist.m3u8 
medias.yourdomain.com/your_id/_definst_/mp4:yourmedia.mp4/media_1.ts 
medias.yourdomain.com/your_id/_definst_/mp4:yourmedia.mp4/media_2.ts 
medias.yourdomain.com/your_id/_definst_/mp4:yourmedia.mp4/media_3.ts
~~~

To purge objects created via Media Packager, you can use a Cache Key Purge, informing all playlist cache keys and chunks individually, or use a Wildcard Purge, placing * after the name of your media file.

**Live Ingest**

If you use the Live Ingest product to transmit your Live transmissions from RTMP to HLS, the m3u8 playlists and ts chunks will be created automatically.

You cannot purge this type of content. The m3u8 playlist and ts chunks will automatically expire via TTL.

**POST Method**

By default, Azion only allows caching of the GET and HEAD methods. You can enable the POST method cache in your Cache Settings, in which case you will be using an advanced cache key. In addition to the host and path, the cache key will include the @@ separator followed by the MD5 hash of the request body (POST arguments).

~~~
dynamic.yourdomain.com/path@@md5_of_post_arguments
~~~

To purge these objects, you can use a Cache Key Purge, reporting all variations individually, or a Wildcard Purge, using @@* at the end.

**Custom Configurations**

If you have a Custom Configuration with a custom cache key, you must use the Cache Key Purge to delete the cache of your objects. In addition to _host_ and _path_, the cache key may include the @@ separator followed by its custom arguments.

~~~
dynamic.yourdomain.com/path@@custom_arguments
~~~

You must consult the custom format of your cache key to run the Cache Key Purge.

---

## 6. Purge confirmation {#Purge-confirmation}

The purge is an operation that does not require confirmation. Since the Real-Time Purge is completed almost instantly, no confirmation of the operation is required and you can expect your purges to be completed in less than 3 seconds, except in the case of consistent use of Rate Limits.

When necessary, you can consult the purging history to find out which user made the request, the time, argument list, type and purge method.

---

## 7. Limits {#Limits}

The purge operation is performed according to the following usage limits, based on the type and number of objects being expired:

*   For URL and Cache Key Purges, up to 10,000 objects every 60 seconds, with up to 200 requests with 50 objects per request, per client. The URL and Cache Key are limited to 4,096 characters.
*   For Wildcard Purges, up to 2,000 requests per day (per 24h interval), one Wildcard URL per request. The Wildcard URL is limited to 256 characters.
*   Purging history is limited to 6 months and up to 1 million requests.

---

Didn't find what you were looking for? [Open a support ticket.](https://tickets.azion.com/)
