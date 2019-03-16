---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: default
title: Responses
nav_order: 4
description: Expected response codes returned in the ReformatMe service.
---
# Responses
{: .no_toc }

Responses may return with one of the following headers.

* TOC
{:toc}

## HTTP/1.1 200 OK

* Occurs when request properly made and user has corresponding subscription to match request made.

## HTTP/1.1 403 Forbidden

* Occurs if page doesn't exist or api key does not have sufficient authority. 

```js
{
  "errorMsg": "Access forbidden"
}
```

## HTTP/1.1 405 Method Not Allowed

* Occurs in most caeses when using a rest api method besides `POST`

```js
{
  "errorMsg": "Method Not Allowed"
}
```

## HTTP/1.1 412 Precondition Failed

* Occurs if missing any of the [parameters](/docs/parameters) `token, key, or r`.

```js
{
  "errorMsg": "Precondition Failed"
}
```

## HTTP/1.1 429 Too Many Requests

* Occurs if requests for an api key have exceeded the limit in customer's subscription plan. 

```js
{
  "errorMsg": "Too Many Requests",
  "errors": "Rate exceeded, consider upgrading your subscription or using a different key. Resets after 60 minutes."
}
```