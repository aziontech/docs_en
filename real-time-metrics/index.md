#  Real-Time **Metrics**

[Edit on GitHub <svg width="14" height="14" xmlns="http://www.w3.org/2000/svg"><g fill="none" stroke="#F3652B"><path d="M4.81.71H.672v11.43H12.1V8.001" stroke-width=".8"/><path d="M6.87.786h5.155V5.94M6.31 6.5L12.026.786"/></g></svg>](https://github.com/aziontech/docs_en/edit/master/real-time-metrics/index.md)

Real-Time Metrics is an Edge Analytics product that provides you with real-time access to dozens of metrics so you can optimize all of your potential through our platform.

Get to know what's happening on the platform and track the behavior of your applications in real time.

> 1. [Basics](#Basics)
> 2. [Accessing Real-Time Metrics](#AccessingReal-TimeMetrics)
> 3. [Selecting your Data Interval Filter](#SelectingyourDataIntervalFilter)
> 4. [Exporting to CSV](#ExportingtoCSV)
> 5. [Interpreting your Graphs](#InterpretingyourGraphs)
> 6. [Tracking your Applications](#TrackingyourApplications)
> 
>    

---

## 1. Basics{#Basics}

The Real-Time Metrics screen is composed of the *Data Interval Filter* section and the *Data* section. 

- *Data Interval Filter* section: where you set the domain or the period that you would like to check out.  

- *Data* section: where graphs are displayed according to your filter selection. 

Real-Time Metrics enables you to apply filters to focus on a variety of data. You can select a period or domain you want to analyse or even choose where the graphs of the requested data are displayed. 



> As you hover the mouse over the graphs, you’ll get the exact values transferred over a period.



---

## 2. Accessing Real-Time Metrics {#AccessingReal-TimeMetrics}

You are about to have real-time insight at your command! Get started with Real-Time Metrics as follows:

- Enter [Real-Time Manager](https://manager.azion.com/) and click either on *Real-time Metrics* under Edge Analytics or through the top left menu. You’ll be directed to the Real-time Metrics - Edge Applications page.

  

---

## 3. Selecting your Data Interval Filter {#SelectingyourDataIntervalFilter}

As you access Real-time Metrics, you’ll see checkboxes on top of the page, with the filter options available for that product.  

All the graph options for the products in Real-Time Metrics have the Data Interval Filter. Some graphs allow you to filter by domain as follows:

1. Click on the arrows to select the domain or the period you would like to check out;
2. Click on the Filter button to apply your selections.

The graphs are updated and the information is displayed accordingly. 



> Note that the graphs presented will vary according to the products you have contracted.



---

## 4. Exporting to CSV {#ExportingtoCSV}

You can export the information as a CSV file. 

- After applying the filters, click on the CSV icon next to the graph you want to export. 

  Done. Your data at your fingertips!
  
  

---

## 5. Interpreting your Graphs {#InterpretingyourGraphs}

The information is displayed according to the product and period of time selected in the filters. Graphs will be grouped in tabs as described in the next section, *Tracking your Applications*.



---

## 6. Tracking your Applications {#TrackingyourApplications}

Information is key when taking decisions. Real-Time Metrics offers you a variety of options displayed in tabs, so you can support your actions more effectively. Check out the function of these tabs - *[Data Transferred](#DataTransferred) - [Requests](#Requests) - [Status Codes](#StatusCodes) - [HTTP Methods](#HTTPMethods) - [WAF](#WAF) - [Live Streaming](#LiveStreaming) - [Bandwidth Saving](#BandwidthSaving)* - as follows.

### Data Transferred {#DataTransferred}

This tab displays graphs referring to the amount of data transferred for the product and period you have selected. 

**Edge Caching:** This graph shows the sum - *Saved Data* + *Missed Data* - of data transferred for the product and period you have selected. At the bottom of the graph, you'll see the total amount of data - Edge Application *In* + Edge Application *Out -*  transferred for the product and period you have selected.

**L2 Caching:** You'll also get the data for *L2 Caching In* + *L2 Caching Out* displayed separately at the bottom of the graph. Your applications in greater detail.

**Edge Offload:** This graph displays the percentage of the amount of data delivered by the Azion product. It displays the *Saved Data* graph in percentages. You'll see the averages for the selected period displayed at the bottom of the graph.

**L2 Offload:** This graph displays *L2 Caching* in percentages. It refers to the amount of data delivered by the origin server. You'll get *L2 Caching* data for the selected period at the bottom of the graph.

***Saved Data:*** This graph displays the sum of data delivered by Azion servers, without looking up content on the origin server. You'll see the total amount for the selected period displayed at the bottom of the graph.

***Missed Data:*** This graph displays the sum of data delivered by the origin server. It means that the request went to the Azion servers but the content had not been transferred from the origin server to Azion. As the origin server handles the request, it sends the content to the Azion servers as well.

You'll see the total amount for the selected period displayed at the bottom of the graph.

**Bandwidth Usage**

***Total Bandwidth Usage:***  Quantity of MBps in bandwidth used. You'll see the average bandwidth used during the selected period displayed at the bottom of the graph. 

***Bandwidth Offloaded:*** Percentage of the bandwidth that was offloaded. You'll see the average bandwidth used during the selected period displayed at the bottom of the graph. 

***Saved Bandwidth:*** Quantity of MBps of bandwidth that was delivered directly through the Edge Network, without looking up content on the origin server. 

You'll see the average bandwidth used during the selected period displayed at the bottom of the graph. 

***Missed Bandwidth:*** Quantity of MBps of bandwidth used by the origin server searching for content.



---

### Requests {#Requests}

**Total Number of Requests:** Quantity of requests made for content. You'll see the total of requests during the selected period displayed at the bottom of the graph.

***Saved Requests:*** Quantity of requests delivered by the Azion servers without looking up content on the origin server. You'll see the total number of requests delivered during the selected period displayed at the bottom of the graph.

***Missed Requests:*** The amount of requests delivered by the origin server. It means that the request went to the Azion servers but the content had not been transferred from the origin server to Azion. You'll see the total number of requests delivered by the origin server during the selected period displayed at the bottom of the graph.

**Requests per Second**

***Total Requests per Second:*** The amount of requests per second, from customers for content. You'll see the average number of requests per second during the selected period displayed at the bottom of the graph.

***Requests per Second Offloaded:*** Percentage of the requests per second delivered by the Azion servers without looking up content on the origin server. You'll see the average for the selected period is at the bottom of the graph. 

***Saved Requests per Second:*** Quantity of requests per second delivered by the Azion servers without looking up content on the origin server. You'll see the average number of requests delivered during the selected period displayed at the bottom of the graph. 

***Missed Requests per Second:*** The amount of requests per second delivered by the origin server. It means that the request went to the Azion servers but the content had not been transferred from the origin server to Azion. You'll see the average number of requests per second during the selected period displayed at the bottom of the graph. 



---

### Status Codes {#StatusCodes}

This tab displays the graphs with information related to the Status Codes of the content delivered. Learn more about the HTTP Status Codes at [List of HTTP Status Codes](https://en.wikipedia.org/wiki/List_of_HTTP_status_codes).

**HTTP Status Codes 2xx:** This type of status indicates that the user request was received, understood, accepted and processed by the server.

| Code | Description                                                  |
| ---- | ------------------------------------------------------------ |
| 200  | **OK:** Standard status for a successful HTTP request. It means that the content was delivered to the user correctly. |
| 204  | **No Content:** It means that the server completed the request, but had no content to deliver. |
| 206  | **Partial Content:** The server delivered only a part of the content because it was divided into parts. |
| 2xx  | **Other Status:** There can be other types of Status for requests that have also been handled, but they are not common. |

**HTTP Status Codes 3xx**: This type of status code indicates that the user request was redirected and needs to go through another stage to be delivered.

| Code | Description                                                  |
| ---- | ------------------------------------------------------------ |
| 301  | **Moved Permanently**: This and all future requests will be redirected to another URL. |
| 302  | **Found:** This request was temporarily redirected to another URL. |
| 304  | **Not Modified:** The content header indicates that the it has not been modified and does not need to be resent. It can deliver the existing file to the user’s browser. |
| 3xx  | **Redirection:** There can be other types of Status for requests that were also redirected, but they are not common. |

**HTTP Status Codes 4xx**: This type of status code indicates that an error has occurred with the user’s request.

| Code | Description                                                  |
| ---- | ------------------------------------------------------------ |
| 400  | **Bad request:** The server cannot process the request, generally this is due to an error with the request format. |
| 403  | **Forbidden:** The request is valid, but was not authorized by the server. This means that the user or the IP that is making the request is not authorized to do so. |
| 404  | **Not Found:** The file that the request was for does not exist on the origin server. |
| 4xx  | **Client Error:** There can be other types of Status for requests that also generate errors, but they are not common. |

**HTTP Status Codes 5xx**: This type of status indicates that the server failed to deliver an apparently valid request.

| Code | Description                                                  |
| ---- | ------------------------------------------------------------ |
| 500  | **Internal Server Error:** This is the generic message given, when an unexpected error occurs on the server and it is unable to handle the request. |
| 502  | **Bad Gateway:** When the server is acting as a Gateway or Proxy and receives an invalid response from the origin. It generally occurs when the origin server is offline. |
| 503  | **Service Unavailable:** Server is not available. Generally a temporary Status. |
| 5xx  | **Server Error:** There can be other types of Status for requests that also generate errors, but they are not common. |

---

### HTTP Methods {#HTTPMethods}

This graph shows the requests for your site divided by the HTTP method used. Learn more about the HTTP Methods at [ Hypertext Transfer Protocol](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol).

| Method | Description                                                  |
| ------ | ------------------------------------------------------------ |
| GET    | This request method only receives data from the server.      |
| POST   | This request method sends data to the server.                |
| HEAD   | This request method is the same as GET, but the body of the HTML page is not sent, only the header. |
| OTHERS | Other request methods, which are not so common, are grouped together here. |

---

### WAF - Web Application Firewall {#WAF}

For clients who have the Web Application Firewall product, there is a specific graph to display the request behavior.

**Threats vs Requests:** This graph displays the average of blocked attacks for the selected period.

**Cross-Site Scripting (XSS) Threats:** This graph displays the average of Cross-Site Scripting attacks. A type of vulnerability typically found in web applications, which enables the attacker to insert itself alongside client scripts on a web page viewed by other users.

**Remote File Inclusion (RFI) Threats:** This graph displays the average of Remote File Inclusion attacks, a type of vulnerability typically found on websites. It enables the attacker to add a file on the web server.

**SQL Injection Threats:** This graph displays the average of SQL Injection attacks, a technique for inserting code used to attack data-driven applications.

**Other Threats:** This graph displays the average attacks blocked by the WAF, which are not classified under any of the above categories.

---

### Live Streaming {#LiveStreaming}

For clients who have the *Live Streaming* product, this tab displays a specific graph with the information about the number of users connected to the company’s streams.

**Average Connected Users:** Average of users connected to the selected stream. You’ll see the average users connected during the selected period displayed at the bottom of the graph.

**Max Connected Users:** Maximum number of users connected to the selected stream. You’ll see the maximum number of users connected during the selected period displayed at the bottom of the graph.

---

### Bandwidth Saving {#BandwidthSaving}

For clients who have the *Image Processor* product, there is a specific graph to display their savings when transmitting images.

The total optimization from transmitting images is displayed at the bottom of the graph.

---

Didn't find what you were looking for? [Open a support ticket.](https://tickets.azion.com/)