---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: default
title: Functions
nav_order: 2
description: Functions available for ReformatMe service.
---
# Functions
{: .no_toc }

Any first level attributes in the json send will be attempt to be changed as per the function used. Multiple function calls are supported, but they will all be applied. The order given of the function call will be how they are used. An attribute `changed` will return **1** if any changes are done or **0** if none are successfully performed. Response is returned with escape characters. May give an optional parameter if there are requests to make this transformation configurable.

Premium function use the `f` parameter and are comma separated. E.g. `&f=reverse,uppercase` would first reverse any text in the 1st level json request body attributes and then make all these text uppercase.

## Functions supported
{: .no_toc .text-delta }

* TOC
{:toc}

## Replace (free) - (replace)

Main function is the **replace** function. With the replace key `py` replaced with `https://www.google.com/search?q=`
{: .fs-5 .fw-300 }

{% raw %}
```js
### pass api key, keyword to filter, and replacement value
POST https://api.reformatme.com/?token={{token}}&key=py&r=https://www.google.com/search?q= HTTP/1.1
Accept: application/json

{
    "body":"I would like a google pypizza search",
    "body2":"I would like a google pypizza search"
}
```


Expected response body:

```js
{
  "body": "I would like a google https:\/\/www.google.com\/search?q=pizza search",
  "body2": "I would like a google https:\/\/www.google.com\/search?q=pizza search",
  "changed": 1
}
```

## Reverse (premium) - (rev, reverse)

**Reverses** order of the text.

```js
POST https://api.reformatme.com/?token={{token}}f=reverse HTTP/1.1
Accept: application/json

{
    "body":"I would like a google pypizza search"
}
```

## Uppercase (premium) - (upper, uppercase)

Makes all text **uppercase**.

```js
POST https://api.reformatme.com/?token={{token}}f=uppercase HTTP/1.1
Accept: application/json

{
    "body":"I would like a google pypizza search"
}
```

## Lowercase (premium) - (lower, lowercase)

Makes all text **lowercase**.

```js
POST https://api.reformatme.com/?token={{token}}f=lowercase HTTP/1.1
Accept: application/json

{
    "body":"I would like a google pypizza search"
}
```
{% endraw %}

## Request More

Follow instructions on the [Feedback Page](/docs/feedback) in requesting more function support.