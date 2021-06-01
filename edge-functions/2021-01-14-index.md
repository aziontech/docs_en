# Edge **Functions**

[Edit on GitHub <svg width="14" height="14" xmlns="http://www.w3.org/2000/svg"><g fill="none" stroke="#F3652B"><path d="M4.81.71H.672v11.43H12.1V8.001" stroke-width=".8"/><path d="M6.87.786h5.155V5.94M6.31 6.5L12.026.786"/></g></svg>](https://github.com/aziontech/docs_en/edit/master/edge-functions/index.md)

Azion Edge Functions allows you to create event-driven, serverless applications, at the edge of the network - closer to users.

With Edge Functions, you can perform serverless functions in response to events on Edge Nodes of our network, with no need of having or managing servers. Azion Edge Functions automatically provides that for you. 

Explore how to use and get the most out of Edge Functions as follows.

1. [About Edge Functions](#About-Edge-Functions)
2. [How it works](#Howitworks)
3. [Basics](#basics)
4. [Step-by-step: creating an Edge Function](#stepbystepcreatinganedgefunction)
5. [Activating your settings](#activatingyoursettings)
6. [Support documentation](#Supportdocumentation)

------

## 1. About Edge Functions {#About-Edge-Functions}

Here are some of the solutions provided by Azion Edge Functions. 

You can use functions to handle HTTP in the following Request and Response phases:

- as soon as the user's requests are received in the Edge Node (Viewer Request);
- before the Azion Edge Node forwards the Request to the Origin (Origin Request);
- as soon as the Edge Node gets the response from the Origin (Origin Response);
- before the Azion Edge Node forwards the response to the user (Viewer Response).

You can also generate Responses without necessarily having to forward the request to the origin.

Using Edge Functions written in **Lua** and **JavaScript** on the Azion's Edge Computing Platform, you can create a variety of solutions, for example:

- inspect cookies to rewrite URLs to different versions of a site for A/B testing;
- send different objects to your users based on the User-Agent header, which contains information about the device that submitted the request. For example, you can send images in different resolutions to users based on their devices;
- inspect headers or authorized tokens, inserting a corresponding header and allowing access control before forwarding a request to the origin;
- add, delete, and modify headers and rewrite the URL path to direct users to different cache objects;
- generate new HTTP responses to do things like redirect unauthenticated users to login pages, or create and deliver static web pages right from the edge.

See more ways of using Edge Functions in [Use Cases](https://www.azion.com/en/documentation/use-cases/).



---

## 2. How it works {#Howitworks}

Create your custom functions or use any of the existing ones provided by Azion, both for Edge Application or Edge Firewall. 

The languages currently supported by the platform are **Lua** and **JavaScript**.

Edge Functions run during the handling of the request, and the Azion Edge Computing Platform provides a Rules Engine model that can trigger the execution of the Edge Functions code according to the handling phases. 

The language-specific Runtime provides a programming interface for interacting and manipulating Request and Response objects to implement the necessary logic.

When instantiating an Edge Function, you can enter parameters that will be passed on to the function, in [JSON](https://www.json.org/) format, through arguments. You can also define and run tests online to validate its construction.

Edge Functions are performed directly on the Azion Edges infrastructure. To use them, they just need to be associated to a Behavior in the Rules Engine. Thus, when a request meets the criteria defined in the Rule Engine rules, the Edge Function will be triggered.

Next, you'll get to know more details about the Azion Edge Functions.

---

## 3. Basics {#basics}

You can create Edge Functions and maintain a repository of functions that can be used in the Edge Application or Edge Firewall. Consult the [Runtime APIs](https://www.azion.com/en/documentation/products/edge-functions/runtime-apis/) according to the Runtime chosen for writing the Edge Function.

In addition to customizing your own functions, you can also choose from the ready-to-use ones provided by Azion or Independent Software Vendors (ISV). Browse the Azion Marketplace catalog on the Real-Time Manager.

### Create Edge Functions

Use the Runtime API of your preferred language to write Edge Functions.

**JavaScript language**

Using the JavaScript Runtime Environment, Edge Functions written by the user go directly into effect without undergoing an internal review because the code runs on limited to isolated resources.

**Lua language**

Edge Functions code written in Lua goes through a thorough a review by our software engineers before going into effect. Our goal is to ensure the security and correct use of the Edge Computing platform. We review your code according to the following criteria:

- use of any global variables that are not allowed. Due to the multi-tenant environment, the Edge Function Lua code should avoid using global variables and shared memory;
- blocking HTTP calls. Every call to an external service must use the HTTP protocol through asynchronous APIs so that the process is not blocked;
- the Code or Lib must also pass the luacheck tests.

For more details of each Runtime API and code samples, refer to the documentation for [Runtime APIs](https://www.azion.com/en/documentation/products/edge-functions/runtime-apis/).

### Edge Functions Instances

According to its initiator type, before associating an execution trigger with Edge Function, it must be instantiated in Edge Application or Edge Firewall. With the Edge Functions module enabled, you can instantiate your Edge Functions for later use in a Rules Engine Rule, through the **Functions** tab.

Learn more about Edge Functions Instances in the [Edge Application](https://www.azion.com/en/documentation/products/edge-application/edge-functions-instances/) and [Edge Firewall](https://www.azion.com/en/documentation/products/edge-firewall/edge-functions-instances/) documentation.

### Edge Functions Metrics

We provide real-time information about the performance of your Edge Functions, through Real-Time Metrics.

To access the graphs, follow these steps:

1. Enter the [Real-Time Manager](https://manager.azion.com/) and click either on *Real-time Metrics* either through the *Edge Analytics* or the *Products* menu, on the top left.  Then, click on **Edge Functions**.
2. Select the **Edge Functions** and the **period** you want to analyze. Click on the **Filter** button.
3.  You'll get the total number of invocations per instance of Edge Functions from Edge Firewall, for example.

Learn more about [Real-Time Metrics](https://www.azion.com/en/documentation/products/real-time-metrics/).

---

## 4. Step-by-step: creating an Edge Function {#stepbystepcreatinganedgefunction}

You are one step closer to creating and running serverless functions in Edge Nodes from the Azion's powerful distributed network.

To see your Edge Function in effectively operation you just need to write, instantiate and associate it with a Behavior _Run Function_, using a Rule in the Rules Engine:

1. Log into the [Real-Time Manager](https://manager.azion.com/). On the Edge Computing menu, click on **Edge Functions**.


2. Click on **Add Function** to add a new Edge Function.
3. Name your function in the **Edge Function Name** field to be able to save your settings.


3. In *Language*, select **JavaScript**. Copy the following example to the *Code* tab field.

   ~~~
   async function handleRequest(request) {
    return new Response("Hello World!",
      {
          status:200
      })
   }
   addEventListener("fetch", event => {
    event.respondWith(handleRequest(event.request))
   })
   ~~~


4. In the *Function to run* field, enter the name of the main function to run in the source code.
5. Select the *Initiator Type*, which refers to the type of module where the function will be instantiated and executed.  In this example, it refers to Edge Application.
6. Click on **Save** to save your settings. You return to the Edge Functions home page, where you see your list of Edge Functions. 
7. Then, access the **Products** menu, on the top left. Select an **Edge Application** from your list.
8. On the *Main Settings* tab, enable the **Edge Functions** module in the *Edge Application Modules* section.
9. On the *Rules Engine* tab, create or edit a Rule and in the *Behavior* section, in the *Then* field, select **Run Function** and associate it to the desired **Edge Function**. 
10. Example of response when running the Behavior *Run Function*:

~~~
Hello World!
~~~

9. Use ***Real-Time Metrics*** to check on your metrics. For example, when you want to see the number of Invocations of Edge Functions instances.

>  Fields marked with an asterisk are required. 

------

## 5. Activating your Settings{#activatingyoursettings}

You will find the following buttons at the bottom of the screen:

- **Active:** this option enables or disables your settings on the system.

- **Cancel:** With this option, you return to the  Edge Functions home page, also discard your edits.

- **Save:** Once your selections are complete, click on **Save** to save your settings.

When you save your settings, you return to the Edge Functions home page, where you see your list of Edge Functions sorted by these options: *name, language, initiator type, last editor, last modified,* *ref. count* and *active*. By clicking on the arrows on those tabs, you can also change how your list is displayed.  

---

## 6. Support Documentation {#support-documentation}

- [Edge Application - Edge Functions Instances](https://www.azion.com/en/documentation/products/edge-application/edge-functions-instances/)
- [Edge Application Rules Engine](https://www.azion.com/en/documentation/products/edge-application/rules-engine/)
- [Edge Firewall - Edge Functions Instances](https://www.azion.com/en/documentation/products/edge-firewall/edge-functions-instances/)
- [Edge Firewall Rules Engine](https://www.azion.com/en/documentation/products/edge-firewall/rules-engine/)
- [Edge Functions - JavaScript Runtime APIs](https://www.azion.com/en/documentation/products/edge-functions/runtime-apis/javascript/)

---

Didn't find what you were looking for? [Open a support ticket.](https://tickets.azion.com/)

