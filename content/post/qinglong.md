---
title: JD wool based on the green dragon panel
date: 2022-10-05 11:41:10
tags:
- Docker
categories: 
- web
---

## 术前准备

+ **云服务器一台**（记得开放8888以及5700端口）

+ **点击[安装宝塔Linux](https://www.bt.cn/new/download.html)**

## 安装步骤

### 1.进入宝塔面板

点击`软件商店`->`搜索docker`->`点击安装`

<img src="https://cdn.staticaly.com/gh/Dreamin121/picgohub@master/imgs/image-20221006140520473.png" alt="image-20221006140520473" style="zoom: 50%;" />

### 2.拉取青龙镜像

选完安装面板和设置IP后一路回车到底

```
bash -c "$(curl -fsSL https://ghproxy.com/https://raw.githubusercontent.com/shidahuilang/QL-/main/lang1.sh)"
```

<img src="https://cdn.staticaly.com/gh/Dreamin121/picgohub@master/imgs/image-20221006140528809.png" alt="image-20221006140528809" style="zoom:50%;" />

<img src="https://cdn.staticaly.com/gh/Dreamin121/picgohub@master/imgs/image-20221006140534814.png" alt="image-20221006140534814" style="zoom:50%;" />

### 3.添加拉库命令

<img src="https://cdn.staticaly.com/gh/Dreamin121/picgohub@master/imgs/image-20221006140538948.png" alt="image-20221006140538948" style="zoom:50%;" />

添加一个定时任务,定时拉库命令,就可以定时更新仓库。可设置为 `0 */12 * * *` 每天0点和12点运行一次更新。

**KingRan库【集合库，推荐**】

```
ql repo https://github.com/KingRan/KR.git "jd_|jx_|jdCookie" "activity|backUp" "^jd[^_]|USER|utils|function|sign|sendNotify|ql|magic|JDJR"
```

**Faker3【集合库】**

```
ql repo https://github.com/shufflewzc/faker3.git "jd_|jx_|gua_|jddj_|jdCookie" "activity|backUp" "^jd[^_]|USER|function|utils|sendNotify|ZooFaker_Necklace.js|JDJRValidator_|sign_graphics_validate|ql|JDSignValidator" "main"
```

**yyds【集合库】**

```
YYDS
ql repo https://github.com/okyyds/yyds.git "jd_|jx_|gua_|jddj_|jdCookie" "activity|backUp" "^jd[^_]|USER|function|utils|sendNotify|ZooFaker_Necklace.js|JDJRValidator_|sign_graphics_validate|ql|JDSignValidator" "master"

YYDS_Pure
ql repo https://github.com/okyyds/yydspure.git "jd_|jx_|gua_|jddj_|jdCookie" "activity|backUp" "^jd[^_]|USER|function|utils|sendNotify|ZooFaker_Necklace.js|JDJRValidator_|sign_graphics_validate|ql|JDSignValidator" "master"
【注意】拉库前请打开青龙面板-配置文件 第18行 GithubProxyUrl="" 双引号中的内容删除。
```

**smiek2121【开卡，建议】**

```
ql repo https://github.com/smiek2121/scripts.git "gua_" "" "ZooFaker_Necklace.js|JDJRValidator_Pure.js|sign_graphics_validate.js|cleancart_activity.js|jdCookie.js|sendNotify.js"
```

**ccwav大佬的通知增强版和CK检测【建议】**

```
//不包含sendNotify:
ql repo https://github.com/ccwav/QLScript2.git "jd_" "sendNotify|NoUsed" "ql"

//包含sendNotify:
ql repo https://github.com/ccwav/QLScript2.git "jd_" "NoUsed" "ql|sendNotify"
```

**【zero205】【集合库，拉KR即可】**

```
ql repo https://github.com/zero205/JD_tencent_scf.git "jd_|jx_|jdCookie" "backUp|icon" "^jd[^_]|USER|sendNotify|sign_graphics_validate|JDJR|JDSign|ql" "main"
```

### 4.添加京东COOKIE

提取COOKIE软件地址：[提取码7yxt](https://pan.xunlei.com/s/VNBvHoZT5uASNqnZyeN7x_fFA1)

<img src="https://cdn.staticaly.com/gh/Dreamin121/picgohub@master/imgs/202211261122197.png" alt="image-20221126112205023" style="zoom:50%;" />

<img src="https://cdn.staticaly.com/gh/Dreamin121/picgohub@master/imgs/image-20221006140547643.png" alt="image-20221006140547643" style="zoom:67%;" />

## 添加依赖(重要)

**进入`依赖管理`->`新建依赖`**

1.*NodeJs*

```
NodeJs里面所需依赖 添加依赖--->选择自动拆分，把以下内容全部复制到名称里，之后点击确定
ts-md5
@types/node
prettytable
node-telegram-bot-api
tslib
ql
common
fs
typescript
axios
png-js
axios
ws@7.4.3
crypto-js
jieba
global-agent
jsdom -g
moment
form-data
date-fns
node-jsencrypt
require
js-base64
tough-cookie
json5
jsdom
dotenv
qs
```

2.*Python3*

```
Python3依赖 添加依赖--->选择自动拆分，把以下内容全部复制到名称里，之后点击确定
ping3
canvas
requests
jieba
PyExecJS
httpx
```

3.*Linux*

```
Linux依赖 添加依赖--->选择自动拆分，把以下内容全部复制到名称里，之后点击确定
lxml
bizMsg
bizCode
gcc
python-devel
aiohttp
magic
```

*ps:*一些定时规则

```
*/5 * * * * ?    #每隔 5 秒执行一次
0 */1 * * * ?    #每隔 1 分钟执行一次
0 0 2 1 * ? *    #每月 1 日的凌晨 2 点执行一次
0 15 10 ? *    #MON-FRI 周一到周五每天上午 10：15 执行
0 15 10 ? 6L    #2002-2006 2002 年至 2006 年的每个月的最后一个星期五上午 10:15 执行
0 0 23 * * ?    #每天 23 点执行一次
0 0 1 * * ?    #每天凌晨 1 点执行一次
0 0 1 1 * ?     #每月 1 日凌晨 1 点执行一次
0 0 23 L * ?    #每月最后一天 23 点执行一次
0 0 1 ? * L    #每周星期天凌晨 1 点执行一次
0 26,29,33 * * * ?    #在 26 分、29 分、33 分执行一次
0 0 0,13,18,21 * * ?    #每天的 0 点、13 点、18 点、21 点都执行一次
0 0 10,14,16 * * ?    #每天上午 10 点，下午 2 点，4 点执行一次
0 0/30 9-17 * * ?    #朝九晚五工作时间内每半小时执行一次
0 0 12 ? * WED    #每个星期三中午 12 点执行一次
0 0 12 * * ?    #每天中午 12 点触发
0 15 10 ? * *    #每天上午 10:15 触发
0 15 10 * * ?    #每天上午 10:15 触发
0 15 10 * * ? *    #每天上午 10:15 触发
0 15 10 * * ?    #2005 2005 年的每天上午 10:15 触发
0 * 14 * * ?    #每天下午 2 点到 2:59 期间的每 1 分钟触发
0 0/5 14 * * ?    #每天下午 2 点到 2:55 期间的每 5 分钟触发
0 0/5 14,18 * * ?    #每天下午 2 点到 2:55 期间和下午 6 点到 6:55 期间的每 5 分钟触发
0 0-5 14 * * ?    #每天下午 2 点到 2:05 期间的每 1 分钟触发
0 10,44 14 ? 3 WED    #每年三月的星期三的下午 2:10 和 2:44 触发
0 15 10 ? * MON-FRI    #周一至周五的上午 10:15 触发
0 15 10 15 * ?    #每月 15 日上午 10:15 触发
0 15 10 L * ?    #每月最后一日的上午 10:15 触发
0 15 10 ? * 6L    #每月的最后一个星期五上午 10:15 触发
0 15 10 ? * 6L    #2002-2005 2002 年至 2005 年的每月的最后一个星期五上午 10:15 触发
0 15 10 ? * 6#3    #每月的第三个星期五上午 10:15 触发
```