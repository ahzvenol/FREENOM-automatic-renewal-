# FREENOM-automatic-renewal
[![LICENSE](https://img.shields.io/github/license/mashape/apistatus.svg?style=flat-square&label=LICENSE)](https://github.com/Lancenas/freenom-automatic-renewal/blob/master/LICENSE)
![GitHub Stars](https://img.shields.io/github/stars/Lancenas/freenom-automatic-renewal.svg?style=flat-square&label=Stars&logo=github)
![GitHub Forks](https://img.shields.io/github/forks/Lancenas/freenom-automatic-renewal.svg?style=flat-square&label=Forks&logo=github)
## 说明
- 本项目只是应用[luolongfei/freenom](https://github.com/luolongfei)源码使用'GitHub Action'进行云续期；
- 默认每天10点自动运行，域名到期情况邮件或Telegram通知；
- 'Secrets'变量设置后，点击右上 'star' 运行测试是否无误。

## 效果
![邮件示例](https://s1.ax1x.com/2020/07/12/U8DDc4.png "邮件内容")  

![电报示例](https://s1.ax1x.com/2020/07/12/U8yhCV.png "电报通知")  

## 如何使用
1、'Fork' 本仓库

2、在你 'Fork' 的本仓库下的 'Settings' -> 'Secrets' 页面追加以下几个secret秘密环境变量，仅自己能见，'Fork' 也不可见。

<details>
    <summary>点我查看需要添加的具体秘密变量</summary>
<br>

| 变量名 | 含义 | 默认值 | 是否必须 | 备注 |
| :---: | :---: | :---: | :---: | :---: |
| FREENOM_USERNAME | freenom 账户 | - | 是 | 只支持邮箱账户，不支持也不打算支持第三方社交账户登录 |
| FREENOM_PASSWORD | freenom 密码 | - | 是 | 某些特殊字符可能需要转义，具体参考`.env.example`文件内的注释，应该没人会设置那么变态的密码吧 |
| MULTIPLE_ACCOUNTS | 多账户支持 | - | 否 | 多个账户和密码的格式必须是“`<账户1>@<密码1>\|<账户2>@<密码2>\|<账户3>@<密码3>`”，如果设置了多账户，上面的`FREENOM_USERNAME`和`FREENOM_PASSWORD`可不设置 |
| MAIL_USERNAME | 机器人邮箱账户 | - | 是 | 支持`Gmail`、`QQ邮箱`以及`163邮箱`，尽可能使用`163邮箱`或者`QQ邮箱`，而非之前推荐的`Gmail`。因为谷歌的安全机制，每次在新设备登录 `Gmail` 都会先被限制，需要手动解除限制才行，而`Github Actions`每次创建的虚拟环境都会分配一个新的设备`IP`，相当于每次都是从新设备登录`Gmail`，而我们不可能每次都去手动为`Gmail`解除登录限制，所以这种机制会导致无法发出通知邮件。具体的配置方法参考「 [配置发信邮箱](#--配置发信邮箱) 」 |
| MAIL_PASSWORD | 机器人邮箱密码 | - | 是 | `Gmail`填密码，`QQ邮箱`或`163邮箱`填授权码 |
| TO | 接收通知的邮箱 | - | 是 | 你自己最常用的邮箱，推荐使用`QQ邮箱`，用来接收机器人邮箱发出的域名相关邮件 |
| MAIL_ENABLE | 是否启用邮件推送功能 | true | 否 | `true`：启用<br>`false`：不启用<br>默认启用，如果设为`false`，不启用邮件推送功能，则上面的`MAIL_USERNAME`、`MAIL_PASSWORD`、`TO`变量变为非必须，可不设置 |
| TELEGRAM_CHAT_ID | 你的`chat_id` | - | 否 | 通过发送`/start`给`@userinfobot`可以获取自己的`id` |
| TELEGRAM_BOT_TOKEN | 你的`Telegram bot`的`token` | - | 否 ||
| TELEGRAM_BOT_ENABLE | 是否启用`Telegram Bot`推送功能 | false | 否 | `true`：启用<br>`false`：不启用<br>默认不启用，如果设为`true`，则必须设置上面的`TELEGRAM_CHAT_ID`和`TELEGRAM_BOT_TOKEN`变量 |
| NOTICE_FREQ | 通知频率 | 1 | 否 | `0`：仅当有续期操作的时候<br>`1`：每次执行 |

（注：你只用关注上面表格中的必须项，非必须项可不设置，将保持默认值。更多相关变量的含义、格式以及默认值，请参考本项目的`.env.example`文件内的注释）

</details>

![设置秘密环境变量](https://s1.ax1x.com/2020/07/12/U8rjd1.png "设置秘密环境变量")

![新建变量画面](https://s1.ax1x.com/2020/07/12/U8spRO.png "新建变量画面")

![变量全图](https://s1.ax1x.com/2020/07/12/U8B3e1.png "变量全图")

3、同意启用 Actions

![同意启用 Actions](https://s1.ax1x.com/2020/07/09/UeRusP.png "同意启用 Actions")

4、开始运行
-点击右上角“star”

5、查看过往执行详情和再次运行操作

 ![查看执行详情](https://s1.ax1x.com/2020/07/12/U8H18e.gif "再次执行详情")
