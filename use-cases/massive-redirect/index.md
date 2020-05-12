# Massive Redirect with **Azion Edge Functions**
[Edit on GitHub <svg width="14" height="14" xmlns="http://www.w3.org/2000/svg"><g fill="none" stroke="#F3652B"><path d="M4.81.71H.672v11.43H12.1V8.001" stroke-width=".8"/><path d="M6.87.786h5.155V5.94M6.31 6.5L12.026.786"/></g></svg>](https://github.com/aziontech/docs_en/edit/master/use-cases/massive-redirect/index.md)

## Migrate applications and domains without affecting a page's rank and user experience

The digital marketing and technology teams work intensively in the construction of pages and SEO strategies so that their ranking in search engines is the best possible, thereby organically leading more users to them. In this scenario, when for some reason it is necessary to change the domain, application or navigation structure of the website, it is essential to build a strategy for redirecting old pages so as not to lose ranking in search engines, such as Google, as this puts the experience of an important part of the audience of the website at risk.

When the need arises to make one of these changes, one of the major concerns of marketing teams is how to maintain ranking and authority in the new address or navigation structure. It is likely that the main domain, all subdomains and pages that belong to this structure will have their scores on search engines impacted.

The solution is to configure a permanent "redirect" response from the previous address to the new one, the so-called HTTP 301 code (moved permanently). With this, the authority of the old address is transferred to the new one, maintaining the ranking on the search engines.

There are several techniques for implementing a 301 redirect, for example, by inserting a script directly into the page's source code. However, depending on the number of pages, this technique can become very costly and, above all, impair the performance and experience of users, which is also penalized by the algorithms of the search engines. An alternative is to create a file directly on the application's Web Server, which will process redirects by means of rules, eliminating the need for individual entry within the website pages.

However, it is common for a website to have hundreds of pages, and therefore the complexity of configuring the rules increases in proportion to the number of necessary redirects, making this an important and difficult to maintain job. Companies that use - or intend to use - any CMS or e-commerce platform to manage their pages, such as Wordpress, Joomla, Magento, SAP Hybris and VTEX, will face enormous challenges when it comes to changing domains, implementing improvements in the structure of the page or change tools or platform: such as structure of pages to be rebuilt, hundreds of pages that point to old links that will cease to exist, and the complexity in maintaining old pages and links.

In general, the concept is simple. However, the strategy adopted to deal with Massive Redirects will define the complexity in the implementation and maintenance, and mainly the effectiveness of ranking and user experience. After all, nothing is more frustrating than a user finding your page through a search engine, and when accessing it they receive a page not found error or slowness in opening the page.

## Azion Edge Functions: serverless functions for massive redirect of pages.

With Azion's Edge Function Massive Redirect you can quickly and simply configure all your redirects, in one place, no matter how many pages there are.

Massive Redirect is a serverless function that is executed directly at the edge of the network, closer to users, which guarantees a series of advantages for your business.

Here are some cases where Azion Massive Redirect will be the ideal solution:

* Migration of CMS, e-commerce, LMS and other platforms;
* URL update (e.g. the address has changed or the URLs need to be transformed into friendly URLs);
* Website update (e.g. the website structure has been remodeled, with a change in the structure of directories, subdomains or pages);
* Redirect a page that no longer exists (e.g. obsolete pages, such as expired promotions or discontinued content);
* Avoid duplication of content (e.g. preventing search engines from considering the old and new addresses as being different, thereby dividing the scoring and ranking).

## Understanding how Massive Redirect works at Azion

Before you start, make sure that the Edge Functions service is active in your Azion account and that you already have the Massive Redirect function in your Edge Functions Libraries. If not, contact our sales team to enable the service.

For the operation of the Edge Function Massive Redirect, we inform through parameters (**Edge Function Json args**) a list with the addresses to be redirected and the respective destination. When a request reaches the Azion edge node, our service will interpret the instruction defined by the function, checking if the address accessed corresponds to those received in *Json args* (parameters), and will execute the redirect to the corresponding destination. From that moment, the request will be directed to the new address, transparently to your application and to the servers of its origin.

To use the Function Massive Redirect, edit the **Edge Application** to which you want to assign this service, ensuring that the Edge Function is enabled in the Main Settings tab. Then select the Functions tab and click the **Add Function** button. Enter a name for your custom function (use a meaningful name, for example MyStoreRedirect, as this is how your Function will be identified later in the Rule Engine configuration) and select the **Edge Function** you want to use from the list of options, in this case , the **Massive Redirect** option. Note that the function code will appear below, in the **Code**, section, for reading and understanding only. 

In the **Json args**, section, enter the parameters (old and new addresses) that will be passed on to the function. The old address can be informed in two ways:

* _**from**_: use the full address to be redirected (old location);
* _**from_regex**_: use a regular expression to represent a URL building pattern, allowing you to configure more than one address with a single rule.

For the new address, we also have two options:

* **moved**: destination location (URI) for a permanent redirect (HTTP status 301);
* **found**: destination location (URI) for a temporary redirect (HTTP status 302).

It is possible to configure one or more redirects in the same Edge Function. Here are some examples of how this configuration can be done:

~~~
[{
    "from": "https://www.old-site.com",
    "moved": "https://www.new-site.com"
}]
~~~
Permanent redirecting (301) from [www.old-site.com](#) to [www.new-site.com](#)

~~~
[{
    "from_regex": "https://(api|store|checkout)\\.old-site\\.com$",
    "moved": "https://www.new-site.com/%1$"

}]
~~~
Permanent redirection (301) using regular expression, directing the **api**, **store** and *checkout* addresses from the [old-site.com](#) domain to the [new-site.com](#) domain.

~~~
[{
    "from": "https://www.old-site.com/shoes.html",
    "moved": "https://www.new-site.com/category/shoes"
},
{
    "from": "https://www.old-site.com/shoes-snekears.html",
    "moved": "https://www.new-site.com/category/shoes/sneakers"
},
{
    "from": "https://www.old-site.com/users-login.html",
    "found": "https://www.new-site.com/login.html"
},
{
    "from": "https://www.old-site.com/clothes-dresses-new-year-eve.html",
    "found": "https://www.new-site.com/category/clothes/dress/new_year_eve"
}]
~~~
Several redirects configured in the same Function.

Once created, simply associate your Function with a Rule Engine within your Edge Application. In the **Rules Engine**,  tab, use the Default Rule or create a new rule with a validation criterion (**criteria**) to activate your function, and in the **Behavior**, section, select Run Function and choose the Massive Redirect Function that you created.


Please contact our Support if you have any questions.

---

Didn’t find what you were looking for? [Open a support ticket.](https://tickets.azion.com/)
