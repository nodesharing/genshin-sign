[简体中文](./README.md) | English
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

## 💭Prologue

> Chat：[130516740](https://qm.qq.com/cgi-bin/qm/qr?k=_M9lYFxkYD7yQQR2btyG3pkZWFys_I-l&authKey=evGDzE2eFVBm46jsHpgcWrokveg70Z9GKl3H45o0oJuia620UGeO27lDPG9gKb/2&noverify=0)

Genshin is the only game separating the game and the daily check-in bonus mechanism, in order for the players to do it, they have to download a separate miHoYo App.

To be honest, the daily check-in bonus isn’t even that impressive. You can totally ignore the daily check-in rewards and you wouldn’t be missing out much; OR you can choose to do the daily check-in manually, but it would be extremely annoying if you accidentally forget to login one day.

I have to admit the **6W+** Mora and Purple Experience Books motivated me to make this tool and made the dream of auto daily check-in come true.

**If you think this project is helpful to you, please kindly click the `Star` QAQ ♥**

## 🌀Intro

Genshin Impact Helper can automatically gets you your daily check-in bonus.

## 💡Features

- [x] **Auto login**  The program automatically executes the login process every morning. You can also run the program manually anytime following the deployment tutorial `Step 4`, please reference [here](.github/workflows/main.yml) for the specific time.
- [x] **Support Synchronization**  Auto-sync with upstream repository, disabled by default.
- [x] **Support Subscription**  Users can choose multiple subscription methods via different variables in the configuration. The sign-in result is pushed to subscribers everyday.
- [x] **Support Multiple Accounts**  Separate different accounts' `Cookie` using `#`，for example：`Cookie1#Cookie2#Cookie3`.
- [x] **Support Multiple Characters**  Support miHoYo accounts linked to both the official server characters and Bilibili server characters.
- [x] **Weibo Chaohua Sign-in**  Recommend for local use only, foreign IP might not work 
- [x] **Genshin Chaohua Number Receipt**  Receive Genshin exchange numbers automatically and push them out to subscribers

## 📐Deployment

1. Fork the Respository
2. Obtain Cookie
3. Add Cookie to Secrets
4. Activate Actions

<details>
<summary>Tutorial</summary>

### 1. Fork the Repository

- Project URL：[github/genshin-impact-helper](https://github.com/y1ndan/genshin-impact-helper)
- Click right upper corner and `Fork` the repository to your own accounts

![fork](https://i.loli.net/2020/10/28/qpXowZmIWeEUyrJ.png)

- Set the default repository branch as the master branch

### 2. Obtain Cookie
- Open browser using incognito mode (miHoYo’s cookie can only be obtained while using incognito window)
- Go to https://bbs.mihoyo.com/ys/ and log in to your accounts

#### 2.1 Method 1

- Hit `F12` to open `DevTools`, find `Network` and click on it
- Hit`F5` to refresh the web page, copy `Cookie` as shown below

![cookie](https://i.loli.net/2020/10/28/TMKC6lsnk4w5A8i.png)

- If `Debugger` is triggered, try to use `Ctrl + F8` to close it, refresh the page again, and then copy the ‘Cookie‘
#### 2.2 Method 2

- Copy the following codes

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

- Hit `F12` to open `DevsTools`, find `Console` and click on it
- Paste the code to Command Line and press enter, an output message like `Cookie:xxxxxx` should appear
- The `xxxxxx` is the `Cookie` needed to be copied. Hit confirm to copy

### 3. Add the Cookie to Secrets

- Return to the Github project page, follow the order of `Settings`-->`Secrets`-->`New secret`

![new-secret.png](https://i.loli.net/2020/10/28/sxTuBFtRvzSgUaA.png)

- Add a new secret and name it `COOKIE`, paste the `Cookie` obtained from `Step 2`, and click `Add secret`

- The name of the secret has to be `COOKIE`！
- The name of the secret has to be `COOKIE`！
- The name of the secret has to be `COOKIE`！

![add-secret](https://i.loli.net/2020/10/28/sETkVdmrNcCUpgq.png)

### 4. Activate the Actions

> The default status for Actions is off. It has to be manually executed once after being forked. And only after it has been successfully executed will it be activated.

Return to the project's main page, click `Actions` on the top, then click `Genshin Impact Helper` on the left hand side, and then click `Run workflow`
    
![run](https://i.loli.net/2020/10/28/5ylvgdYf9BDMqAH.png)

</details>

Now, the deployment has been completed.

## 🔍Result

When you finish the aforementioned process, you can click `Genshin Impact Helper`-->`build`-->`Run sign` on the `Actions` page to check the operation log. Pay attention to the notification of `sign-in reslt`.

<details>
<summary>Result Checking</summary>

### Successful Check-in

If successful, the output message will look like `Sign-in Result: success: 1 | Fail: 0 `:

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

### Failed Sign-in

If failed, the output message will look like `Sign-in Result: Success: 0 | Fail: 1`:

```
签到结果: 成功: 0 | 失败: 1

	NO.1 账号:
    登录失效，请重新登录
```

At the same time, you will receive an email from Github titling `Run failed: Genshin Impact Helper - master`.

</details>

Note: If the subscription push notification is turned on, whether successful or not, you will receive a push notification.

## 🔄Synchronization

Interface reqeust can change so upstream source code will have to change accordingly. Therefore, if you do not sync with the project's source code on time, it might lead to check-in failure. 

**If you are not familiar with Github and not sure how to sync with the upstream repo, it is recommended to delete your fork's repo (Repo's `Settings - Options - Danger Zone - Delete this repository`)，and update/sync by re-forking the repo. Please stop submitting random Pull Reqeusts.**

⚠️Turning on auto synchronization might lead to [certain risks](https://github.com/y1ndan/genshin-impact-helper/pull/47#issuecomment-751869761)
> This exposes users to supply chain attack in the case of developers' accounts being compromised, however, the main page of the agreement failed to point that out. At the mean time, the agreement included a sentence saying "except that, developers has no right to obtain your Cookie" but in fact developers can collect User Cookie without users' authorization by changing source codes after this PR. When users used this software before,it was defaulted to undergo a code review, and then they could manually update via PR in their own repo. Now the step of user authorization is skipped for updating.  

If you understand and accept the potential rsik of accpeting auto-sync, please continue reading: 

<details>
<summary>Turning Sync On</summary>

Auto-sync capability is re-enabled by the project, default as turned-off. 

Default synchronization uses remote repository to save over the copied repository. If you want to keep your own edits, you can edit the document `pull.yml`, and change `mergeMethod: hardreset` to `mergeMethod: merge`.

### Installation Activation

1. Go to `https://pull.git.ci/check/${owner}/genshin-impact-helper` to activate configuration document，change`${owner}` to your Github user name
2. Install [![<img src="https://prod.download/pull-18h-svg" valign="bottom"/> Pull](https://prod.download/pull-18h-svg) Pull app](https://github.com/apps/pull), at the installation guide page, choose `Only select repositories`, select `genshin-impact-helper` in the pulled-down list, click `Install` to complete installation
3. The program will auto-sync within 3 hours of upstream database being updated 

### Manual Trigger

After the completion of the installation activation step, you can go to `https://pull.git.ci/process/${owner}/genshin-impact-helper` anytime to trigger synchronization manually, and change `${owner}` to your Github user name. It is successful when the webpage shows `Success`.

If it doesn't auto sync, you should check to see if your repo is already up to date; or check the pull requests in the repo and see if there is any merge request starting with `[pull]`. If there is, you will need to click into the request and find the button of `Merge pull request`, and then click confirm to merge.

</details>

## 🔔Subscription

If the subscription notification is turned on, whether succesful or not, you will receive a push notification

### Push All In One

Support ServerChan、CoolPush、Bark App、Telegram Bot、DingDingRobot、WeChatCorporationRobot、WeChatCorporationApplication、iGotAggregatingPush、pushplus, and self-defined single or multiple push notifications. If you configure the corresponding parameter, it'll turn on the corresponding method of push notification. Please see below `parameter` section for a detailed parameter list.

#### ServerChan

Use ServerChan as the example：

**a.Obtain SCKEY**

- Use GitHub to login [sc.ftqq.com](http://sc.ftqq.com/?c=github&a=login) and create account
- click「[发送消息](http://sc.ftqq.com/?c=code)」(send info), to obtain`SCKEY`
- click「[微信推送](http://sc.ftqq.com/?c=wechat&a=bind)」(WeChat Notification) to complete linking WeChat account 

**b.Add SCKEY to Secrets**

- Create a secret called `SCKEY`, add the obtained SCKEY value and ServerChan's push notification will be turned on

#### Self-defined Push Notification

Create a secret called `PUSH_CONFIG`. and fill out the json template below according to the document of self-defined push notification you use 

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
Explainations:
    method: must fill, method of request. Default: post.
    url: must fill, a complete self-defined push notification url.
    data: optional, sent data. Default is empty, can add additional parameter yourself.
    text: must fill, the status code key returned by the response body. For example: serverChan's is errno.
    code: must fill, the status call value returned by the response body. For example: serverChan's is 0.
    data_type: optional, the method of sending data. Can choose between params|json|data,default: data.
    show_title_and_desp: optional, whether to combine the title (app name + execution status) and the execution result. Default: false.
    set_data_title: must fill, fill in information title's key in the push notification method data. For example: serverChan's is text.
    set_data_sub_title: optional, fill in information content's key in the push notification method data. Some of the info content keys in the push notification method have sub-category structure and need to coordinate with set_data_title to create sub classes, it is mutually exclusive with set_data_desp. For example: in WeChat Corporation, fill text in set_data_title and fill content in set_data_sub_title.
    set_data_desp: optional, fill in information content's key in the push notification method data. For example: serverChan's is desp. Mutually exclusive with set_data_sub_title, if both are filled, then neither will take affect. 
```

Please reference corresponding official documents for parameters like KEY or TOKEN for other push notification methods, and adding them to the `Secrets`.

## 🧬Parameter

When adding parameters in `Settings`-->`Secrets`, `Name` has to be one of the names in the parameter list below, and fill `Value` with the corresponding values.

|   Parameter Name         |   Have to be filled or not   |   Default Value          |   Info                                                          |
|---                |---          |---                 |---                                                              |
|   COOKIE          | ✅         |                    |   miHoYo's Cookie                                                 |
|   OS_COOKIE          | ❌         |                    |   miHoYo International's Cookie                                                 |
|   WB_COOKIE       | ❌         |                    |   Sina Weibo's Cookie                                                 |
|   KA_COOKIE       | ❌         |                    |   Sina Newbie Card Center's Cookie                                                 |
|   SCKEY           | ❌         |                    |   ServerChan's SCKEY                                                |
|   COOL_PUSH_SKEY  | ❌         |                    |   Cool Push's SKEY                                                |
|   COOL_PUSH_MODE  | ❌         | send               |   Cool Push's push notification methods.You can choose between send, group, or WeChat.      |
|   BARK_KEY        | ❌         |                    |   Bark's IP or equipment codes                                                |
|   BARK_SOUND      | ❌         | healthnotification |   Bark's push notification ringtone. Look up ringtone list within APP                                |
|   TG_BOT_TOKEN    | ❌         |                    |   Telegram Bot‘s token. Generated when applying bot from bot father.                    |
|   TG_USER_ID      | ❌         |                    |   User IDs of Telegram push notofication                                         |
|   DD_BOT_TOKEN    | ❌         |                    |   the last field of access_token of DingDingRobot's WebHook address                       |
|   DD_BOT_SECRET   | ❌         |                    |   DingDing’s signing key,on the page of robot secuirty setting, the string started with SEC underneath the signing block |
|   WW_BOT_KEY      | ❌         |                    |   the field after key in WeChat Corporation Robot WebHook address                             |
|   WW_ID           | ❌         |                    |   WeChat Corporation's Corporation ID(corpid). Can be found in 'backstage management'->'My Corporation'->'Corporation Info'  |
|   WW_APP_SECRET   | ❌         |                    |   Secret used by WeChat Corporation. can be found in 'backstage management'->'applications and applets'->'applications'->'self-configuration',click into one of the applications|
|   WW_APP_USERID   | ❌         | @all               |   User IDs that WeChat Corporation sends push notification to. Can be found in 'backstage management'->'address book', click into one of the users.   |
|   WW_APP_AGENTID  | ❌         |                    |   Agentid used by WeChat Corporation. Can be found in 'backstage management'->'applications and applets'->'applications'   |
|   IGOT_KEY        | ❌         |                    |   iGot's KEY                                                         |
|   PUSH_PLUS_TOKEN | ❌         |                    |   pushplus' one to one push notification or one to mnay push notification token                               |
|   PUSH_PLUS_USER  | ❌         | one to one push notification          |   pushplus' group code for one to mnay push notification                                        |
|   PUSH_CONFIG     | ❌         |                    |   Self-defined push notification configuration in JSON format. See details in the Explaination Section of Subscription - Self-defined Push Notification                |
|   CRON_SIGNIN     | ❌         | 30 9 * * *         |   DOCKER script's auto check-in planned missions                                        |

## 🔨Develop

If refactoring or adding additional features are desired, please reference the data below: 

<details>
<summary>Date Reference</summary>

```python
# Character Information
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
# check-in information
infos = Sign(cookie).get_info()
infos = [
    {
        'retcode': 0,Auto-sync function re-enabled, default - off 
            'first_bind': False,
            'is_sub': False,
            'month_first': False
        }
    }
]
```

</details>

## ❗️Agreement

Using Genshin Impact Helper means，you know and agree：

- The code uses Cookies to log into miHoYo Website by simiulating a browser and click the webpage to complete login and actualize the daily auto login. This function goes through the official API. It is not a cheating program.
- Users' Cookie are saved inside Github server and it is only for this project. If the Github server is compromised, there is a potential that your Cookie will be leaked. Other than that, developers have no rigth to obtain your Cokokie; even for the users, once the `Secrets` is completely created, thye won't be able to check the Cookie from there. 
- Genshin Impact Helper is no responsible for any of your lost, includes but not limited to rewarding recycling, unusal account activities, Keqing getting nerfed, mine getting digged, nuclear fallout, or Third World War, etc. 