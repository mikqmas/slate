---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - ruby
  - python
  - javascript

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>

includes:
  - errors
  - api_ref

search: true
---

# INTRODUCTION

Welcome to the Clover API! You can use our API to get access to merchant data like orders, payments, employees, customer, etc.

We have language bindings in Shell, Ruby, Python, and JS! Our docs are generated through Swagger, which you can use to create your own client libraries for the language of your choice.

# Sandbox vs Production
Clover provides a REST API for each of its supported markets.
United States: https://api.clover.com
Europe: https://api.eu.clover.com

For development and testing purpose, please use our sandbox environment:
https://apisandbox.dev.clover.com
 
Our documentation will always refer to sandbox environment.

# Authentication

> To authorize, use this code:

```ruby
require 'cloverpos'

api = CloverPOS::APIClient.authorize!('your_access_token')
```

```python
import cloverpos

api = cloverpos.authorize('your_access_token')
```

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "Authorization: your_access_token"
```

```javascript
const cloverpos = require('cloverpos');

let api = cloverpos.authorize('your_access_token');
```

> Make sure to replace `your_access_token` with your API key.

Clover uses API keys to allow access to the API. You can register a new Clover API key at our [developer portal](http://example.com/developers).

Clover expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: your_access_token`

<aside class="notice">
You must replace <code>your_access_token</code> with your personal API key.
</aside>

## Token Type
There are three methods of generating an access token. 
1. OAuth 2.0
  - Generally accepted method of generating token.
2. Merchant Generated Token
  - Strictly for testing only. This will be limited in endpoints that will be available. It will also lack CORS support.
3. Android SDK 
  - For Android Apps to make REST calls, `CloverAuth.authenticate(context, mAccount).token`;

## Permissions
Your app will need to request specific (Read / Write) permissions from merchants on download from App Market.

# OAuth 2.0
OAuth 2.0
While building your Clover app, you may want to access data about Clover merchants, such as their order history or current inventory. With Clover’s powerful REST APIs, your app can easily access data about merchants and their businesses.

Considering the sensitivity of merchant data, we at Clover have implemented the OAuth 2.0 security framework. When a merchant selects and installs your app from the Clover App Market, we use OAuth 2.0 to first secure the communication between your app and the merchant, and then give your app the desired access to merchant data.

In this article, we discuss:
The Clover OAuth 2.0 Flow
Step 1: Request Merchant Authorization
Step 2: Receive an Authorization Code
Step 3: Request an API Token
Step 4: Receive an API Token
Using the Response Type Token Method
The Clover OAuth 2.0 Flow
As shown in the figure below, there are 4 keys steps involved in the Clover OAuth 2.0 flow.

OAuth 2.0

To begin with, let’s define a few terms that can help us in discussing the OAuth 2.0 flow:

Client ID
This ID uniquely identifies your app on the Clover App Market. This public-facing ID confirms that your app is participating in the OAuth 2.0 flow.

Client Secret
This ID is a secret key that is assigned to your app by Clover. The client ID and client secret together authenticate the identity of your app with the Clover Server.

Merchant
Clover merchants can be either one of two states:

An unauthorized Merchant wants access to your app, but has not logged in to their Clover merchant account. Your app redirects this merchant to log in to their merchant account.

https://sandbox.dev.clover.com/oauth/authorize?client_id={App ID}
An authorized Merchant has logged in to their Clover merchant account. The Clover Server redirects this merchant to your app.

https://www.example.com/oauth_callback?merchant_id={Merchant ID}&client_id={App ID}
&code={Authorization code}
Authorization Code
An authorized merchant is redirected to your app along with an authorization code. With this code, the Clover Server confirms that your request for merchant data has been authorized by the merchant.

https://sandbox.dev.clover.com/oauth/token?client_id={App ID}&client_secret={App secret}
&code={Authorization code}
API Token
Your app uses the authorization code, client ID, and client secret to negotiate with the Clover server for an API token. With the API token, your app can make REST API calls and access merchant data.

{
"access_token":"{API token}"
}
Step 1: Request Merchant Authorization
When an unauthorized merchant selects and installs your app from the Clover App Market, redirect this merchant using the following URL format to log in to their Clover merchant account:

https://sandbox.dev.clover.com/oauth/authorize?client_id={App ID}&redirect_uri={Client redirect URL}
TIP
If an unauthorized merchant navigates directly to your app URL without installing the app from the Clover App Market:

