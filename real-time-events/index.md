# Real-Time **Events**

[Edit on GitHub <svg width="14" height="14" xmlns="http://www.w3.org/2000/svg"><g fill="none" stroke="#F3652B"><path d="M4.81.71H.672v11.43H12.1V8.001" stroke-width=".8"/><path d="M6.87.786h5.155V5.94M6.31 6.5L12.026.786"/></g></svg>](https://github.com/aziontech/docs_en/edit/master/real-time-events/index.md)

Real-Time Events is an Edge Orchestration module that allows you to view data on your Azion products and services in real time.
You can use Real-Time Events to perform complex searches and explore your application data on Azion, which are organized in Data Origins.

> 1. [Data Origins](#DataSources)
> 2. [Time Filter](#TimeFilter)
> 3. [Search](#Search)
> 4. [Refresh](#Refresh)

---

## 1. Data Origins {#DataSources}

The first step for you to explore your data is choosing the Data Origin, which represents the Azion product or service that generated the events.

When submitting a search, the Data Origin represents the index from where you want to collect data.

Azion makes available the following Data Origins:

*   **Edge Applications:** presents the data of requests made to your Edge Applications at Azion.
*   **WAF Events:** if you have contracted the [Web Application Firewall](https://www.azion.com/pt-br/docs/produtos/web-application-firewall/) product, the WAF Events data origin will present the requests analyzed by WAF to allow you to map the score assigned to the request, the WAF rules that matched, the reason for the block and more.
*   **Edge Pulse:** if you are using Edge Pulse on your pages, this data origin will present their performance data, measured from the user's browser (RUM).
*   **Data Streaming:** if you have contracted the [Data Streaming](https://www.azion.com/pt-br/docs/produtos/data-streaming/) product, this data origin will present the event records of sending the data to your endpoints.

---

## 2. Time Filter {#TimeFilter}

Real-Time Events keeps the events from the last 24 hours for you and you can choose to filter only the most recent events. The Time Filter restricts the event search result, and is selected by default for Last 15 minutes, but you can change the scope of the search by selecting:

* Last 15 minutes
* Last 30 minutes
* Last 1 hour
* Last 3 hours
* Last 6 hours
* Last 12 hours
* Last day
* Last 2 days
* Last 3 days

---

## 3. Search {#Search}

In the Search field, you can optionally filter your search results by a keyword or phrase.

When submitting a search with the Search field blank, you will get all existing records in the Data Origin, for the selected time filter.

Records are indexed as key: value. If you use only one keyword, such as www, you will filter all records that have that keyword as the value of any field.

You can also restrict the search to a particular field, using the notation: *key:value*, such as *status:200*. In this case, you will filter only the records which have a value specified for this key.

You may search for more complex field compositions. Use the notations AND and OR, in the search field to combine the fields, such as `status:200 AND scheme:https`.

---

## 4. Refresh {#Refresh}

The search always returns the results ordered by the time of the event, from the most recent to the oldest.

You can use the Refresh button to update the returned data, repeating the last search performed.

---

Didn't find what you were looking for? [Open a support ticket.](https://tickets.azion.com/)
