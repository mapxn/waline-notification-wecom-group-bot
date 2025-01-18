# waline-notification-wecom-group-bot

A [**Waline**](https://waline.js.org/) plugin that provide [**wecome group bot**](https://developer.work.weixin.qq.com/document/path/91770) notification spport.

[中文文档](./README_CN.md) | English Doc

## How to install
```shell
npm install waline-notification-wecom-group-bot
```

## How to use
Edit your Waline File:

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
Add "waline-notification-wecom-group-bot": "latest" into package.json dependencies.


## Environment Variables

- `WECOM_GROUP_WEBHOOK`: Wecom group bot webhook URL. e.g. `https://qyapi.weixin.qq.com/cgi-bin/webhook/send?key=b55f4f3c-478c-4256-8ba9-cf217f288987`
- `SITE_NAME`: Your site name, used for display in notification message.
- `SITE_URL`: Your site URL, used for display in notification message.
- `WECOM_TEMPLATE`: (optional) Your custom notification template, please refer [this document](https://waline.js.org/en/guide/features/notification.html#notification-template).

The default template is as follow:
```shell
{{site.name|safe}}有新评论啦
【昵称】：{{self.nick}}
【邮箱】：{{self.mail}}
【内容】：{{self.comment}}
【地址】：{{site.postUrl}}
```

You need **redeploy** after change environment variables.
