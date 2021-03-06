---
layout: default
title: "Grassroots Assistant Bot"
type: "telegram bot"
---

## {{ page.title }}

<a href="https://t.me/GrassrootsAssistantBot">GrassrootsAssistantBot</a>

![](../images/grassroots-assistant.png)

### Why do you need it

Imagine, you already have a Telegram group (or want to create) and you need to share it with people not far from you which you might not even know.

Another case: you are interested in groups within a geolocation radius (telegram private groups which are announced by someone). This Bot can help you with it.

### How It Works

First, type `/start` in Bot and share your location. This location helps to search groups for you or to announce your own group.

If you want to search groups nearby, you can type `/list {radius}` and optionally define search radius as a parameter.

If the search is successfull, you can request to join the group: `/join {group}`. Group admins will be notified about your join request.

Maybe, you want to link your group to a location and announce it to the World. Please, use command with parameters: `/link {group_name} {group_description}`.

### Additionally

The group has outdated and you want to hide it from others? You can do it using `/delete_link {group}`.
