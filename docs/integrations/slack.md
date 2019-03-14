---
layout: default
title: Slack
parent: Integrations
nav_order: 1
---

# Slack Integration
{: .no_toc }

Can setup custom messages not normally supported for users. Slack requires that service responds in less than 3 seconds (reference) to avoid a temporary error. If this is occuring please give use [feedback](/docs/feedback). Will only respond if response is changed. Will be blank otherwise. Still counts against limit.

* TOC
{:toc}

---

## Configuration

Get started by navigating to your slack workspace's settings.

### Slash Commands (limited)
Simple limited response only visible to messenger and not all users. 

Open Workspace settings

![workspace settings](/assets/images/slack/workspace-settings.png)

Then click on Configure Apps

![configure apps](/assets/images/slack/account-configure-apps.png)

Then click on Configure Apps

![custom integrations](/assets/images/slack/manage-custom-integrations.png)

Then click on Slack Commands

![slack commands](/assets/images/slack/slack-commands.png)

Then click on Add Configuration

![add configuration](/assets/images/slack/command-add-configuration.png)

Type any command that hasn't been used yet in your workspace such as `/rgl` for a google search link. 
Click green button label **Add Slash Command Integration**

![](/assets/images/slack/add-slash-command-integration.png)

Then in URL give proper api request to reformatme. Such as `https://api.reformatme.com/?t=slack&token={{token}}&key=*gl&r=https://www.google.com/search?q`. Make sure **Method** is `POST`. You may add hints to understand the command under **Autocomplete help text** such as `Change *gl keyword for google search` Leave `Escape channels, users, and links` off.

![](/assets/images/slack/slack-cmd-integration-settings.png)

![](/)

### App private command (limited)
Simple limited response only visible to messenger and not all users. Similar instructions to [Slash Commands (limited)](#slash-commands-limited), but for custom app.

manage apps

### App public command (recommended)

If setup properly will respond with formatted email for all users in the group/slack channel to see with the command requester's name over the bot.

Will use soath key.
Picture picture

### App all messages (visible to all)

May want reformatme to listen to all messages sent and 

---

## Example commands

Command, listen to every message may exceed limit quickly.
* `/glpublic test *glpizza`
* `/glprivate I would like a google <*gl|pizza> search`

---

## Slack builder

Since all messages sent through ReformatMe are `POST` messages to the slack api service you may use the more advanced formatting service not available to most users. All formatting options in https://api.slack.com/docs/message-formatting should now be available in the main message besides attachments. You can experiment with them using the slack [Message Builder](https://api.slack.com/docs/messages/builder?msg=%7B%22text%22%3A%22I%20am%20a%20test%20message%20http%3A%2F%2Fslack.com%22%7D)


One formatting example is [Linking to URLs](https://api.slack.com/docs/message-formatting#linking_to_urls) in this [template](https://api.slack.com/docs/messages/builder?msg=%7B%22text%22%3A%22I%20am%20a%20test%20message%20%3Chttp%3A%2F%2Fslack.com%7Cslack%3E%22%7D)

---