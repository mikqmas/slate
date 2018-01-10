# API REFERENCE
Clover provides endpoints to pull data from merchants.

# Orders

## Get All Orders


```ruby
require 'cloverpos'

api = Clover::APIClient.authorize!('your_access_token')
api.orders.get
```

```python
import cloverpos

api = cloverpos.authorize('your_access_token')
api.orders.get()
```

```shell
curl "http://example.com/api/orders"
  -H "Authorization: your_access_token"
```

```javascript
const cloverpos = require('cloverpos');

let api = cloverpos.authorize('your_access_token');
let orders = api.orders.get();
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "name": "Fluffums",
    "breed": "calico",
    "fluffiness": 6,
    "cuteness": 7
  },
  {
    "id": 2,
    "name": "Max",
    "breed": "unknown",
    "fluffiness": 5,
    "cuteness": 10
  }
]
```

This endpoint retrieves all orders.

### HTTP Request

`GET http://example.com/api/orders`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_orders | false | If set to true, the result will also include orders.
available | true | If set to false, the result will include orders that have already been adopted.

<aside class="success">
Remember — a happy order is an authentiordered order!
</aside>

## Get a Specific Order

```ruby
require 'cloverpos'

api = Clover::APIClient.authorize!('your_access_token')
api.orders.get(2)
```

```python
import cloverpos

api = cloverpos.authorize('your_access_token')
api.orders.get(2)
```

```shell
curl "http://example.com/api/orders/2"
  -H "Authorization: your_access_token"
```

```javascript
const cloverpos = require('cloverpos');

let api = cloverpos.authorize('your_access_token');
let max = api.orders.get(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Max",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a specific order.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://example.com/orders/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the order to retrieve

## Delete a Specific Order

```ruby
require 'cloverpos'

api = CloverPOS::APIClient.authorize!('your_access_token')
api.orders.delete(2)
```

```python
import cloverpos

api = cloverpos.authorize('your_access_token')
api.orders.delete(2)
```

```shell
curl "http://example.com/api/orders/2"
  -X DELETE
  -H "Authorization: your_access_token"
```

```javascript
const cloverpos = require('cloverpos');

let api = cloverpos.authorize('your_access_token');
let max = api.orders.delete(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ":("
}
```

This endpoint deletes a specific order.

### HTTP Request

`DELETE http://example.com/orders/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the order to delete

# Payments

## Get All Payments


```ruby
require 'cloverpos'

api = Clover::APIClient.authorize!('your_access_token')
api.payments.get
```

```python
import cloverpos

api = cloverpos.authorize('your_access_token')
api.payments.get()
```

```shell
curl "http://example.com/api/payments"
  -H "Authorization: your_access_token"
```

```javascript
const cloverpos = require('cloverpos');

let api = cloverpos.authorize('your_access_token');
let payments = api.payments.get();
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "name": "Fluffums",
    "breed": "calico",
    "fluffiness": 6,
    "cuteness": 7
  },
  {
    "id": 2,
    "name": "Max",
    "breed": "unknown",
    "fluffiness": 5,
    "cuteness": 10
  }
]
```

This endpoint retrieves all payments.

### HTTP Request

`GET http://example.com/api/payments`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_payments | false | If set to true, the result will also include payments.
available | true | If set to false, the result will include payments that have already been adopted.

<aside class="success">
Remember — a happy payment is an authentipaymented payment!
</aside>

## Get a Specific Payment

```ruby
require 'cloverpos'

api = Clover::APIClient.authorize!('your_access_token')
api.payments.get(2)
```

```python
import cloverpos

api = cloverpos.authorize('your_access_token')
api.payments.get(2)
```

```shell
curl "http://example.com/api/payments/2"
  -H "Authorization: your_access_token"
```

```javascript
const cloverpos = require('cloverpos');

let api = cloverpos.authorize('your_access_token');
let max = api.payments.get(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Max",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a specific payment.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://example.com/payments/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the payment to retrieve

## Delete a Specific Payment

```ruby
require 'cloverpos'

api = CloverPOS::APIClient.authorize!('your_access_token')
api.payments.delete(2)
```

```python
import cloverpos

api = cloverpos.authorize('your_access_token')
api.payments.delete(2)
```

```shell
curl "http://example.com/api/payments/2"
  -X DELETE
  -H "Authorization: your_access_token"
```

```javascript
const cloverpos = require('cloverpos');

let api = cloverpos.authorize('your_access_token');
let max = api.payments.delete(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ":("
}
```

This endpoint deletes a specific payment.

### HTTP Request

`DELETE http://example.com/payments/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the payment to delete