Redirect this merchant to first log in to their Clover merchant account, and then
Request the merchant to install your app from the Clover App Market
Clover provides a wide range of parameters that you can use to customize the merchant authorization redirect URL as listed in the following table.

Table 1: Parameters in the merchant authorization redirect URL

Parameter	Description
client_id

This ID uniquely identifies your app on the Clover App Market.

NOTE
The client_id parameter value is the App ID value in your app’s Settings page on the Developer Dashboard.

client_ids(Optional)

If you are building an app for multiple Clover markets, your app receives a unique app ID for each Clover market. For such apps, set the client_ids parameter with a comma separated list of app IDs.

merchant_id(Optional)

This ID is assigned by Clover to uniquely identify a merchant account or business. App users can own multiple businesses and merchant accounts. If an app user has multiple merchant accounts, the user is requested to select the desired merchant account as part of the OAuth 2.0 flow.

If you know the merchant account that the user will select, you can simply set the merchant_id parameter with the merchant ID of that account. This enables the user to skip the account selection step.

redirect_uri(Optional)

Once the merchant has logged in to their account, you can redirect them to a custom URL with the redirect_uri parameter.

NOTE
The value of the redirect_uri parameter must be a subpath of the Site URL value in your app’s Settings > Web Configuration page.

response_type(Optional)

By default, the Clover Server responds to merchant authorization requests by redirecting the merchant to your app along with an authorization code. For your app on the Clover App Market, receiving the authorization code is an important step in the OAuth 2.0 flow.

You can also build and publish client-based JavaScript and mobile apps on the Clover App Market. For such apps, if you set the value of the response_type parameter as token in the redirect URL, the Clover Server follows the Response Type Token method and directly sends you an API token along with redirecting the merchant to your app.

WARNING
When you use the Response Type Token method, the API token from the Clover Server is publicly accessible. We highly recommend that you use this method only for merchant-facing apps.

state(Optional)

To ensure that merchants are logging in to a legitimate redirect URL from your app, you can set the state parameter with any string value. In this case, if the Clover Server response also includes the same state parameter value, this ensures that:

An legitimate request has been made by your app, and then
The Clover Server has redirected the merchant to your app in response to the legitimate request
Step 2: Receive an Authorization Code
Once a merchant is authorized, the Clover Server redirects this merchant to your app using the Site URL value in your app’s Settings > Web Configuration page.

NOTE
If you have set the redirect_uri parameter to a custom location as part of the merchant authorization redirect URL, the server then redirects the merchant to the specified location.

The Clover Server redirects the merchant to your app along with a set of parameters in the following URL format, which includes an authorization code:

https://www.example.com/oauth_callback?merchant_id={Merchant ID}&client_id={App ID}
&employee_id={Employee ID}&code={Authorization code}
With the authorization code, the Clover Server confirms that your request for merchant data has been authorized by the merchant. You can use this code to further negotiate with the Clover Server for an API token.

TIP
Every time a merchant is redirected to your app, you can confirm whether the merchant has logged in to their Clover merchant account by checking for an authorization code in the redirect URL.

The following table lists the parameters in the merchant redirect URL from the Clover Server to your app.

Table 2: TParameters in the merchant redirect URL from the Clover Server

Parameter	Description
merchant_id

This ID uniquely identifies the Clover merchant account that has been authorized to use your app.

client_id

This ID uniquely identifies your app on the Clover App Market. This parameter confirms that your app is participating in the OAuth 2.0 flow and that the code parameter value is for the specified client_id parameter value.

code

With this authorization code, the Clover Server confirms that your request for merchant data has been authorized by the merchant. You can use this code to further negotiate with the Clover Server for an API token.

employee_id(Optional)

This ID uniquely identifies the employee from the merchant roster that has logged in to their account. You can create custom rules in your app based on the employee.

NOTE
If a Clover customer support agent accesses your app on behalf of the merchant, the employee_id parameter is not part of the redirect URL.

Step 3: Request an API Token
At this stage of the OAuth 2.0 flow, you exchange your authorization code for an API token from the Clover Server. Send an API token request to the Clover Server in the following URL format:

