# Azion Edge Caching: an evolution of CDN with **Edge Computing**

[Edit on GitHub  <svg width="14" height="14" xmlns="http://www.w3.org/2000/svg"><g fill="none" stroke="#F3652B"><path d="M4.81.71H.672v11.43H12.1V8.001" stroke-width=".8"/><path d="M6.87.786h5.155V5.94M6.31 6.5L12.026.786"/></g></svg>](https://github.com/aziontech/docs_en/edit/master/use-cases/edge-caching/index.md)

In 2019, on-line sales in Brazil alone was around BRL 61.2 billion. In 2020, the sector is predicted to grow by more than 20%. If we also add in, for example, the education and financial sectors, the figures only get bigger. More and more efficient solutions are needed to keep this huge volume of transactions going.

Traditional Content Delivery Network (CDN) services will not be enough to deal with this. What can make a big difference for organizations is to be able to process the data closer to the customer, through an Edge Computing platform, running Edge Caching. 

## More agile and better performance, less cost and Real-Time processing.

At times of peak use, such as promotions or special events (Black Friday and Christmas, for example), the high number of simultaneous requests can lead to instability or even crash applications. Service quality failures have a direct impact on the user experience, which negatively affect a site’s conversion rate.

Azion's Edge Computing platform offers dynamic solutions to support large increases in demand. It can handle thousands of simultaneous requests without any compromise to its infrastructure, ensuring that your users get the best experience. 
Our Edge Nodes software defined network (SDN), works dynamically and in real time to send the device (whether a person, mobile, IoT device, etc.) to the best placed Edge Node to service the user. All of this with a 100% SLA, while still protecting your customers' datacenter or cloud infrastructure from attack.

Edge Caching solutions can optimize and speed up your APIs processing. With server-less processing available, you can create code, business rules, clustering logic and categorize cached data in Edge to define and manage any degree of consistency time for the response, regardless of size. 
The logic behind this, is that large loads of requests for dynamic content are supported, without the need to use queue systems and without creating an overload in the call center due to the difficulty (technically or financially impossible) in horizontally scaling the back office systems.
Requests are processed and responses sent much more quickly when you put your tasks and business rules into Edge: directly by Azion, rather than the CDNs having to link back to your IT infrastructure at all times (by cache bypass for dynamic content). 

Azion’s Software monitors and ensures the connection is secure and uses the resources of your cloud or datacenter when it is not feasible to respond directly from the platform. This saves on processing resources and time, dramatically reducing your costs for software licenses, databases, infrastructure (on premises and off premises) or cloud services.

## How it works 

Before you begin, make sure that the Application Acceleration service is active on your Azion account. If not, please get in contact with our support or commercial teams to access the service.

To better explain how to configure Application Acceleration, we will use the cover page of an e-commerce site as an example. You will see that, as well as the main part, we have some special sections, whose content is delivered by APIs.

* Login: section for the user to log into the page. **Not Cached**. Source Content: _api.myeccomerce.com/login_;
* Highlights: Highlights of Daily Promotions. **Cache for 1 day**. Source Content: a_pi.myeccomerce.com/highlights_;
* Recommendations: Recommended offers, based on the user’s browsing. **Micro cache for 5 seconds**. Source Content: _api.myeccomerce.com/recommendations_.

In our example, we will set some caching and micro caching rules for dynamic content. The first step is to set the rules (Cache Settings) and the second is to set the tasks for these rules (Rules Engine).

We begin with the “**Highlights**” section of the site, and access through Real-Time Manager, the Edge Application that we want to configure. On the Main Setting tab, check that the Application Acceleration module is active. On the Cache Settings tab, click on the Add Cache Settings button. Enter a name for your Cache Setting (make sure you use an appropriate name, for example HighlightsCacheSet, as you will need to be able to identify the setting later, when you configure your rule in the Rule Engine).

The basic rules for cache expiry are set in the Expiration Settings section. In the field **Browser Cache Settings**, select **Honor Origin Cache Headers** so that the cache settings of the Source Cache will persist. In **Honor Origin Cache Headers**, select **Override Cache Settings** and enter a value of 3600 (1 day) in **Maximum TTL**. The other settings can be left as they are. Click on **Save**. This rule, therefore, sets the expiry time in Edge to 1 day.

Now, having completed the previous steps, add a new caching rule for the “**Recommendations**” section, giving it the name _RecommendationsCacheSet_. The only thing that needs to be changed is in the **CDN Cache Settings** section, where we will add the value 5 (5 seconds) to the **Maximum TTL** field. This rule, therefore, sets the expiry time of the content to 5 seconds.

To create the rule validation task, open the **Rules Engine** tab. Let’s begin by creating a rule for the **login** section in our example. Click on the **New Rule** button, **Request Phase** option. Enter a name for your new Rule (make sure you use an appropriate name, for example RuleLogin, as this is how you will be able to identify it).

In the **Criteria** section, we set the rule’s condition to validation. For the conditional “**If**”, add a value of **${uri}**, showing that we will be validating the URI of the request. Next select “**starts with**” and enter “_/login_” as the string to compare. What this is saying is that the rule will be executed whenever a URI begins with the string “_/login_”. 

Next, we define what behavior will be run when the rule is executed. In the **Behavior** section, in the field “**Then**”, select **Bypass Cache**. Click on the “_+_” button to add an action and select **Forward Cookies**. When the rule is run, it will run a bypass for this request.

Now we will create a rule for the “**Highlights**” section. Click on the **New Rule** button, **Request Phase** option. Enter the name _RuleHighlights_ for the new Rule. In the **Criteria** section, add a value of **${uri}**, showing that we will be validating the URI of the request. Next select “starts with” and enter “_/highlights_” as the string to compare. What this is saying is that the rule will be executed whenever a URI begins with the string “_/highlights_”.

In the **Behavior** section, in the field **Then**, select "Set Cache Policy" and select the cache rule we previously created, in this case **CacheHighlights**. Click on the **Save** button. When the rule is executed, the caching rule of 1 day will be applied to the content.

Finally, add a new item to the **Rule Engine**, called RuleRecommendations, using the same steps as before. In the **Criteria** section, enter “/recommendations” as the string to be compared, and in the **Behavior** section, in the field **Then**, select "Set Cache Policy" and select the cache rule we previously created, in this case “CacheRecommendations”. Click on the **Save** button. Now, when the rule is executed, the caching rule of 5 seconds will be applied to the content.

---

Didn’t find what you were looking for? [Open a support ticket.](https://tickets.azion.com/)
