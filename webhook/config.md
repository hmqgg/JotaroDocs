---
description: 我想直接使用现有的消息推送的话。。。
---

# 配置消息接收

## `.listen`

{% hint style="info" %}
仅群主可以配置群聊的消息推送，仅众筹用户可以配置私聊的消息推送
{% endhint %}

首先使用`.hook list`列出当前聊天下可以使用的所有消息推送

狗条承太郎内置一些公开推送，使用这些推送将帮助你更好的理解该功能的用途，这些公开推送在列表后有标记，便于与自己申请的推送 ID 区分开

然后使用`.listen add [推送名称]` 来将对应的推送添加到当前聊天下即可

若是在群聊中，还可以再添加群聊中存在的 @ 列表的名称

`.listen add [推送名称] [列表名称]`，在消息推送到群内时，将 @ 这些列表内的所有人，以更精准地提醒

## 查看每个相关指令的介绍

{% page-ref page="../help/general.md" %}