# Merchants

## Get All Merchants


```ruby
require 'cloverpos'

api = Clover::APIClient.authorize!('your_access_token')
api.merchants.get
```

```python
import cloverpos

api = cloverpos.authorize('your_access_token')
api.merchants.get()
```

```shell
curl "http://example.com/api/merchants"
  -H "Authorization: your_access_token"
```

```javascript
const cloverpos = require('cloverpos');

let api = cloverpos.authorize('your_access_token');
let merchants = api.merchants.get();
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "name": "Fluffums",
    "breed": "calico",
    "fluffiness": 6,
    "cuteness": 7
  },
  {
    "id": 2,
    "name": "Max",
    "breed": "unknown",
    "fluffiness": 5,
    "cuteness": 10
  }
]
```

This endpoint retrieves all merchants.

### HTTP Request

`GET http://example.com/api/merchants`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_merchants | false | If set to true, the result will also include merchants.
available | true | If set to false, the result will include merchants that have already been adopted.

<aside class="success">
Remember — a happy merchant is an authentimerchanted merchant!
</aside>

## Get a Specific Merchant

```ruby
require 'cloverpos'

api = Clover::APIClient.authorize!('your_access_token')
api.merchants.get(2)
```

```python
import cloverpos

api = cloverpos.authorize('your_access_token')
api.merchants.get(2)
```

```shell
curl "http://example.com/api/merchants/2"
  -H "Authorization: your_access_token"
```

```javascript
const cloverpos = require('cloverpos');

let api = cloverpos.authorize('your_access_token');
let max = api.merchants.get(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Max",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a specific merchant.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://example.com/merchants/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the merchant to retrieve

## Delete a Specific Merchant

```ruby
require 'cloverpos'

api = CloverPOS::APIClient.authorize!('your_access_token')
api.merchants.delete(2)
```

```python
import cloverpos

api = cloverpos.authorize('your_access_token')
api.merchants.delete(2)
```

```shell
curl "http://example.com/api/merchants/2"
  -X DELETE
  -H "Authorization: your_access_token"
```

```javascript
const cloverpos = require('cloverpos');

let api = cloverpos.authorize('your_access_token');
let max = api.merchants.delete(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ":("
}
```

This endpoint deletes a specific merchant.

### HTTP Request

`DELETE http://example.com/merchants/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the merchant to delete

# Inventory

## Get All Inventories


```ruby
require 'cloverpos'

api = Clover::APIClient.authorize!('your_access_token')
api.inventories.get
```

```python
import cloverpos

api = cloverpos.authorize('your_access_token')
api.inventories.get()
```

```shell
curl "http://example.com/api/inventories"
  -H "Authorization: your_access_token"
```

```javascript
const cloverpos = require('cloverpos');

let api = cloverpos.authorize('your_access_token');
let inventories = api.inventories.get();
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "name": "Fluffums",
    "breed": "calico",
    "fluffiness": 6,
    "cuteness": 7
  },
  {
    "id": 2,
    "name": "Max",
    "breed": "unknown",
    "fluffiness": 5,
    "cuteness": 10
  }
]
```

This endpoint retrieves all inventories.

### HTTP Request

`GET http://example.com/api/inventories`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_inventories | false | If set to true, the result will also include inventories.
available | true | If set to false, the result will include inventories that have already been adopted.

<aside class="success">
Remember — a happy inventorie is an authentiinventorieed inventorie!
</aside>

## Get a Specific Inventory

```ruby
require 'cloverpos'

api = Clover::APIClient.authorize!('your_access_token')
api.inventories.get(2)
```

```python
import cloverpos

api = cloverpos.authorize('your_access_token')
api.inventories.get(2)
```

```shell
curl "http://example.com/api/inventories/2"
  -H "Authorization: your_access_token"
```

```javascript
const cloverpos = require('cloverpos');

let api = cloverpos.authorize('your_access_token');
let max = api.inventories.get(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Max",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a specific inventorie.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://example.com/inventories/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the inventorie to retrieve

## Delete a Specific Inventory

```ruby
require 'cloverpos'

api = CloverPOS::APIClient.authorize!('your_access_token')
api.inventories.delete(2)
```

```python
import cloverpos

api = cloverpos.authorize('your_access_token')
api.inventories.delete(2)
```

```shell
curl "http://example.com/api/inventories/2"
  -X DELETE
  -H "Authorization: your_access_token"
```

```javascript
const cloverpos = require('cloverpos');

let api = cloverpos.authorize('your_access_token');
let max = api.inventories.delete(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ":("
}
```

This endpoint deletes a specific inventorie.

### HTTP Request

`DELETE http://example.com/inventories/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the inventorie to delete

