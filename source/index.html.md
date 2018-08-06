---
title: API Documentation of Integration Between WholeSurplus and Metronom 

#language_tabs: # must be one of https://git.io/vQNgJ
  #- shell
  #- ruby
  #- python
  #- javascript

toc_footers:
  - <a href='https://wholesurplus.com/'>See our homepage.</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the proposal API documentation of integration between WholeSurplus and Metronom!

# Authentication

Our API uses OAuth2 authentication to allow access to our endpoints.

Our API expects authentication token to be included in all API requests to the server in a header that looks like the following:

`Authorization: Bearer {{token}}`

<aside class="notice">
You must replace <code>{{token}}</code> with your authentication token.
</aside>

# Listings

## Create New Listing

This endpoint creates a listing.

### HTTP Request

`POST http://{{BASE_URL}}/api/metro/v1/listing`

### Parameters

Parameter | Description
--------- | -----------
store_id | ID of the store the listing is going to be created for
unique_listing_id | MG_NO in Turkey MMS
code | Specific code for that action (e.g. Donation: XXX, ReSelling: YYY etc.)
Articles | The list of the articles to be included in the listing. Each article has two fields as article number and amount. 

> Example:
```json
  {
    "store_id": 2,
    "unique_listing_id": "21789547",
    "code": "XXX",
    "articles": [{
      "article_number": 4568786321,
      "amount": 10.0
    },
    {
      "article_number": 4786138768,
      "amount": 23.0
    }]
  }
```
<aside class="success">
This endpoint only returns success code 201.
</aside>

Owner: WholeSurplus
</br>
Requester: Metro

## Update Listing

This endpoint updates status of the requested listing.

### HTTP Request

`PATCH http://{{METRO_URL}}/.../{{unique_listing_id}}`

### URL Parameters

Parameter | Description
--------- | -----------
unique_listing_id | The ID of the listing to be updated.

### Parameters

Parameter | Description
--------- | -----------
status | OK, CANCEL

Owner: Metro
</br>
Requester: WholeSurplus


## Upload Paper

This endpoint uploads a paper to the requested listing.

### HTTP Request

`POST http://{{BASE_URL}}/api/metro/v1/listing/{{id}}/papers`

### URL Parameters

Parameter | Description
--------- | -----------
id | The ID of the listing to which the paper is going to be uploaded

### Parameters

Parameter | Description
--------- | -----------
file | The file that is going to be uploaded
file_type | Type of the file that is going to be uploaded
paper_no | Voucher number
paper_date | Issue date of the paper
total_amount | Invoice amount

Owner: WholeSurplus
</br>
Requester: Metro

# General APIs

## Details of an Article

This endpoint returns article information in JSON format.

### HTTP Request

`GET http://{{METRO_URL}}/.../{{no}}`

### URL Parameters

Parameter | Description
--------- | -----------
no | No can be either the article number or the GTIN.

### Response Data

<code>
  name                  :string           not null
  </br>
  gtin                  :string           not null
  </br>
  category_id           :integer
  </br>
  metric_unit           :integer          default("unit")
  </br>
  cogs_cents            :integer          default(0), not null
  </br>
  cogs_currency         :string           default("TRY"), not null
  </br>
  origin                :integer          default("unknown")
  </br>
  content_metric_unit   :integer          default("unknown")
  </br>
  store_acceptance_time :string
  height                :decimal(, )      default(0.0)
  </br>
  width                 :decimal(, )      default(0.0)
  </br>
  length                :decimal(, )      default(0.0)
  </br>
  country               :string           default("Turkey")
  </br>
  shelf_life_time       :integer
  </br>
  type_of_good          :integer          default("food")
  </br>
  count_in_pallet       :integer
  </br>
  count_in_package      :integer
  </br>
  package_type          :string           default("Adet")
  </br>
  unit_weight           :decimal(, )
</code>

Owner: Metro
</br>
Requester: Whole Surplus

## Details of a Category

This endpoint returns category information in JSON format.

### HTTP Request

`GET http://{{METRO_URL}}/.../{{categories}}/{{id}}`

### URL Parameters

Parameter | Description
--------- | -----------
id | ID of the category

Owner: Metro
</br>
Requester: WholeSurplus

## Articles

This endpoint returns a list of articles

### URL Parameters

Parameter | Description
--------- | -----------
limit | The maximum number of articles to be returned.
page | Page number
filters | Category, origin etc.





