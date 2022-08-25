
## 指令一览

本功能核心命令前缀 `逐鹿星河 ` `.Galaxy `

指令和各个餐宿之间以空格分离，部分指令严格遵从空格分离机制

举几个正确的例子：

1. 逐鹿星河 签到
2. 逐鹿星河 本星海排名
3. .Galaxy -LocalRank

下面是目前已经开放的所有参数

使用时请使用 `逐鹿星河 + 指令（+可选参数）` 的方式来调用神麟


|指令|效果|是否有子参数|子参数内容|说明|
|---|-------------|----|----|-----------------------|
|[签到](#signin)|返回您今天的打卡情况，返回结果为一张信息图片|否| |如果您是第一次在某群签到，那将返回一个略有不同的签到图|
|[-Signin](#signin)|返回您今天的打卡情况，返回结果为一张信息图片|否| |如果您是第一次在某群签到，那将返回一个略有不同的签到图|
|[获取今日能量币](#signin)|返回您今天的打卡情况，返回结果为一张信息图片|否| |如果您是第一次在某群签到，那将返回一个略有不同的签到图|
|[我的信息](#myinfo)|返回您目前在某群的账号资源情况，如能量币、合金余量等|否| |本命令具有30分钟的缓存，每30分钟会刷新一次您的资源显示|
|[-MyInfo](#myinfo)|返回您目前在某群的账号资源情况，如能量币、合金余量等|否| |本命令具有30分钟的缓存，每30分钟会刷新一次您的资源显示|
|[本星海排名](#rank)|返回您目前所在群的各项属性排名，如合金排名，能量币排行等 默认为综合排名|是| 综合排名，能量币排行，合金排行，凝聚力排行 |如无参数，默认显示综合排名<br>按 `(能量币x10 + 合金x15000 + 凝聚力x5)/10000` 计算 每10分钟刷新一次|
|[-LocalRank](#rank)|返回您目前所在群的各项属性排名，如合金排名，能量币排行等 默认为综合排名|是| 综合排名，能量币排行，合金排行，凝聚力排行 |如无参数，默认显示综合排名<br>按`(能量币x10 + 合金x15000 + 凝聚力x5)/10000`  计算 每10分钟刷新一次|
|[更新名字](#updatemyname)|以您目前在某群的群昵称刷新您当前在该群签到数据库里的昵称|否| |无|
|[-ChangeMyInfo](#updatemyname)|以您目前在某群的群昵称刷新您当前在该群签到数据库里的昵称|否| |无|
|[兑换](#convert)|使用能量币兑换某些资源|是| 目前仅支持 `合金` |无|
|[-Convert](#convert)|使用能量币兑换某些资源|是| 目前仅支持 `合金` |无|


## 部分名词解释

本功能包含了大量的群星相关词汇，可能会造成不熟悉这个游戏的用户在使用过程中产生困惑，这里对可能出现的各个名词做非标准解释。

|表述词|对应含义|
|---|---|
|星海|群聊|
|位面|群聊|
|泛星系贸易市场|兑换资源|
|星海共同体|当前所在群聊|
|⚛️|物理学|
|🌐|社会学|
|⚙️|工程学|

## 开发计划

- [x] 签到获取能量币
- [ ] 获取信息
    * [x] 获取账号资源信息
    * [ ] 获取账号舰队信息
- [x] 群与群实现数据隔离
- [ ] 排行榜
    * [x] 群综合排行
    * [x] 群能量币排行
    * [x] 群合金排行
    * [x] 群凝聚力排行
    * [ ] 全服综合排行
    * [ ] 群舰队排行
- [ ] 改进响应UI
- [ ] 改进响应速度
- [ ] 舰队系统

## 功能详细

### 签到 { #signin }

指令 ： `逐鹿星河 签到` 或 `.Galaxy -Signin`

=== ":octicons-check-circle-fill-16: 使用成功效果"

    如图，如果神麟不存在服务异常或账号临时被风控的情况下，默认返回一张您的签到信息
    [![content.tabs.link success_signin]][content.tabs.link success_signin]

=== ":octicons-skip-16: 第一次使用效果"
    
    如图，如果您为第一次在某群使用签到，神麟会增加发送一条 ~~战犯~~ 星味很浓的提示。并且返回一张包含宣誓词的略有不同的签到信息
    [![content.tabs.link success_signin_firsttime]][content.tabs.link success_signin_firsttime]

  [content.tabs.link success_signin]: ../assets/images/success_signin.jpg
  [content.tabs.link success_signin_firsttime]: ../assets/images/success_signin_firsttime.jpg


### 我的信息 { #myinfo }

指令 ： `逐鹿星河 我的信息` 或 `.Galaxy -MyInfo`


=== ":octicons-check-circle-fill-16: 获取成功效果"

    如图，如果神麟不存在服务异常或账号临时被风控的情况下，默认返回一张您的账号信息
    [![content.tabs.link success]][content.tabs.link success]

=== ":octicons-skip-16: 获取失败效果"
    
    如图，如果您之前未在某群有账号记录，则会返回一条提示签到的信息
    [![content.tabs.link faild]][content.tabs.link faild]

  [content.tabs.link success]: ../assets/images/success_get_myinfo.jpg
  [content.tabs.link faild]: ../assets/images/faild_get_myinfo.jpg


### 排行 { #rank }

指令 ： `逐鹿星河 本星海排行 <参数>` 或 `.Galaxy -LocalRank <参数>`

参数可选：

1. 综合排名
2. 能量币排行
3. 合金排行
4. 凝聚力排行

默认空参等于 `综合排名`

=== ":octicons-check-circle-fill-16: 综合排名"

    如图，如果神麟不存在服务异常或账号临时被风控的情况下，默认返回一张所在群聊的综合排名
    
    综合排名使用 (能量币x10 + 合金x15000 + 凝聚力x5)/10000 的算法计算

    [![content.tabs.link comp]][content.tabs.link comp]

=== ":octicons-check-circle-fill-16: 合金排名"
    
    如图，如果神麟不存在服务异常或账号临时被风控的情况下，默认返回一张所在群聊的合金数量排名

    [![content.tabs.link alloys]][content.tabs.link alloys]

=== ":octicons-check-circle-fill-16: 能量币排名"
    
    如图，如果神麟不存在服务异常或账号临时被风控的情况下，默认返回一张所在群聊的能量币数量排名

    [![content.tabs.link energy]][content.tabs.link energy]

=== ":octicons-check-circle-fill-16: 凝聚力排名"
    
    如图，如果神麟不存在服务异常或账号临时被风控的情况下，默认返回一张所在群聊的凝聚力排名

    [![content.tabs.link ninjuli]][content.tabs.link ninjuli]

  [content.tabs.link comp]: ../assets/images/comp_rank.jpg
  [content.tabs.link alloys]: ../assets/images/alloys_rank.jpg
  [content.tabs.link energy]: ../assets/images/energy_rank.jpg
  [content.tabs.link ninjuli]: ../assets/images/ninjuli_rank.jpg


### 更新昵称 { #updatemyname }

指令 ： `逐鹿星河 更新名字` 或 `.Galaxy -ChangeMyInfo`


=== ":octicons-check-circle-fill-16: 更改成功"

    如图，如果神麟不存在服务异常或账号临时被风控的情况下，默认返回一张您的账号信息
    [![content.tabs.link success]][content.tabs.link success]

=== ":octicons-skip-16: 更改失败"
    
    如图，如果您之前未在某群有账号记录，则会返回一条提示签到的信息
    [![content.tabs.link faild]][content.tabs.link faild]

  [content.tabs.link success]: ../assets/images/success_changename.jpg
  [content.tabs.link faild]: ../assets/images/faild_changename.jpg


### 泛星系贸易市场 { #convert }

指令 ： `逐鹿星河 兑换 <参数>` 或 `.Galaxy -Convert <参数>`


=== ":octicons-check-circle-fill-16: 兑换合金成功"

    [![content.tabs.link success_alloys]][content.tabs.link success_alloys]

=== ":octicons-skip-16: 兑换合金失败"
    
    如能量币不足或账号不未注册
    [![content.tabs.link faild_alloys]][content.tabs.link faild_alloys]

  [content.tabs.link success_alloys]: ../assets/images/success_get_alloys.jpg
  [content.tabs.link faild_alloys]: ../assets/images/faild_get_alloys.jpg