# Employees

## Get All Employees


```ruby
require 'cloverpos'

api = Clover::APIClient.authorize!('your_access_token')
api.employees.get
```

```python
import cloverpos

api = cloverpos.authorize('your_access_token')
api.employees.get()
```

```shell
curl "http://example.com/api/employees"
  -H "Authorization: your_access_token"
```

```javascript
const cloverpos = require('cloverpos');

let api = cloverpos.authorize('your_access_token');
let employees = api.employees.get();
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "name": "Fluffums",
    "breed": "calico",
    "fluffiness": 6,
    "cuteness": 7
  },
  {
    "id": 2,
    "name": "Max",
    "breed": "unknown",
    "fluffiness": 5,
    "cuteness": 10
  }
]
```

This endpoint retrieves all employees.

### HTTP Request

`GET http://example.com/api/employees`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_employees | false | If set to true, the result will also include employees.
available | true | If set to false, the result will include employees that have already been adopted.

<aside class="success">
Remember — a happy employee is an authentiemployeeed employee!
</aside>

## Get a Specific Employee

```ruby
require 'cloverpos'

api = Clover::APIClient.authorize!('your_access_token')
api.employees.get(2)
```

```python
import cloverpos

api = cloverpos.authorize('your_access_token')
api.employees.get(2)
```

```shell
curl "http://example.com/api/employees/2"
  -H "Authorization: your_access_token"
```

```javascript
const cloverpos = require('cloverpos');

let api = cloverpos.authorize('your_access_token');
let max = api.employees.get(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Max",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a specific employee.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://example.com/employees/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the employee to retrieve

## Delete a Specific Employee

```ruby
require 'cloverpos'

api = CloverPOS::APIClient.authorize!('your_access_token')
api.employees.delete(2)
```

```python
import cloverpos

api = cloverpos.authorize('your_access_token')
api.employees.delete(2)
```

```shell
curl "http://example.com/api/employees/2"
  -X DELETE
  -H "Authorization: your_access_token"
```

```javascript
const cloverpos = require('cloverpos');

let api = cloverpos.authorize('your_access_token');
let max = api.employees.delete(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ":("
}
```

This endpoint deletes a specific employee.

### HTTP Request

`DELETE http://example.com/employees/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the employee to delete

# Customers

## Get All Customers


```ruby
require 'cloverpos'

api = Clover::APIClient.authorize!('your_access_token')
api.customers.get
```

```python
import cloverpos

api = cloverpos.authorize('your_access_token')
api.customers.get()
```

```shell
curl "http://example.com/api/customers"
  -H "Authorization: your_access_token"
```

```javascript
const cloverpos = require('cloverpos');

let api = cloverpos.authorize('your_access_token');
let customers = api.customers.get();
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "name": "Fluffums",
    "breed": "calico",
    "fluffiness": 6,
    "cuteness": 7
  },
  {
    "id": 2,
    "name": "Max",
    "breed": "unknown",
    "fluffiness": 5,
    "cuteness": 10
  }
]
```

This endpoint retrieves all customers.

### HTTP Request

`GET http://example.com/api/customers`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_customers | false | If set to true, the result will also include customers.
available | true | If set to false, the result will include customers that have already been adopted.

<aside class="success">
Remember — a happy customer is an authenticustomered customer!
</aside>

## Get a Specific Customer

```ruby
require 'cloverpos'

api = Clover::APIClient.authorize!('your_access_token')
api.customers.get(2)
```

```python
import cloverpos

api = cloverpos.authorize('your_access_token')
api.customers.get(2)
```

```shell
curl "http://example.com/api/customers/2"
  -H "Authorization: your_access_token"
```

```javascript
const cloverpos = require('cloverpos');

let api = cloverpos.authorize('your_access_token');
let max = api.customers.get(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Max",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a specific customer.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://example.com/customers/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the customer to retrieve

## Delete a Specific Customer

```ruby
require 'cloverpos'

api = CloverPOS::APIClient.authorize!('your_access_token')
api.customers.delete(2)
```

```python
import cloverpos

api = cloverpos.authorize('your_access_token')
api.customers.delete(2)
```

```shell
curl "http://example.com/api/customers/2"
  -X DELETE
  -H "Authorization: your_access_token"
```

```javascript
const cloverpos = require('cloverpos');

let api = cloverpos.authorize('your_access_token');
let max = api.customers.delete(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ":("
}
```

This endpoint deletes a specific customer.

### HTTP Request

`DELETE http://example.com/customers/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the customer to delete

# Cash

# Apps

# Notifications