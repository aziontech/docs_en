# Rules Engine for **Edge Firewall**

The Rules Engine is designed for you to be able to implement your security logic at the edge. Based on programmable criteria, you choose what you want to do: block, ignore the request, limit the access rate, apply a WAF policy, perform an edge function with your own security code or simply monitor traffic to identify threats.

> 1. [How does it work?](#como-funciona)
> 2. [Rules](#regras)
> 3. [Hands-on. Step by step to configure Azion Edge Firewall](#hands-on-passo-a-passo-para-configurar-o-azion-edge-firewall)
> 4. [Hands-on. Creating a configuration with the Web Application Firewall Module using Criteria and Behavior](#hands-on-waf-criteria-behavior)
> 5. [Hands-on. Creating a Web Application Firewall configuration using the WAF Rule Set for your application](#hands-on-waf-rule-sets)

---

## 1. How does it work? {#como-funciona}

Each request from your users to your application is processed first by Edge Firewall.

You can define a set of security rules in Edge Firewall. The rules are composed by criteria which represent the conditions for the execution of the rules, and by behaviors which represent the actions that need to be executed.

The processing of the rules is sequential and you can use as criteria a powerful set of variables and comparison operators. If the conditions are met, the behaviors of each rule are executed until all the rules are processed or a rule with a finalizing behavior is found in the path (*Deny ou Drop*).

---

## 2. Rules {#regras}

Rules are always composed of conditions and behavior.

### Criteria

Determines the set of conditions that need to be met for the execution of Behaviors.

**Variables**

| Criteria | Description | Requirements | 
|----------|-------------|--------------|
| Header Accept | Header that tells you what types of media the customer accepts for the response. | Web Application Firewall |
| Header Accept-Encoding | Header that tells you what types of content encoding, usually compression algorithms, that the client accepts for the response. | Web Application Firewall |
| Header Accept-Language | Header that informs the expected language. | Web Application Firewall |
| Header Cookie | Header containing the cookies sent by the client in the request to the server. | Web Application Firewall |
| Header Origin | Header that informs the origin of a cross-site access request or a preflight request. The source is a URI indicating the name of the server, with no path information. | Web Application Firewall |
| Header Referrer | Header indicating the address of the document, or element in a document, from which the request's URI was obtained. | Web Application Firewall |
| Header User Agent | Header with a characteristic string that allows servers to identify the application, operating system, vendor and/or version of the device. | Web Application Firewall |
| Hostname | In order of precedence: the *hostname* of the request line, or the value of the *Host* header field of the request, or the name of the server serving the request. | - |
| Network | The IP address of the client making the HTTP request, which can be used for any network comparison (CIDR, ASN or Country). | Network Layer Protection |
| Request Args | All arguments sent by the user in the request string (*query string*). | Web Application Firewall |
| Request Method | The HTTP method of the request. For example: GET, POST, PUT, etc. | - |
| Request URI | URI of the request. | - |
| *Scheme* | The scheme of the request: http or https. | - |

**Operadores de Comparação**

A condição para execução de uma regra deve ser a comparação de uma variável com um argumento. Os operadores de comparação são:

| Operator | Description | Argument |
|----------|-------------|----------|
| is equal | The value of the variable is equal to the argument, compared character by character. | string |
| is not equal | The value of the variable is not exactly the same as the argument. | string |
| starts with | The value of the variable starts with the argument. | string |
| does not start with | The value of the variable does not start with the argument. | string |
| matches | The value of the variable matches the regular expression or list entered as an argument. | regular expression<br><br>list |
| does not match | The value of the variable does not match the regular expression entered as an argument. | regular expression<br><br>list |
| exists | The variable has a defined value. For example, Request Args exists if an argument is sent in the request's query string. | - |
| does not exist | The variable does not have a defined value. For example, Request Args does not exist if an argument is sent in the request's query string. | - |

**Logic Operators**

Multiple conditions can be defined using the logical operators "and" and "or”. The operator “and” has implicit precedence over the operator “or”.

If explicit precedence is required, you can add multiple criteria groups under the and logic.

### Behaviors

In Behavior you add the behaviors you want to perform, if the rule's conditions are met.

| Behavior | Description | Requirements |
|----------|-------------|--------------|
| Deny (403 Forbidden) | Closes the request with HTTP *403 Forbidden response.* | - |
| Drop (Close Without Response) | Closes the request without responding to the customer. | - | 
| Set Rate Limit | Defines an access rate limit that, if exceeded, will result in an HTTP *429 To Many Requests* response. To configure the *Rate Limit*, you must inform: Average Rate Limit (req/s), which is the limit rate itself; Client IP address, if you want the access rate to be counted by the client's IP address or Global, if you want total access rate counted; Maximum burst size, which indicates the maximum burst size of HTTP requests sent simultaneously, which will be queued and dispatched gradually, respecting the limit rate. The configured value will be the Rate Limit for each Azion Edge Node, implemented using the Leaky Bucket algorithm. We recommend that you use *Maximum burst size* at a maximum of 10 times of the value configured in *Average Rate Limit*, which would result in penalizing the last request for a burst with up to a 10 second delay. | - | 
| Set WAF Rule Set | Associates the WAF Rule Set to be used in the request. WAF policies must be previously configured in the Edge Services> WAF menu. | Web Application Firewall | 
| Run Function | Executes a function specified as a parameter. The function must have been previously instantiated and parameterized in the Functions tab, in order to be used. | Edge Functions |  


## 3. Hands-on.  Step by step to configure Azion Edge Firewall {#hands-on-passo-a-passo-para-configurar-o-azion-edge-firewall}

### Step 1: Creating a new Rule Set on Edge Firewall

1. Acess [Real-Time Manager](https://manager.azion.com/login/?next=/) and enter the Edge Services> Edge Firewall menu. You will see the main interface where you can create and manage your Edge Firewall rule sets.
2. Click on the Add Rule Set button.
3. Fill in the fields that will appear, as follows: 
    Add Edge Firewall
    Atribua um nome sugestivo para seu Edge Application.
    Domain Settings
    In this section, select the domains to which you want these settings to be applied.
    Edge Firewall Modules
    Enable the modules you deem necessary to be able to have access to the specific functionalities of each one. The available modules are:
      - Network Layer Protection
      - Web Application Firewall
      - Edge Functions
4. Select the field *Active* to activate the rule set.
5. Click on *Save* to save.

### Step 2: Creating security rules through the Rules Engine

1. Select the tab Rules Engine.
2. Click on New Rule to add a new rule.
3. Fill in the fields that will appear, as shown below:
    Rule Name
    Assign a descriptive name for your rule.    
    Criteria
    Parameterize your rule with the criteria that will define the conditions for the execution of the behaviors.
    - If: Conditional command. Select the variable, the comparison operator and the value to be compared.
    Ex: *IF Request URI starts with /product*. This condition will test every request in which the URI starts with */product*. 
    You can combine more than one condition within the same rule, just add rules through the logical operators *And and Or*.
4. Behavior
Defines the action to be taken if the requisition matches the defined criteria. Select the attribute, and, if necessary, select the condition and add the reference value. Some Actions do not require a complement, just select them so that their behavior is defined, for example, in the action Deny (403 Forbidden), which will return an HTTP *Status Code 403* indicating that the server understood the request, but refuses to authorize it.
  - Then: Choose one of the available actions. The set of behaviors depends on the enabled Edge Firewall modules. Some options require the completion of complementary fields. 
Ex: *Then Set Rate Limit, Average Rate Limit (req/s) 2, Client IP Address, Maximum burst size 10*. In this example, for the Set Rate Limit action, the additional fields Average Rate Limit (req/s) and Maximum Burst Size will appear, in addition to the restriction selection option by IP or Global address, that is, if the request meets the criteria of the Rule, then a rate limit of 2 requests per second, per IP address will be set, with a burst limit of 10 requests.
5.  Select the field *Active* to activate the rule set.
6.  Click *Save* to save the Edge Firewall Rule Set.

--- 

## 4. Hands-on. Creating a configuration with the Web Application Firewall Module using Criteria and Behavior {#hands-on-waf-criteria-behavior}

Create a configuration with Web Application Firewall business rules through the Rules Engine. Example: Rate Limit of 2 requests per second with a burst of 10 for user-agent Googlebot.

1. Select the tab Rules Engine;
2. Click on New Rule to add a new rule.
3. Fill the field which will appear, as shown below:

Rule Name (Name of your rule)

Give your Rule Engine a descriptive name. e.g.: Rate Limiting Googlebot

Criteria

Parameterize your Rule Engine with the criteria that will define how your rule works.

- IF: Conditional command. Select the attribute, select the condition and add a value to be tested.
e.g.: *IF Request User-Agent Matches Googlebot*. This condition will test every request where the user-agent header contains *"Googlebot"*
e.g.: *Header User Agent* Matches *Googlebot* And Network Matches Azion Tor Exit Nodes - In this case the rule will only fit into requests with a header containing "Googlebot" and originated in the Tor Network..

Behavior:

- Then: Choose Set Rate Limit
e.g.: *Then Set Rate Limit, Average Rate Limit (req/s) 2, Client IP Address, Maximum burst size 10*. In this example, for the Set Rate Limit action, the additional fields Average Rate Limit (req/s) and Maximum Burst Size will appear, in addition to the restriction selection option by IP or Global address, that is, if the request meets the criteria of the Rule, then a rate limit of 2 requests per second, per IP address will be set, with a burst limit of 10 requests.
4. Select the field *Active* to activate the rule set.
5. Click *Save* to save the Edge Firewall Rule Set

--- 

## 5. Hands-on. Creating a Web Application Firewall configuration using the WAF Rule Set for your application {#hands-on-waf-rule-sets}

*Rule set* s the WAF rule set that enables protection against the most varied types of attacks. It defines the protections you want to activate, the detection sensitivity level and the *whitelist*.

Creating a WAF configuration within your Edge Firewall is very simple, it consists of the following steps:
1. Access the [Real-Time Manager](https://manager.azion.com/), access the menu Edge Services > WAF. You will see the main interface where you can create and manage your Web Application Firewall;
2. To add a new WAG configuration, click the Add button;
3. Fill in the fields that will appear, as shown below: 
Name (Name of your WAF)
Assign a descriptive name to your WAF. To create a *rule set*: 
Mode (WAF operation mode)
  - Counting: Analyzes all requests and identifies those with malicious behavior, however it does not block, it only counts. We recommend using this option only in the learning (calibration) stage of your WAF.
  - Blocking: Analyzes all requests and blocks those with malicious behavior.
4. Threat Type (families of threats) 
A list of the families or types of threats addressed by the *WAF* is presented. Select the WAF sensitivity level you want for each one under Sensitivity. Activate all types you deem necessary by selecting Status. 
Active
Check this option to activate your WAF.
5. Click SAVE to save your settings.

For your WAF to effectively take action it is necessary to associate it with a Behavior, within a Rule Engine of your Edge Firewall:

1. Access [Real-Time Manager](https://manager.azion.com/) and enter the Edge menu, and select Edge Firewall.
2. To add a *new rule set*, click the *Add Rule Set button*;
3. In the Main Settings tab, enable Web Application Firewall in the Edge Firewall Modules and select one or more domains to receive WAF protection.
4. Save your *rule set* with a descriptive name. You will need it to perform the Rule Set configuration later on in the Rules Engine tab.
5. In the *Rules Engine* tab, in the *Behavior* section, in the *Then* field, select "Set WAF Rule Set" and associate the desired WAF Rule Set. Make sure that the *Active* option is selected.
6. Use Analytics or WAF logs through Real-Time Events and Data Streaming products to track detected threats.

> Remember: WAF only blocks threats if it is configured in Blocking Mode.

---

Didn't find what you were looking for? [Open a ticket.](https://tickets.azion.com/)

[Edit this page](https://github.com/aziontech/docs_en/edit/master/edge-caching/rules-engine/index.md) on GitHub.
