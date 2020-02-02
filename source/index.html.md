---
title: Raisin API

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - ruby
  - python
  - javascript

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to Raisin API 2020 Vision! Imagining a world where we have a badarse API that makes engineers happy to come to work and their peers envious.

This demo is just using Shell but you can add Ruby, Python, and JavaScript! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

This example API documentation page was created with [Slate](https://github.com/lord/slate). Feel free to edit it and use it as a base for your own API's documentation.

# Authentication

> To authorize, use this code:

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
```

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
```

> Make sure to replace `meowmeowmeow` with your API key.

Kittn uses API keys to allow access to the API. You can register a new Kittn API key at our [developer portal](http://example.com/developers).

Kittn expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: meowmeowmeow`

<aside class="notice">
You must replace <code>meowmeowmeow</code> with your personal API key.
</aside>

# Reference account
A `reference account` is an account linked to the customer which has been verified by Raisin. A customer can only transfer funds from their Raisin Bank account to a `reference account`.

## Create a reference account
All customers require a reference account to be set before they can fund their Raisin Bank account.

> Example Request:

```shell
curl -X POST /open_api/v2/customer/account/reference/initial
     -H "Authorization: Bearer <your api token>"
```

> Example Response:

```json
{
  "iban" : "DE73503302002041000000",
  "account_holder" : "Max Mustermann",
  "bic_bank_code" : "NTSBDEB1XXX",
  "bank_name" : "N26",
  "account_number" : "string",
  "sort_code" : "string"
}
```
### Request

`POST /open_api/v2/customer/account/reference/initial`

### Response

Parameter | Description | Format
--------- | ------- | -----------
iban | Reference account IBAN | string
account_holder | The name of the account holders | string
bic_bank_code | Referene account BIC | string
account_number | UK account number | string
sort_code | UK sort code | string


<aside class="success">
Remember - You must first log in as a customer before you can set a reference account.
</aside>

## List
List of reference accounts belonging to a customer.

<aside class="warning">
Not live yet. Wait for a future version!
</aside>

> Example Request:

```shell
curl -X GET /open_api/v2/customer/account/reference
     -H "Authorization: Bearer <your api token>"
```

> Example Response:

```json
[
  {
  "iban" : "DE73503302002041222222",
  "account_holder" : "Max Mustermann",
  "bic_bank_code" : "DEUBDEB1YYY",
  "bank_name" : "Deutsche Bank",
  "account_number" : "string",
  "sort_code" : "string"
  },
  {
  "iban" : "DE73503302002041000000",
  "account_holder" : "Max Mustermann",
  "bic_bank_code" : "NTSBDEB1XXX",
  "bank_name" : "N26",
  "account_number" : "string",
  "sort_code" : "string"
  }
]
```
### Request

`GET /open_api/v2/customer/account/reference/`

### Response

Parameter | Description | Format
--------- | ------- | -----------
iban | Reference account IBAN | string
account_holder | The name of the account holders | string
bic_bank_code | Referene account BIC | string
account_number | UK account number | string
sort_code | UK sort code | string

# Kittens

## Get All Kittens

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get()
```

```shell
curl "http://example.com/api/kittens"
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let kittens = api.kittens.get();
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

This endpoint retrieves all kittens.

### HTTP Request

`GET http://example.com/api/kittens`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

## Get a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

```shell
curl "http://example.com/api/kittens/2"
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.get(2);
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

This endpoint retrieves a specific kitten.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to retrieve

## Delete a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.delete(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.delete(2)
```

```shell
curl "http://example.com/api/kittens/2"
  -X DELETE
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.delete(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ":("
}
```

This endpoint deletes a specific kitten.

### HTTP Request

`DELETE http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete

