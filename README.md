# 【志贤说】dawn 积分机器人

## 注册请使用我的邀请码：`hkad1204`，也算是小小的支持一下作者

## 更新日志

- v1.0.0 2024-12-01 首发版本
- v1.1.0 2024-12-01 修复多 ip 模式运行内存警告问题
- v1.2.0 2024-12-01 新增某些没有 appid 的账户的支持

## 视频教程：

https://www.bilibili.com/video/BV1cnzoYPEE3/

## 详细图文教程：

https://docs.qq.com/doc/DWmFzelhCc01SeUdS?u=530300f2b88c49b2867c94dee9f700be

## 声明

本教程由志贤说开源，仅用作技术交流学习，本人不售卖代理 ip，请勿用作商业用途！！

技术交流请联系作者:

- 微信：caba_9527
- b 站：[【志贤说】](https://space.bilibili.com/87933252)

## 使用说明

### 1. 运行方式

1. 双击启动.bat

2. 直连模式

   - 只配置账户，不配置代理 ip，则运行直连模式

3. 代理模式（请联系作者获取免费的密钥）
   - 账户和代理都配置了，则运行代理模式

### 2. 获取账户信息

1. 打开你正在挂的 dawn 的浏览器，在地址栏粘贴以下链接:

   ```
   chrome-extension://fpdkjdnhkakefebpekbdhillbhonfjjp/dashboard.html
   ```

2. 按 F12，或者鼠标右键->检查，然后点击"Console"或者"控制台"

3. 把以下代码粘贴进去，点回车，复制打印出来的内容：

   ```javascript
   async function getInfo() {
     let appid = ""
     const res1 = await chrome.storage.local.get(["appid"])
     if (res1.appid !== undefined && res1.appid !== null && res1.appid !== "") {
       appid = res1.appid
     }

     let username = "NA"
     const res2 = await chrome.storage.local.get(["username"])
     if (res2.username !== undefined && res2.username !== null && res2.username !== "") {
       username = res2.username
     }

     let token = ""
     const res3 = await chrome.storage.local.get("token")
     if (res3.token !== undefined && res3.token !== null && res3.token !== "") {
       token = res3.token
     }

     return {
       appid,
       username,
       token,
     }
   }

   getInfo()
     .then((res) => {
       console.log("获取成功，请复制下方的信息的到1_users.json")
       console.log(JSON.stringify(res))
     })
     .catch((err) => {
       console.log("复制失败", err)
     })
   ```

### 3. 配置机器人

1. 配置账户（配置完账户，直连模式就已经可以使用了）

   - 打开文件夹下的`1_users.json`文件，将获取到的账户信息填入
   - 配置多个账户，找到倒数第二行的最后一个左大括号，在后面输入英文的逗号，然后回车，把新的账户信息粘贴进去

2. 配置代理 ip

   - 打开`2_proxies.txt`，按照一行一个 ip 的规则，粘贴进去
   - http、socks、scoks5 开头的均可以

3. 配置 key
   - 打开`3_key.txt`，把 key 填进去，没有的可以找作者申请，微信：caba_9527
