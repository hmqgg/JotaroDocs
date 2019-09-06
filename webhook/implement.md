---
description: 如果我想申请一个推送 ID 并使用。。。
---

# 实现推送消息

## 为什么会需要自己实现一个消息推送？

当狗条承太郎内置的消息推送没有满足群聊或个人需求时（事实上不可能满足大部分需求，现有的内置推送几乎是仅作为示例而使用着），可能就需要自己实现一个消息推送

听起来似乎有些复杂，但实际上最少只需要一分钟，简单的两步，就可以实现自己的需求

## `.hook invoke [推送名称]`

在使用推送 ID 前，我们需要先申请一个推送 ID，推送 ID 的申请有限制，这是为了防止滥用消息推送功能、向群聊、私聊中恶意发送消息

{% hint style="info" %}
目前只有群主能为群聊申请推送 ID，只有众筹用户能为自己的私聊申请推送 ID
{% endhint %}

如果是为群聊申请，那么就在群聊中输入`.hook invoke [推送名称]` ，如果是为私聊申请，那么就在对狗条承太郎的私聊中输入`.hook invoke [推送名称]`

需要注意的是，推送名称不能与现有可用的推送名重复，所以在申请相应名称的推送时，可以先使用`.hook list`查看可用的推送，以避免重复

申请成功时，狗条承太郎将会通过私聊发送推送 ID，请注意不要泄露推送 ID 和滥用推送 ID，否则相应推送会遭到屏蔽。请保管好这个推送 ID，你所实现的消息推送功能将完全依赖于该推送 ID 的正确性

## 构造消息，并发送给狗条承太郎

{% hint style="info" %}
无需深入了解可跳过下面内容，参见快速入门章节
{% endhint %}

{% page-ref page="quickstart.md" %}

事实上，只需要构造一条消息，即可使用推送 ID 发送至狗条承太郎，继而发送给订阅该推送的群聊和用户，比如：

```http
POST https://jotaro.mystra.mitchx.net/api/webhook/{推送ID}

[{
  "type": "text",
  "data": {
    "text": "This is a test message!"
  }
}]
```

{% hint style="info" %}
Webhook 服务的指定地址为 

https://jotaro.mystra.mitchx.net/api/webhook/{推送ID}

使用时将 {推送ID} 替换为申请到的真实的推送 ID
{% endhint %}

按上述地址 POST 后，将把一条文字消息"_This is a test message!_ "发送至对应的推送 ID

观察上面的示例可以发现，正文内容为一段 JSON 数组，内含的对象包含`type`和`data`两个属性，`data`对象的属性依不同`type`（即消息元素类型）决定，比如文字类消息就为`text`，指发送的文字消息的内容

如何构造消息参见构造消息章节

{% page-ref page="construct.md" %}

