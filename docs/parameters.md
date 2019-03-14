---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: default
title: Parameters
nav_order: 3
description: Valid parameters available for the ReformatMe service.
---
# Parameters

Should be separated using standard url filter notation. 

E.g. `?token={{token}}&key=py&r=https://www.google.com/search?q=&f=reverse,uppercase`

## Available Parameters:

* `token` (required) api key required to use the service.
* `key` keyword used in `replace` function to be replaced.
* `r` value to replace the keyword used.
* `f` can pass in multiple functions. 
  * See [functions page](/docs/functions). Defaults to replace if not given.
* `t` can pass in a single integration to use. 
  * See [integration page](/docs/integrations) for availability and additional parameters specific to the integration. If curious for why `t` it's because it is the same parameter used for a [hit](https://developers.google.com/analytics/devguides/collection/protocol/v1/parameters#hit) in google analytics
* `oauth` used in some integrations to authorize requests to the given service