https://sandbox.dev.clover.com/oauth/token?client_id={App ID}&client_secret={App secret}
&code={Authorization code}
NOTE
Since the API token request consists of sensitive information about your app, this request does not have CORS support in the production environment. To successfully request an API token, send this request from your app server to the Clover Server. When the Clover Server responds to the request, retrieve the API token from your app server.

You must set all the parameters as listed in the following table.

Table 3: Parameters in the API token request URL

Parameter	Description
client_id

This ID uniquely identifies your app on the Clover App Market.

client_secret

This ID is a secret key that is assigned to your app by Clover. The client ID and client secret together authenticate the identity of your app with the Clover Server when you are requesting for an API token.

NOTE
The client_secret parameter value is the same as the App Secret value in your app’s Settings page. Do not share this key publicly.

code

With this authorization code, the Clover Server confirms that your request for merchant data has been authorized by the merchant. You can use this code to further negotiate with the Clover Server for an API token.

Step 4: Receive an API Token
In the final step, the Clover Server responds your API token request with a JSON object in the following format:

{
"access_token":"{API token}"
}
Using the Response Type Token Method
All your apps on the Clover App Market undergo the 4-step OAuth 2.0 flow to retrieve an API token from the Clover Server. You can also build and publish client-based JavaScript and mobile apps on the Clover App Market. For these client-based apps, Clover provides you with the Response Type Token method to retrieve an API token as soon as the merchant is authorized.

To use the Response Type Token method:

In your app’s Settings > Web Configuration page, set the Default OAuth Response value to Token.
In the merchant authorization redirect URL (Step 1 of the OAuth 2.0 flow), set the value of the response_type parameter as token.
The Clover Server directly sends you an API token along with redirecting the authorized merchant to your app using the following URL format:

http://example.com/javascript_app?&merchant_id={Merchant ID}&client_id={App ID}
&employee_id={Employee ID}#access_token={API token}
WARNING
When you use the Response Type Token method, the API token from the Clover Server is publicly accessible. We highly recommend that you use this method only for merchant-facing apps.

# Using API Token
Requests to the REST API require a merchant ID and an API token. The merchant ID is embedded in the URL that’s used to access the Clover merchant website:

https://sandbox.dev.clover.com/home/m/[Merchant ID]
 

To retrieve the API token, you must use OAuth in the production environment.

NOTE
Since the API token request consists of sensitive information about your app, this request does not have CORS support in the production environment. To successfully request an API token, send this request from your app server to the Clover Server. When the Clover Server responds to the request, retrieve the API token from your app server.

Once you have retrieved your API token, you can test Clover’s REST APIs in your app client command line. For testing purposes, we at Clover provide CORS support for such client-side requests. In your request, set the value of the access_token query parameter as your API token.

```shell
$ curl -s https://apisandbox.dev.clover.com/v3/merchants/[Merchant ID]/items?access_token={Your API token} | python -mjson.tool
```

When you are making server-side requests to Clover’s REST APIs, use set the value of the Authorization header as Bearer {Your API token}. As a test sample, the following cURL command shows the use of the Authorization header.

```shell
$ curl -s https://apisandbox.dev.clover.com/v3/merchants/[Merchant ID]/orders --header "Authorization:Bearer {Your API token}" | python -mjson.tool
```

## Rate Limit
We maintain two rate limits on apps to ensure quality of service for both merchants and developers.
We maintain a rate limit of 16 requests per second for each token.
Apps also have a cross-token total rate limit of 50 requests per second.

# Manipulating API Requests 

## Expanding Objects
Fields can be expanded with the expand query parameter. You can see what parameters are expandable for a given method in the API Reference.

```shell
$ curl -s "https://apisandbox.dev.clover.com/v3/merchants/[Merchant ID]/items/[Item ID]?expand=categories" --header "Authorization: Bearer {Your API token}" | python -mjson.tool

{
    "id": "Z0EPYQ2R5TQ5Y",
    "hidden": false,
    "name": "Bangers and Mash",
    "alternateName": "",
    "code": "024463061095",
    "price": 150,
    "priceType": "FIXED",
    "defaultTaxRates": true,
    "unitName": "",
    "isRevenue": true,
    "categories": {
        "elements": [
            {
                "id": "MHH9XR2YXZ4T4",
                "name": "Food",
                "sortOrder": "0"
            }
        ]
    }
}
```

You can expand multiple fields by separating them with commas.

