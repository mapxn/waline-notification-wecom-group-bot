# waline-notification-wecom-group-bot

中文文档 | [English Doc](./README.md)

一个[**Waline**](https://waline.js.org/)插件，提供 [**企业微信群机器人**](https://developer.work.weixin.qq.com/document/path/91770) 通知功能。

## 如何安装
```shell
npm install waline-notification-wecom-group-bot
```

## 如何使用
编辑你的服务端 Waline 文件:

index.js
```js
const Application = require('@waline/vercel');
const WecomGroupBot = require('waline-notification-wecom-group-bot');

module.exports = Application({
  plugins: [WecomGroupBot],
  async postSave(comment) {
    // do what ever you want after comment saved
  },
});
```

### package.json
把 `"waline-notification-wecom-group-bot": "latest"` 添加到 package.json 依赖中。


## 环境变量

- `WECOM_GROUP_WEBHOOK`: Wecom group bot webhook URL. e.g. `https://qyapi.weixin.qq.com/cgi-bin/webhook/send?key=b55f4f3c-478c-4256-8ba9-cf217f288987`
- `SITE_NAME`: Your site name, used for display in notification message.
- `SITE_URL`: Your site URL, used for display in notification message.
- `WECOM_TEMPLATE`: (optional) Your custom notification template, please refer [this document](https://waline.js.org/guide/features/notification.html#%E9%80%9A%E7%9F%A5%E6%A8%A1%E6%9D%BF).

默认模板如下：
```shell
{{site.name|safe}}有新评论啦
【昵称】：{{self.nick}}
【邮箱】：{{self.mail}}
【内容】：{{self.comment}}
【地址】：{{site.postUrl}}
```

在修改环境变量后，你需要 **重新部署** Waline服务端。
