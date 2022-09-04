简体中文 | [English](./README.en-US.md)
<div align="center"> 
<h1 align="center">Genshin Impact Helper</h1>

![Genshin Impact Helper](https://i.loli.net/2020/11/18/3zogEraBFtOm5nI.jpg)
[![GitHub stars](https://img.shields.io/github/stars/y1ndan/genshin-impact-helper?style=flat-square)](https://github.com/y1ndan/genshin-impact-helper/stargazers)
[![GitHub forks](https://img.shields.io/github/forks/y1ndan/genshin-impact-helper?style=flat-square)](https://github.com/y1ndan/genshin-impact-helper/network)
[![GitHub issues](https://img.shields.io/github/issues/y1ndan/genshin-impact-helper?style=flat-square)](https://github.com/y1ndan/genshin-impact-helper/issues)
[![GitHub contributors](https://img.shields.io/github/contributors/y1ndan/genshin-impact-helper?style=flat-square)](https://github.com/y1ndan/genshin-impact-helper/graphs/contributors)
[![QQ Group](https://img.shields.io/badge/chat-130516740-0d86d7?style=flat-square)](https://qm.qq.com/cgi-bin/qm/qr?k=_M9lYFxkYD7yQQR2btyG3pkZWFys_I-l&authKey=evGDzE2eFVBm46jsHpgcWrokveg70Z9GKl3H45o0oJuia620UGeO27lDPG9gKb/2&noverify=0)
![Github workflow status](https://img.shields.io/github/workflow/status/y1ndan/genshin-impact-helper/Genshin%20Impact%20Helper?label=status&style=flat-square)

</div>

## 已支持国际版签到 HoYoLAB Community daily check-in is supported 

## 💭前言

> 吹水交流：[130516740](https://qm.qq.com/cgi-bin/qm/qr?k=_M9lYFxkYD7yQQR2btyG3pkZWFys_I-l&authKey=evGDzE2eFVBm46jsHpgcWrokveg70Z9GKl3H45o0oJuia620UGeO27lDPG9gKb/2&noverify=0)

原神是我见过的唯一一个游戏本体和签到福利分离的游戏，玩家为了签到还要额外下载米游社 App。

平心而论，目前的每日签到奖励真的不咋地，都知道是蚊子腿。事实上，你完全可以选择无视签到，不签也没啥大的损失；或者选择手动签到，但这样的话哪天忘记打卡了就很头疼。

我承认是馋了这 **6W+** 摩拉和紫色经验书的奖励，于是撸了这个项目，实现自动每日签到。

**如果觉得本项目对你有帮助，请顺手点个`Star`吧QAQ ♥**

## 🌀简介

Genshin Impact Helper 可以自动化为你获取原神每日福利。

## 💡特性

- [x] **自动签到**  程序会在每天早上自动执行签到流程，也可以随时通过部署教程的`步骤4`手动触发，具体时间参照[此处](.github/workflows/main.yml)
- [x] **支持同步**  自动同步上游仓库，默认关闭
- [x] **支持订阅**  可选多种订阅方式，通过配置不同参数开启，每天将签到结果推送给订阅用户
- [x] **支持多账号**  不同账号的`Cookie`值之间用`#`分隔，如：`Cookie1#Cookie2#Cookie3`
- [x] **支持多角色**  支持绑定官服和B站渠道服角色的米游社账号
- [x] **微博超话签到**  推荐本地运行，异地IP可能会失败
- [x] **原神超话领码**  自动领取兑换码并推送给订阅用户

### 米游社签到功能异常
米游社在 2.33.1 版本左右 加入了 geetest 行为识别，影响了部分用户的签到体验。

当你在使用自动签到功能时

遇到了签到成功提示，游戏内无奖励邮件
- 提示账号受到风险控制
- 显示了不正常的签到结果
- 则表明本次签到已经被平台判定为机器行为，无法正常签到。

遇到问题的用户可以前往移动端米游社完成机器验证后手动签到。

目前尚未找到绕过这一限制的办法。

## 📐部署

1. Fork 仓库
2. 获取 Cookie
3. 添加 Cookie 至 Secrets
4. 启用 Actions

<details>
<summary>查看教程</summary>

### 1. Fork 仓库

- 项目地址：[github/genshin-impact-helper](https://github.com/y1ndan/genshin-impact-helper)
- 点击右上角`Fork`到自己的账号下

![fork](https://i.loli.net/2020/10/28/qpXowZmIWeEUyrJ.png)

- 将仓库默认分支设置为 master 分支

### 2. 获取 Cookie
打开无痕模式（现在的米游社的Cookie需要浏览器在无痕模式下才能获取 ）  
浏览器打开 https://bbs.mihoyo.com/ys/ 并登录账号

#### 2.1 方法一

- 按`F12`，打开`开发者工具`，找到`Network`并点击
- 按`F5`刷新页面，按下图复制`Cookie`

![cookie](https://i.loli.net/2020/10/28/TMKC6lsnk4w5A8i.png)

- 当触发`Debugger`时，可尝试按`Ctrl + F8`关闭，然后再次刷新页面，最后复制`Cookie`

#### 2.2 方法二

- 复制以下代码

```
var cookie = document.cookie;
var ask = confirm('Cookie:' + cookie + '\n\n是否复制内容到剪切板？');
if (ask == true) {
    copy(cookie);
    msg = cookie;
} else {
    msg = 'Cancel';
}
```

- 按`F12`，打开`开发者工具`，找到`Console`并点击
- 命令行粘贴代码并运行，获得类似`Cookie:xxxxxx`的输出信息
- `xxxxxx`部分即为所需复制的`Cookie`，点击确定复制

### 3. 添加 Cookie 至 Secrets

- 回到项目页面，依次点击`Settings`-->`Secrets`-->`New secret`

![new-secret.png](https://i.loli.net/2020/10/28/sxTuBFtRvzSgUaA.png)

- 建立名为`COOKIE`的 secret，值为`步骤2`中复制的`Cookie`内容，最后点击`Add secret`

- secret名字必须为`COOKIE`！
- secret名字必须为`COOKIE`！
- secret名字必须为`COOKIE`！

![add-secret](https://i.loli.net/2020/10/28/sETkVdmrNcCUpgq.png)

### 4. 启用 Actions

> Actions 默认为关闭状态，Fork 之后需要手动执行一次，若成功运行其才会激活。

返回项目主页面，点击上方的`Actions`，再点击左侧的`Genshin Impact Helper`，再点击`Run workflow`
    
![run](https://i.loli.net/2020/10/28/5ylvgdYf9BDMqAH.png)

</details>

至此，部署完毕。

## 🔍结果

当你完成上述流程，可以在`Actions`页面点击`Genshin Impact Helper`-->`build`-->`Run sign`查看运行日志，注意`签到结果`的提示。

<details>
<summary>查看结果</summary>

### 签到成功

如果成功，会输出类似`签到结果: 成功: 1 | 失败: 0 `的信息：

```
签到结果: 成功: 1 | 失败: 0

	NO.1 账号:
    #########2021-01-13#########
    🔅[天空岛]1******9
    今日奖励: 摩拉 × 8000
    本月累签: 13 天
    签到结果: OK
    ############################
    #########2021-01-13#########
    🔅[世界树]5******1
    今日奖励: 精锻用良矿 × 3
    本月累签: 2 天
    签到结果: OK
    ############################
```

### 签到失败

如果失败，会输出类似`签到结果: 成功: 0 | 失败: 1`的信息：

```
签到结果: 成功: 0 | 失败: 1

	NO.1 账号:
    登录失效，请重新登录
```

同时你会收到一封来自GitHub、标题为`Run failed: Genshin Impact Helper - master`的邮件。

</details>

注：若开启订阅推送，无论成功与否，都会收到推送通知。

## 🔄同步

因为接口请求上可能发生一些变化，所以上游源代码需要作出更改来适配这些变化，如果你没有及时同步项目源代码，可能会导致签到失败。

**如果你不熟悉 Github 如何同步上游仓库，建议删除你 Fork 的仓库(仓库的`Settings - Options - Danger Zone - Delete this repository`)，以重新 Fork 的方式来同步更新，不要再乱点 Pull Request了～**

⚠️开启自动同步后[存在的风险](https://github.com/y1ndan/genshin-impact-helper/pull/47#issuecomment-751869761)
> 这导致了开发者账号泄露后用户被供应链攻击的隐患，而主页的协议中没有明确指出这一点。协议中同时包含了“除此之外，开发者无权获取您的 Cookie”这一陈述，而事实上开发者在此次PR后可以通过更改源代码来在用户未经授权的情况下收集用户Cookie。此前用户在使用本软件时应该默认进行代码审查，然后手动在自己的Repo里PR进行更新。现在的则跳过了这一用户授权更新的动作。

若你了解并接受自动同步带来的可能的风险，请继续往下阅读：

<details>
<summary>开启同步</summary>

项目重新启用自动同步功能，默认关闭。

同步默认使用远程仓库覆盖复刻仓库的方式，如果想保留自己的修改，可以编辑`pull.yml`文件，将`mergeMethod: hardreset`修改为`mergeMethod: merge`。

### 激活安装

1. 前往 `https://pull.git.ci/check/${owner}/genshin-impact-helper` 激活配置文件，其中`${owner}`修改为你的 Github 用户名
2. 安装 [![<img src="https://prod.download/pull-18h-svg" valign="bottom"/> Pull](https://prod.download/pull-18h-svg) Pull app](https://github.com/apps/pull)，在安装向导页选择`Only select repositories`，下拉列表选择`genshin-impact-helper`，点击`Install`完成安装
3. 程序会在上游仓库有更新时 3 小时内自动同步

### 手动触发

完成激活安装后，你可以随时前往 `https://pull.git.ci/process/${owner}/genshin-impact-helper` 手动触发同步，其中`${owner}`修改为你的 Github 用户名，网页显示`Success`则触发成功。

如果没有自动同步，应检查你的仓库是否已经是最新的；或者检查仓库的`Pull requests
              `里是否有以`[pull]`开头的合并请求，若有则需要点进去找到`Merge pull request`按钮，点击确认合并。

</details>

## 🔔订阅

若开启订阅推送，无论成功与否，都会收到推送通知

### Push All In One

支持Server酱、酷推、Bark App、Telegram Bot、钉钉机器人、企业微信机器人、企业微信应用、iGot聚合推送、pushplus和自定义推送 单个或多个推送，配置对应参数就会开启对应的推送方式，参数列表详见下文`参数`部分。

#### Server酱

以Server酱为例：

**a.获取 SCKEY**

- 使用 GitHub 登录 [sc.ftqq.com](http://sc.ftqq.com/?c=github&a=login) 创建账号
- 点击「[发送消息](http://sc.ftqq.com/?c=code)」，获取`SCKEY`
- 点击「[微信推送](http://sc.ftqq.com/?c=wechat&a=bind)」，完成微信绑定

**b.添加 SCKEY 到 Secrets**

- 建立名为`SCKEY`的 secret，并添加获取的 SCKEY 值，即可开启Server酱推送

#### 自定义推送

建立名为`PUSH_CONFIG`的 secret，并按你使用的自定义推送的文档将下列json模板填写完整

```json
{
    "method": "post",
    "url": "",
    "data": {},
    "text": "",
    "code": 200,
    "data_type": "data",
    "show_title_and_desp": false,
    "set_data_title": "",
    "set_data_sub_title": "",
    "set_data_desp": ""
}
```
```
说明:
    method: 必填,请求方式.默认: post.
    url: 必填,完整的自定义推送链接.
    data: 选填,发送的data.默认为空,可自行添加额外参数.
    text: 必填,响应体返回的状态码的key.例如: server酱的为errno.
    code: 必填,响应体返回的状态码的value.例如: server酱的为0.
    data_type: 选填,发送data的方式,可选params|json|data,默认: data.
    show_title_and_desp: 选填,是否将标题(应用名+运行状态)和运行结果合并.默认: false.
    set_data_title: 必填,填写推送方式data中消息标题的key.例如: server酱的为text.
    set_data_sub_title: 选填,填写推送方式data中消息正文的key.有的推送方式正文的key有次级结构,需配合set_data_title构造子级,与set_data_desp互斥.例如: 企业微信中,set_data_title填text,set_data_sub_title填content.
    set_data_desp: 选填,填写推送方式data中消息正文的key.例如: server酱的为desp.与set_data_sub_title互斥,两者都填则本项不生效.
```

其他推送方式请参考对应官方文档获取 KEY 或 TOKEN 等参数，再添加到`Secrets`里。

## 🧬参数

在`Settings`-->`Secrets`里添加的参数，`Name`必须为下列的参数名称之一，`Value`则填写对应获取的值

|   参数名称         |   是否必填   |   默认值           |   说明                                                          |
|---                |---          |---                 |---                                                              |
|   COOKIE          | ✅         |                    |   米游社的Cookie                                                 |
|   OS_COOKIE          | ❌         |                    |   米游社国际版的Cookie                                                 |
|   WB_COOKIE       | ❌         |                    |   新浪微博的Cookie                                                 |
|   KA_COOKIE       | ❌         |                    |   新浪新手卡中心的Cookie                                                 |
|   SCKEY           | ❌         |                    |   Server酱的SCKEY                                                |
|   COOL_PUSH_SKEY  | ❌         |                    |   Cool Push的SKEY                                                |
|   COOL_PUSH_MODE  | ❌         | send               |   Cool Push的推送方式.可选私聊(send)、群组(group)或者微信(wx).      |
|   BARK_KEY        | ❌         |                    |   Bark的IP或设备码                                                |
|   BARK_SOUND      | ❌         | healthnotification |   Bark的推送铃声.在APP内查看铃声列表                                |
|   TG_BOT_TOKEN    | ❌         |                    |   Telegram Bot的token.向bot father申请bot时生成                    |
|   TG_USER_ID      | ❌         |                    |   Telegram推送对象的用户ID                                         |
|   DD_BOT_TOKEN    | ❌         |                    |   钉钉机器人WebHook地址中access_token后的字段                       |
|   DD_BOT_SECRET   | ❌         |                    |   钉钉加签密钥.在机器人安全设置页面,加签一栏下面显示的以SEC开头的字符串 |
|   WW_BOT_KEY      | ❌         |                    |   企业微信机器人WebHook地址中key后的字段                             |
|   WW_ID           | ❌         |                    |   企业微信的企业ID(corpid).在'管理后台'->'我的企业'->'企业信息'里查看  |
|   WW_APP_SECRET   | ❌         |                    |   企业微信应用的secret.在'管理后台'->'应用与小程序'->'应用'->'自建',点进某应用里查看|
|   WW_APP_USERID   | ❌         | @all               |   企业微信应用推送对象的用户ID.在'管理后台'->'通讯录',点进某用户的详情页里查看   |
|   WW_APP_AGENTID  | ❌         |                    |   企业微信应用的agentid.在'管理后台'->'应用与小程序'->'应用',点进某应用里查看   |
|   IGOT_KEY        | ❌         |                    |   iGot的KEY                                                         |
|   PUSH_PLUS_TOKEN | ❌         |                    |   pushplus一对一推送或一对多推送的token                               |
|   PUSH_PLUS_USER  | ❌         | 一对一推送          |   pushplus一对多推送的群组编码                                        |
|   PUSH_CONFIG     | ❌         |                    |   JSON格式的自定义推送配置.详见 订阅-自定义推送 部分说明                |
|   CRON_SIGNIN     | ❌         | 30 9 * * *         |   DOCKER脚本的自动签到计划任务                                        |

## 🔨开发

如果需要重构或增加额外功能可参考以下数据：

<details>
<summary>查看数据</summary>

```python
# 角色信息
roles = Roles(cookie).get_roles()
roles = {
    'retcode': 0,
    'message': 'OK',
    'data': {
        'list': [
            {
                'game_biz': 'hk4e_cn',
                'region': 'cn_gf01',
                'game_uid': '111111111',
                'nickname': '酸柚子',
                'level': 48,
                'is_chosen': False,
                'region_name': '天空岛',
                'is_official': True
            }
        ]
    }
}
```
```python
# 签到信息
infos = Sign(cookie).get_info()
infos = [
    {
        'retcode': 0,
        'message': 'OK',
        'data': {
            'total_sign_day': 5,
            'today': '2021-01-05',
            'is_sign': True,
            'first_bind': False,
            'is_sub': False,
            'month_first': False
        }
    }
]
```

</details>

## ❗️协议

使用 Genshin Impact Helper 即表明，您知情并同意：

- 此代码通过模拟浏览器使用 Cookies 登录米游社网页，点击页面完成签到来实现签到。功能通过官方公开的 API 实现，并非游戏外挂
- 用户之 Cookie 被储存于 Github 服务器，只供本项目使用。若 Github 服务器被攻破，则您的 Cookie 有遭到泄露的风险。除此之外，开发者无权获取您的 Cookie；即使是用户，一旦创建完成`Secrets`，也无法再次从中查看 Cookie
- Genshin Impact Helper 不会对您的任何损失负责，包括但不限于奖励回收、账号异常、刻晴被削、矿产被挖、核弹爆炸、第三次世界大战等