IMPORTANT
Please limit expansions to a maximum of three fields per API call. This will allow us to continually provide quick API response times and reduce undue load.

```shell
$ curl -s "https://apisandbox.dev.clover.com/v3/merchants/[Merchant ID]/items/[Item ID]?expand=tags%2Ccategories" --header "Authorization: Bearer {Your API token}" | python -mjson.tool

{
    "cost": 0,
    "defaultTaxRates": true,
    "hidden": false,
    "id": "AK5ESN5YR8YWY",
    "isRevenue": true,
    "modifiedTime": 1432671908000,
    "name": "Pizza",
    "price": 1499,
    "priceType": "FIXED",
    "tags": {
        "elements": [
            {
                "id": "HYQ5Z74KS9E6W",
                "name": "Hot"
            }
        ]
    },
    "categories": {
        "elements": [
            {
                "id": "1JZPWY014VPEP",
                "name": "Italian",
                "sortOrder": 1
            },
            {
                "id": "0AJNZP04JXB4G",
                "name": "From the Oven",
                "sortOrder": 0
            }
        ]
    }
}
```
 

Two levels of fields can be expanded by specifying a dotted field path:

```shell
$ curl -s "https://apisandbox.dev.clover.com/v3/merchants/[Merchant ID]/orders/[Order ID]?expand=lineItems.taxRates" --header "Authorization: Bearer {Your API token}" | python -mjson.tool

...
{
    "clientCreatedTime": "1389389735000",
    "createdTime": "1389389736000",
    "employee": "id",
    "groupLineItems": "true",
    "id": "QGSS9P64219CM",
    "lineItems": {
        "elements": [
            {
                "createdTime": "1389389734000",
                "id": "VGQRH14DBR7JC",
                "name": "Bangers and Mash",
                "price": "1000",
                "printed": "true",
                "taxRates": {
                    "elements": [
                        {
                            "id": "VSA19B84VG1GT",
                            "isDefault": "true",
                            "name": "VAT",
                            "rate": "1500000"
                        },
                        {
                            "id": "BTHZCAXV6Z5R8",
                            "isDefault": "true",
                            "name": "Zero Tax",
                            "rate": "0"
                        }
                    ]
                }
            }
        ]
    },
    "manualTransaction": "false",
    "payType": "FULL",
    "state": "locked",
    "taxRemoved": "false",
    "total": "1000"
}
...
```
## Sorting

Most JSON responses take the form of collections, which can be sorted by specifying the orderBy query parameter. You can specify multiple fields by separating them with commas.

```shell 
$ curl -s https://apisandbox.dev.clover.com/v3/merchants/[Merchant ID]/items?orderBy=modifiedTime,price --header "Authorization: Bearer {Your API token}" | python -mjson.tool
{
    "elements": [
        {
            "code": "",
            "defaultTaxRates": false,
            "hidden": false,
            "id": "V33H8XGTZCKNP",
            "isRevenue": true,
            "name": "Item Use",
            "price": 100,
            "priceType": "PER_UNIT",
            "unitName": "hr"
        },
        {
            "code": "",
            "defaultTaxRates": false,
            "hidden": false,
            "id": "EWKZEMNCBQQ9Y",
            "isRevenue": true,
            "name": "Nontax Item",
            "price": 100,
            "priceType": "FIXED",
            "unitName": "oz"
        },
...
```

The default sort order is descending by creation time. You can manually order by ascending or descending by inputting %20ASC or %20DESC, respectively.

```shell
$ curl -s https://apisandbox.dev.clover.com/v3/merchants/[Merchant ID]/items?orderBy=modifiedTime%20ASC --header "Authorization: Bearer {Your API token}" | python -mjson.tool

{
  "elements": [ {
      "id": "1CF022RN5TGDM",
      "hidden": false,
      "name": "Pizza Slice",
      "price": 250,
      "priceType": "FIXED",
      "defaultTaxRates": true,
      "cost": 0,
      "isRevenue": true
    }, {
      "id": "SNGFTY41642NY",
      "hidden": false,
      "name": "Pork Rice Bowl with House Salad",
      "price": 1200,
      "priceType": "FIXED",
      "defaultTaxRates": true,
      "cost": 0,
      "isRevenue": true,
      "stockCount": 3
    },
...
```

## Filtering
Collections can be filtered with the filter query parameter. The filter parameter supports standard comparison operations, such as =, >=, and !=. Specify multiple filterparameters by joining &filter= statements.

