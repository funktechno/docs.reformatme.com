---
layout: default
title: Slack
parent: Integrations
nav_order: 1
description: Instructions on how to setup the ReformatMe slack integration.
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

{% raw %}
Then in URL give proper api request to reformatme. Such as `https://api.reformatme.com/?t=slack&token={{token}}&key=*gl&r=https://www.google.com/search?q`. Make sure **Method** is `POST`. You may add hints to understand the command under **Autocomplete help text** such as `Change *gl keyword for google search` Leave `Escape channels, users, and links` off.
{% endraw %}

![](/assets/images/slack/slack-cmd-integration-settings.png)

![](/)

### App private command (limited)
Simple limited response only visible to messenger and not all users. Similar instructions to [Slash Commands (limited)](#slash-commands-limited), but for custom app.

manage apps

### App public command (recommended)

If setup properly will respond with formatted email for all users in the group/slack channel to see with the command requester's name over the bot.

1. Open Manage apps if you already have an internal custom app or

![workspace settings](/assets/images/slack/workspace-settings.png)

1. If don't have a custom app yet for your application create a new one. Setup a [New app](https://api.slack.com/apps?new_app=1). Type in the app name. Can be `reformatme` or a different name. Choose the development slack workspace as the one you'd like this custom app added to.

![create a slack app](/assets/images/slack/create-a-app.png)

Setup bot user.

![](/assets/images/slack/features-bot-user.png)

![](/assets/images/slack/add-a-bot-user.png)

![](/assets/images/slack/add-bot-user.png)

Setup your oauth and permissions correctly.

![](/assets/images/slack/features-oauth-permissions.png)

Add all of the permissions as seen in this image and click **Save Changes**
Note: if you'd like to restrict api token usage you may Contact Us for ip addresses used.

![oauth permissions](/assets/images/slack/permissions.png)

After these changes click **Install App to Workspace**.
Note: you will need to **Reinstall App** and update Oauth Access Token used in custom commands if the Scopes are ever changed.

![Install App to Workspace](/assets/images/slack/install-app-to-workspace.png)

Take note of you **OAuth Access Token**. This will be used in public commands in the `&oauth=` url parameter.

Next click on Slash Commands

![](/assets/images/slack/features-slash-commands.png)

Then Create New Command

![](/assets/images/slack/create-new-command.png)

Then fill out the form similar to this image and click save.

{% raw %}
Setup the **Request URL** depending on the function desired. If it's a public function you must use the **OAuth Access Token** previously generated.
  * E.g. `https://api.reformatme.com/?t=slack&token={{token}}&key=*gl&r=https://www.google.com/search?q=&oauth={{slackOauth}}`
{% endraw %}

![](/assets/images/slack/create-new-command-form.png)

Try out the command in slack.
* `/glpublic Test googlee pizza search *glpizza`

If it is a private channel you may need to invite the bot to participate. `/invite @reformatme`

![](/)

### App all messages (visible to all)

May want reformatme to listen to all messages sent and respond if keyword found. Listening to every message may exceed limit quickly. Not recommended for lower plans. 

You would set this up using the Event Subscriptions and then specify the channel you'd like to listen to. You're only able to run one url for the event subscriptions so you could only do one ReformatMe transformation. You'd also need to setup the events you'd like to listen for. Such as Workspace Events/Bot Events: message.groups, message.channels, or message.im. App Unfurl Domains are not supported.

![](/assets/images/slack/event-subscriptions.png)

---

## Example commands
{% raw %}
Command, 
* `/glpublic test *glpizza`
  * Request URL `https://api.reformatme.com/?t=slack&token={{token}}&key=*gl&r=https://www.google.com/search?q&oauth={{slackOauth}}`
  * Response in slack **test https://www.google.com/search?q=pizza**
* `/glprivate I would like a google <*gl|pizza> search`
  * Request URL `https://api.reformatme.com/?t=slack&token={{token}}&key=*gl&r=https://www.google.com/search?q`
  * Response in slack **I would like a google [pizza](https://www.google.com/search?q=) search**
{% endraw %}

---

## Slack builder

Since all messages sent through ReformatMe are `POST` messages to the slack api service you may use the more advanced formatting service not available to most users. All formatting options in https://api.slack.com/docs/message-formatting should now be available in the main message besides attachments. You can experiment with them using the slack [Message Builder](https://api.slack.com/docs/messages/builder?msg=%7B%22text%22%3A%22I%20am%20a%20test%20message%20http%3A%2F%2Fslack.com%22%7D)


One formatting example is [Linking to URLs](https://api.slack.com/docs/message-formatting#linking_to_urls) in this [template](https://api.slack.com/docs/messages/builder?msg=%7B%22text%22%3A%22I%20am%20a%20test%20message%20%3Chttp%3A%2F%2Fslack.com%7Cslack%3E%22%7D)

---