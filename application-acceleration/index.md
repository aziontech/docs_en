# Application **Acceleration**

This is the service of accelerating web applications and APIs through protocol optimizations and the management of the different requirements of dynamic content.

Through Application Acceleration you can configure advanced cache by path rules that allow granular caching, content segmentation and cache policies based on criteria such as name/value of Cookies and Query Strings, as well as features such as Bypass Cache, Forward Cookies and support for POST/PUT and other HTTP methods.

Application Acceleration extends the functionality of the Azion Edge Application product to allow you to configure rules per path to:

> 1. [Advanced Cache Key](#AdvancedCacheKey)
> 2. [Bypass Cache](#BypassCache)
> 3. [Forward Cookies](#ForwardCookies)
> 4. [Support for POST/PUT and other methods](#SuportePOSTPUT)

---

## 1. Advanced Cache Key {#AdvancedCacheKey}

You can used Azion to deliver your dynamic or static content. Even the dynamic part of a website can often be cached for a user profile, grouped according to the specific needs of your application, whether by city, browsing profile, or shopping profile. If you want your dynamic content to be cached on Azion's Edge Nodes, you can define advanced cache key rules based on Cookies or Query String.

As a standard, Azion considers each URL as a different object in cache. Through the Advanced Cache Key, you can configure a custom cache key rule based on Cookies or Query String and, with that, define the segmentation of your content in your application.

To use the functionality, follow these steps:

1. Acess [Real-Time Manager](https://manager.azion.com/)  and click the menu **Edge Services** and select **Edge Applications**.
2. Add or edit one **Edge Application**.
3. To enable the **Application Acceleration** module, continue in the tab **Main Settings** and select the option **Application Acceleration** in the section **Edge Application Modules**.
4. After enabling the module, access the tab **Cache Settings**.
5. In the tab **Cache Settings**, add or edit a custom cache setting.
6. In the **Advanced Cache Key** section, define your custom Cache by **Query String** and **Cache by Cookie** setting.
7. In the **Rules Engine** tab, add or edit a rule in **Request Phase** to define the behavior for one or more paths.
8. In the **Set Cache Policy** behavior, select the custom cache configuration.


**Cache by Query String**

At Azion you define how you want the content to be cached according to variations of Query String in your URLs:


* **Content does not vary by Query String (Improves Caching):** defines that the cache key must ignore the Query String, that is, two distinct URLs just by varying the Query String will be considered as the same cached object, for example http://seudominio.com/path?queryA e http://seudominio.com/path?queryB will deliver the same cache content to your users.
* **Content varies by some Query String fields (Whitelist):** you can list which Query String fields should be considered to differentiate between objects in the Azion Edge Caching. All other fields will be ignored. For example, if you list the field **city**, the URLs http://seudominio.com/path?cidade=A&nome=X and http://seudominio.com/path?cidade=A&nome=Y will be considered as a single object in cache, while URLs http://seudominio.com/path?cidade=A&nome=X and http://seudominio.com/path?cidade=B&nome=X will be considered as different objects.
* **Content varies by Query String, except for some fields (Blacklist):** you can list which Query String fields to ignore when differentiating cached objects. All other fields will be considered. For example, if you list the field **random**, the URLs http://seudominio.com/path?cidade=A&random=123 and http://seudominio.com/path?cidade=B&random=123 will be considered different object in cache, while http://seudominio.com/path?cidade=A&random=123 and http://seudominio.com/path?cidade=A&random=456 will be considered as the same object in cache.
* **Content varies by all Query String fields:** defines that the cache key must consider all Query String fields, that is, two different URLs by the variation of the Query String will be considered as two different cached objects, for example http://yourdomain. com/path?queryA and http://yourdomain.com/path?queryB will be stored as separate objects in the Azion cache.

Furthermore, to increase cache’s efficiency, you may enable the Query String Sort functionality. With the Query String Sort functionality enabled, all fields in the query string will be sorted, making the position of the fields irrelevant in the definition of the cache key. If the field positions are relevant to differentiate your content, you must leave the feature disabled.

**Cache by Cookie**

You can also distinguish objects in the Azion cache by name/value of cookies.


* **Content does not vary by Cookies (Improves Caching):** defines that cookies will not be taken into account to differentiate objects in the Azion cache. Only the URL will be considered for differentiating the objects.
* **Content varies by some Cookies (Whitelist):** you can list the name of the cookies that your application uses to differentiate cached objects. All other cookies will be ignored. As a result, you can segment your content by user profiles and more. This is the most recommended option if you use cookies to manage user sessions.
* **Content varies by Cookies, with the exception of a few (Blacklist):** you can list the name of the cookies you want to ignore in the definition of the cache key and, thus, all cookies will be considered, except for those listed.
* **Content varies by all Cookies:** Content varies by all Cookies: defines that in addition to the URL, all cookies must be considered to differentiate objects in the Azion cache.

Use this functionality to segment your content by user profile, browsing session, access region or according to your content targeting needs.

---

## 2. Bypass Cache {#BypassCache}

You can also use Azion to deliver your dynamic and personalized content, even when some of your content cannot be cached on Azion's infrastructure. In Azion you define cache rules per path. Create a Bypass Cache rule for the paths of your website that cannot be cached in our infrastructure.

To use the functionality, follow these steps:


1. Acess [Real-Time Manager](https://manager.azion.com/) and click the menu **Edge Services** and select **Edge Applications**.
2. Add or edit one **Edge Application**.
3. In the **Rules Engine** tab, add or edit a rule in **Request Phase** to define the behavior for one or more paths.
4. Select the **Bypass Cache** behavior.


When using Bypass Cache, you will be configuring the Azion service to forward all requests to a path directly to their origin. Still, you will have important protocol optimizations to speed up your application and a keepalive connection between Azion Edge Nodes and their origin, whenever possible.

**Diferença entre Bypass Cache e TTL 0 (zero)**

There is a difference in behavior between Bypass Cache and cache with TTL (time-to-live) set to 0 (zero) seconds. Using Bypass Cache, all http and https requests received by Azion's Edge Nodes will be sent to their origin, without any content caching. Use Bypass Cache if you want to deliver distinct content for each user request.

However, for TTL set to 0 (zero) seconds, multiple requests in parallel to Azion's Edge Nodes will be sent as a single request to their origin, by Azion's Edge. Use TTL zero if the content can be delivered identically to all users who order simultaneously, but the content varies from time to time. In addition, when using TTL sero, Azion Edge Nodes will validate changes to the content with its origin using If-Modified-Since and, if the object has not changed since the last request, the content will not need to be transferred again, and it could result in a much faster 304 Not Modified response.

This difference is important for you to be able to obtain maximum optimization in the delivery of your content and load reduction at its origin.

---

## 3. Forward Cookies {#ForwardCookies}

If your origin manages application cookies, you may need the Forward Cookies functionality.

By default, Azion filters the Response Header Set-Cookie sent by its origin. If you wish, you can configure Azion so that the Set-Cookie is passed on to your users.

To use the functionality, follow these steps:

1. Acess [Real-Time Manager](https://manager.azion.com/) and click the menu **Edge Services** and select **Edge Applications**.
2. Add or edit one **Edge Application**.
3. In the **Rules Engine** tab, add or edit a rule in **Request Phase** to define the behavior for one or more paths.
4. Select the **Forward Cookies** behavior.

> By using the Forward Cookies functionality, you are determining that Azion forwards to the users the Set-Cookie header received from its origin, even in a cache content situation (cache hit). To prevent a user from receiving another user's Set-Cookie session, you must list all session cookies (private cookies) for your application in the Cache Settings tab of your Edge Application configuration, in the Advanced Cache Key section, in Cache by Cookie.

**JavaScript Cookies**

An alternative to sending the Response Header Set-Cookie is to create cookies using JavaScript. JavaScript allows you to create, read and expire cookies through the document.cookie property.

To create a JavaScript cookie, you must enter name = value and, optionally, expires and path:

~~~
document.cookie = “username=John Doe; expires=Thu, 18 Dec 2020 12:00:00 UTC; path=/”;
~~~

You will find more information about JavaScript Cookies by clicking [here](https://www.w3schools.com/js/js_cookies.asp).

By default, Azion will not filter the Request Header Cookie regardless of its Forward Cookies configuration and therefore JavaScript Cookies may be sent to the origin to enable the management of your application.

---

## 4. Support for POST/PUT and other methods {#SuportePOSTPUT}

You can use Azion to accelerate your web applications and APIs. Through the Application Acceleration you extend the Edge Application functionalities to support the POST, PUT, PATCH, DELETE methods, in addition to those already natively supported GET, HEAD and OPTIONS.

To use the functionality, follow these steps:


1. Acess [Real-Time Manager](https://manager.azion.com/) and click the menu **Edge Services** and select **Edge Applications**.
2. Add or edit one **Edge Application**.
3. In the **Main Settings** tab, activate the **Application Acceleration** module.

---

Didn't find what you were looking for? [Open a support ticket.](https://tickets.azion.com/)

[Edit this page](https://github.com/aziontech/docs_en/edit/master/application-acceleration/index.md) on GitHub.