```shell
$ curl -s "https://apisandbox.dev.clover.com/v3/merchants/[Merchant ID]/orders?filter=clientCreatedTime>=[unix-time]&filter=clientCreatedTime<=[unix-time]" --header "Authorization: Bearer {Your API token}" | python -mjson.tool
To determine the parameters that can be filtered for a given method, see the API Reference.
```
```shell
$ curl -s "https://apisandbox.dev.clover.com/v3/merchants/[Merchant ID]/orders?filter=total>1000&filter=payType!=FULL" --header "Authorization: Bearer {Your API token}" | python -mjson.tool

{
    "elements": [
        {
            "clientCreatedTime": 1401286267000,
            "createdTime": 1401286268000,
            "currency": "USD",
            "employee": {
                "id": "QT0DES4CXR572"
            },
            "groupLineItems": true,
            "href": "https://sandbox.dev.clover.com/v3/merchants/[Merchant ID]/orders/8WAD6KV8D90KR",
            "id": "8WAD6KV8D90KR",
            "isVat": false,
            "manualTransaction": false,
            "modifiedTime": 1401286463000,
            "payType": "SPLIT_CUSTOM",
            "state": "locked",
            "taxRemoved": false,
            "testMode": false,
            "total": 5293
        },
        {
            "clientCreatedTime": 1400106245000,
            "createdTime": 1400106245000,
            "currency": "USD",
            "employee": {
                "id": "QT0DES4CXR572"
            },
            "groupLineItems": true,
            "href": "https://sandbox.dev.clover.com/v3/merchants/[Merchant ID]/orders/0S0JJYG231462",
            "id": "0S0JJYG231462",
            "isVat": false,
            "manualTransaction": false,
            "modifiedTime": 1400106366000,
            "payType": "SPLIT_CUSTOM",
            "state": "locked",
            "taxRemoved": false,
            "testMode": false,
            "total": 2829
        }
    ],
    "href": "https://apisandbox.dev.clover.com/v3/merchants/[Merchant ID]/orders?filter=total%3E1000&filter=payType!%3DFULL&limit=100"
}
```


## Pagination/Limit
The offset and limit query parameters can be used to page through larger results. The default limit is 100 elements, and the hard limit is 1000.

```shell
$ curl -s "https://apisandbox.dev.clover.com/v3/merchants/[Merchant ID]/orders?offset=10&limit=1" --header "Authorization: Bearer {Your API token}" | python -mjson.tool
{
    "elements": [
        {
            "clientCreatedTime": 1403294602000,
            "createdTime": 1403294602000,
            "currency": "USD",
            "employee": {
                "id": "5PYBJET35969W"
            },
            "groupLineItems": true,
            "href": "https://sandbox.dev.clover.com/v3/merchants/[Merchant ID]/orders/6Z3JQ98FQ8B40",
            "id": "6Z3JQ98FQ8B40",
            "isVat": false,
            "manualTransaction": false,
            "modifiedTime": 1403295698000,
            "state": "open",
            "taxRemoved": false,
            "testMode": false,
            "total": 1743
        }
    ],
    "href": "https://apisandbox.dev.clover.com/v3/merchants/[Merchant ID]/orders?offset=10&limit=1"
}
```

## Displaying Null Field
To have a response display all possible fields, you can append return_null_fields=true to your query.

```shell
$ curl -s https://apisandbox.dev.clover.com/v3/merchants/[Merchant ID]/orders/[Order ID]?return_null_fields=true  --header "Authorization:Bearer {Your API token}" | python -mjson.tool

{
   "id": "[Order ID]",
   "currency": "USD",
   "employee": {
      "id": "0YN6A3WJ5BEZJ"
   },
   "total": 152,
   "title": "5",
   "note": null,
   "orderType": {
       "id": "2ZPZHQG2Z64NM",
       "labelKey": null,
       "label": null,
       "taxable": null,
       "isDefault": null,
       "isDeleted": null
   },
   "taxRemoved": false,
   "isVat": false,
   "state": "locked",
   "manualTransaction": true,
   "groupLineItems": true,
   "testMode": false,
   "payType": null,
   "createdTime": 1373613867000,
   "clientCreatedTime": 1373613795000,
   "modifiedTime": 1373613868000,
   "serviceCharge": null
}
```
