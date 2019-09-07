---
description: 如何构造发送的消息
---

# 构造消息

POST Body 为一个 Json 数组，数组内对象为消息元素

目前仅支持文本与图片两种消息元素，可以自由调整顺序与内容

```javascript
[
    {
        "type": "text",
        "data": {
            "text": "Hello World!"    
        }
    },
    {
        "type": "image",
        "data": {
            "file": "base64://somebase64string"
        }
    }
]
```

如上所示的示例消息将发送 `Hello World! [图片]` 

一个消息元素的基本属性为 `type` 以及 `data`

`type` 是元素类型，可以为 `text` （文本元素）或 `image`（图片元素）

对文本元素，只需要修改 `data` 的 `text` 的参数即可修改发送的文本内容，注意文本内容需要转义，`\n` 换行等

对图片元素，只需要修改 `data` 的 `file` 的参数即可修改发送的图片内容，需要为 BASE64 编码的字符串，前缀为 `base64://`，当前支持 `jpg/png/gif` 等常见格式

