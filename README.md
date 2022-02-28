# bot使用说明

- [bot使用说明](#bot使用说明)
  - [引言](#引言)
  - [特殊插件](#特殊插件)
    - [nonebot_plugin_alias | 别名设置](#nonebot_plugin_alias--别名设置)
    - [nonebot_plugin_help | 帮助插件](#nonebot_plugin_help--帮助插件)
    - [nonebot_plugin_status | 服务器状态查看](#nonebot_plugin_status--服务器状态查看)
  - [指令插件](#指令插件)
    - [nonebot_plugin_abbrreply | 缩写查询](#nonebot_plugin_abbrreply--缩写查询)
    - [nonebot_plugin_asoulcnki | 枝网查重](#nonebot_plugin_asoulcnki--枝网查重)
    - [nonebot_plugin_code | 在线运行代码](#nonebot_plugin_code--在线运行代码)
    - [nonebot_plugin_covid19_news | 国内新冠消息查询](#nonebot_plugin_covid19_news--国内新冠消息查询)
    - [nonebot_plugin_fortune | 运势](#nonebot_plugin_fortune--运势)
    - [nonebot_plugin_gamedraw | 模拟抽卡](#nonebot_plugin_gamedraw--模拟抽卡)
    - [nonebot_plugin_morning | 早晚安](#nonebot_plugin_morning--早晚安)
    - [nonebot_plugin_read_60s | 观世界](#nonebot_plugin_read_60s--观世界)
    - [nonebot_plugin_roll | 掷色子](#nonebot_plugin_roll--掷色子)
    - [nonebot_plugin_translator | 翻译插件](#nonebot_plugin_translator--翻译插件)
    - [nonebot_plugin_weather_lite | 看天气](#nonebot_plugin_weather_lite--看天气)
    - [nonebot_plugin_what2eat | 吃什么](#nonebot_plugin_what2eat--吃什么)
    - [nonebot_plugin_word_bank2 | 问答插件](#nonebot_plugin_word_bank2--问答插件)
    - [nonebot_plugin_youthstudy | 青年大学习](#nonebot_plugin_youthstudy--青年大学习)
    - [random_cat_gif | 随机猫猫(加载很慢，慎用）](#random_cat_gif--随机猫猫加载很慢慎用)
  - [@指令插件(需要@机器人才能触发)](#指令插件需要机器人才能触发)
    - [nonebot_plugin_caiyunai | 彩云小梦AI续写](#nonebot_plugin_caiyunai--彩云小梦ai续写)
    - [nonebot_plugin_chess | 棋类游戏](#nonebot_plugin_chess--棋类游戏)
    - [nonebot_plugin_remake | 人生重开模拟器](#nonebot_plugin_remake--人生重开模拟器)
    - [nonebot_plugin_withdraw | 撤回插件](#nonebot_plugin_withdraw--撤回插件)
    - [haruka_bot | B站推送](#haruka_bot--b站推送)
  - [非指令插件（无需前缀指令）](#非指令插件无需前缀指令)
    - [nonebot_plugin_analysis_bilibili |bilibili视频、番剧解析](#nonebot_plugin_analysis_bilibili-bilibili视频番剧解析)
    - [nonebot_plugin_emojimix | emoji 合成器](#nonebot_plugin_emojimix--emoji-合成器)
    - [nonebot_plugin_repeater | 复读插件](#nonebot_plugin_repeater--复读插件)
  - [无用插件（仅提供编写机器人代码支持）](#无用插件仅提供编写机器人代码支持)
    - [nonebot_plugin_apscheduler](#nonebot_plugin_apscheduler)
    - [nonebot_plugin_htmlrender](#nonebot_plugin_htmlrender)

## 引言

一个基于Nonebot搭建的bot，功能基本全是大佬们的现成插件（少数进行了改动），只是出于兴趣，跟着大佬搭建的，但是搭了没人用就很尴尬，所以拿出来让有兴趣的用用，但是如果没人会用也很尴尬，就写了这个使用说明。

如果对这个使用说明有什么建议，请联系我。

bug很多很经常，如果发现请联系我，请轻喷（

------



## 特殊插件

### nonebot_plugin_alias | 别名设置 

- `alias [别名]=[指令名称]` 添加别名
- `alias [别名]` 查看别名
- `alias -p` 查看所有别名
- `unalias [别名]` 删除别名
- `unalias -a` 删除所有别名

默认只在当前群聊/私聊中生效，使用 `-g` 参数添加全局别名；增删全局别名需要超级用户权限

- `alias -g [别名]=[指令名称]` 添加全局别名

- `unalias -g [别名]` 删除全局别名

传入参数

可以用 bash shell 的风格在别名中使用参数，如：`alias test="echo $1"`

`$1` 表示第一个参数，以此类推；`$a` 表示所有参数

**当创建别名的命令中包含 `$` 符号时，即认为使用了参数。**

**此时，别名之后的内容会以参数方式解析，而不仅仅是替换别名**

使用 [expandvars](https://github.com/sayanarijit/expandvars) 来解析参数，可实现参数默认值、切片等功能：

- `alias test="echo ${1:-default}"`
- `alias test="echo ${1:0:4}"`

### nonebot_plugin_help | 帮助插件

`help`获取本插件帮助

`help list/ls`查看已加载插件列表

`help [插件名]/插件中文名`查看已加载某一插件用途

### nonebot_plugin_status | 服务器状态查看 

`戳一戳机器人` 查看服务器状态

------



## 指令插件

### nonebot_plugin_abbrreply | 缩写查询 

- `缩写/sx [想查询的缩写] ` 查询缩写

### nonebot_plugin_asoulcnki | 枝网查重 

- `小作文/随机小作文`
- `查重/枝网查重 [要查重的小作文]`
- `回复需要查重的内容，回复“查重”`

### nonebot_plugin_code | 在线运行代码 

```
code [语言] [-i] [inputText]
[代码]
```

语言：c/cpp/c#/py/php/go/java/js

-i：可选 输入 后跟输入内容

```
运行代码示例(python)(无输入)：
    code py
        print("sb")
运行代码示例(python)(有输入)：
    code py -i 你好
        print(input())
```

### nonebot_plugin_covid19_news | 国内新冠消息查询 

`城市名 + 疫情` 查询地方疫情信息（风险等级 新增 目前确诊）
`城市名 + 疫情政策` 查询地方出入政策
`城市名 + 风险地区` 查询城市风险地区（只限查询大陆地级市或直辖市）
`关注疫情 + 城市名` 疫情信息更新推送
`取消疫情 + 城市名` / `取消关注疫情 + 城市名` / `取消推送疫情 + 城市名` 取消推送

### nonebot_plugin_fortune | 运势 

`今日运势/抽签/运势`一般抽签

`指定[xxx]签`指定签底并抽签

`抽签设置`查看当前群抽签主题的配置；

`今日运势帮助`显示插件帮助文案；

`主题列表`显示当前已启用主题；

[群管或群主或超管] 

- `设置[原神/pcr/东方/vtb/xxx]签`设置群抽签主题；
- `重置抽签`设置群抽签主题为随机；

[超管] 

`刷新抽签`即刻刷新抽签，防止过0点未刷新的意外；

### nonebot_plugin_gamedraw | 模拟抽卡

抽卡命令

```
' .* ?方舟[1-9|一][0-9]{0,2}[抽|井]'
' .* ?原神(武器|角色)?池?[1-9|一][0-9]{0,2}[抽|井]'
' .* ?马娘卡?[1-9|一][0-9]{0,2}[抽|井]'
' .* ?坎公骑冠剑武?器?[1-9|一][0-9]{0,2}[抽|井]'
' .* ?(pcr|公主连结|公主连接|公主链接|公主焊接)[1-9|一][0-9]{0,2}[抽|井]'
' .* ?碧蓝航?线?(轻型|重型|特型)池?[1-9|一][0-9]{0,2}[抽]'
' .* ?fgo[1-9|一][0-9]{0,2}[抽]'
' .* ?阴阳师[1-9|一][0-9]{0,2}[抽]'
```



注（特别抽卡命令详解）

1.**原神**（当武器和角色无UP池时，所有抽卡命令都指向 '常驻池'）

- `原神N抽` （常驻池）
- `原神角色N抽` （角色UP池）
- `原神武器N抽` （武器UP池）

2.**赛马娘**

- `赛马娘N抽` （抽马）
- `赛马娘卡N抽` （抽卡）

3.**坎公骑冠剑**

- `坎公骑冠剑N抽` （抽角色）
- `坎公骑冠剑武器N抽` （抽武器）

4.**碧蓝航线**

- `碧蓝轻型N抽` （轻型池）
- `碧蓝重型N抽` （重型池）
- `碧蓝特型N抽` （特型池）

其他命令

```
'重置原神抽卡'（重置保底）
'重载原神卡池'
'重载方舟卡池'
'重载赛马娘卡池'
'重载坎公骑冠剑卡池
```

更新命令

```
'更新明日方舟信息'
'更新原神信息'
'更新赛马娘信息'
'更新赛坎公骑冠剑信息'
'更新pcr信息'
'更新碧蓝航线信息'
'更新fgo信息'
'更新阴阳师信息'
```

### nonebot_plugin_morning | 早晚安 

`早安/晚安`早晚安，记录睡眠时间；

`我的作息`查看我的作息

`群友作息`查看群友作息，看看今天几个人睡觉或起床了

`早晚安设置`查看配置当前安晚安规则

[群管或群主或超管] 设置命令

-  `早安/晚安开启/关闭某项功能`开启/关闭某个配置：
- `设置功能的参数`早安/晚安设置
- 详见规则配置；

### nonebot_plugin_read_60s | 观世界 

`看世界/60s看世界`发送60s看世界图片

每天早上9点自动发送，如需开启，请联系QQ：877067309

### nonebot_plugin_roll | 掷色子 

`rd、掷骰，后接“[x]d[y]”， x指定个数，y指骰子面数。`掷色子，仅提供总点数

### nonebot_plugin_translator | 翻译插件 

`翻译/机翻` 根据提示使用翻译

### nonebot_plugin_weather_lite | 看天气 

命令：

注：1.以下`天气`命令均可以使用`wttr`、`weather`、`tianqi`等效替代,

 2.`城市名`可以使用各种语言，例如`Beijing`、`Peking`、`北京`是等效的。

 3.支持查询全球各种地区。例如莫斯科什么的都可以。

基础：

`天气 城市名`查询城市天气

`天气 城市名_format=v2/v3`高级查询

`天气 城市名_lang=语言` 指定语言

语言可选于：

> ```
> am ar af be bn ca da de el et fr fa hi hu ia id it lt mg nb nl oc pl pt-br ro ru ta tr th uk vi zh-cn zh-tw
> ```

```
例如俄文查询北京：

天气 北京_lang=ru
```

多格式联动:

```
使用v2格式、俄文来查询北京：

`天气 北京_format=v2_lang=ru
```

`天气 Moon` 查看月相

### nonebot_plugin_what2eat | 吃什么 

`今天吃什么、中午吃啥、今晚吃啥、中午吃什么、晚上吃啥、晚上吃什么、夜宵吃啥……`吃什么

`菜单/群菜单/查看菜单`查看群菜单

[管理或群主或超管] 

`添加/移除 菜名`添加或移除

[超管]

 `加菜 菜名`添加至基础菜单

`基础菜单` 查看基础菜单

 `开启/关闭小助手添加或移除` 开启/关闭按时吃饭小助手，如需开启，请联系QQ：877067309

### nonebot_plugin_word_bank2 | 问答插件 

问答教学

- 设置词条命令由`问句`和`答句`组成。设置之后, 收到`消息`时触发。并非所有人都可以设置词条, 详见[权限](https://github.com/kexue-z/nonebot-plugin-word-bank2#permission)

- 格式`[模糊|全局|正则|@]问...答...`

  - `模糊|正则` 匹配模式中可任性一个或`不选`, `不选` 表示 `全匹配`
  - `全局`, `@` 可与以上匹配模式组合使用

- 教学中可以使用换行

  - 例如

    ```
    问
    123
    答
    456
    ```

- 问答句中的首首尾空白字符会被自动忽略

- 私聊好友个人也可以建立属于自己的词库, 可以实现类似备忘录的功能

问句选项

- `问...答...` 全匹配模式, 必须全等才能触发答

- `模糊问...答...` 当`问句`出现在`消息`里时则会触发

- `正则问...答...`, 当`问句`被`消息`正则捕获时则会匹配

- 例如: 正则问[他你]不理答你被屏蔽了

  | 消息     | 回复       |
  | -------- | ---------- |
  | 他不理   | 你被屏蔽了 |
  | 他不理我 | 你被屏蔽了 |
  | 你不理我 | 你被屏蔽了 |

- `全局问...答...`, 在所有群聊和私聊中都可以触发, 可以和以上几种组合使用

  - 例如: `全局模糊问 晚安 答 不准睡`

- `@问...答...`, 只有 `event.tome` 时才会触发，如被@、被回复时或在私聊中，可以和以上几种组合使用

  - 例如: `全局模糊@问 晚安 答 不准睡`

- 问句可包含`at` 即在QQ聊天中手动at群友

  - 建议只在`问...答...`中使用
  - 例如: `问 @这是群名称 答 老婆!`

答句选项

- `/at` + `qq号`, 当答句中包含`/at` + `qq号`时将会被替换为@某人
  - 例如: `问 群主在吗 答 /at 123456789在吗`
- `/self`, 当答句中包含`/self`时将会被替换为发送者的群昵称
  - 例如: `问 我是谁 答 你是/self` (群昵称为: 我老婆)
- `/atself`, 当答句中包含`/atself`时将会被替换为@发送者
  - 例如: `问 谁是牛头人 答 @这是群昵称`

删除词条

- `删除[模糊|全局|正则|@]词条` + 需要删除的`问句`
  - 例如: `删除全局模糊@词条 你好`
- 以下指令需要结合自己的`COMMAND_START` 这里为 `/`
- 删除词库: 删除当前群聊/私聊词库
  - 例如: `/删除词库`
- 删除全局词库
  - 例如: `/删除全局词库`
- 删除全部词库
  - 例如: `/删除全部词库`
- 权限

|              | 群主 | 群管理 | 私聊好友 | 超级用户 |
| ------------ | ---- | ------ | -------- | -------- |
| 增删词条     | O    | O      | O        | O        |
| 增删全局词条 | X    | X      | X        | O        |
| 删除词库     | O    | O      | O        | O        |
| 删除全局词库 | X    | X      | X        | O        |
| 删除全部词库 | X    | X      | X        | O        |

### nonebot_plugin_youthstudy | 青年大学习 

`“青年大学习”或者“大学习”` 获取最新一期的青年大学习答案

### random_cat_gif | 随机猫猫(加载很慢，慎用） 

`来个猫猫`随机猫猫gif

------



## @指令插件(需要@机器人才能触发)

### nonebot_plugin_caiyunai | 彩云小梦AI续写

`@机器人 续写/彩云小梦 [内容]`

### nonebot_plugin_chess | 棋类游戏 

`@机器人 围棋 或 五子棋 或 黑白棋 或者 chess --rule <rule> [--size <size>]` 开始一个对应的棋局，一个群组内同时只能有一个棋局。



| 快捷名          | 规则名  | 默认大小 |
| --------------- | ------- | -------- |
| 围棋            | go      | 19       |
| 五子棋          | gomoku  | 15       |
| 黑白棋 / 奥赛罗 | othello | 8        |

`停止下棋 或者 chess --stop` 可以停止一个正在进行的棋局。

落子，悔棋和跳过

 `落子 position 如 落子 A1 或者 chess position` 进行下棋。

当棋局开始时，第一个落子的人为先手，第二个落子的人为后手，此时棋局正式形成，其他人无法继续加入游戏。而参与游戏的两人可以依次使用“落子”指令进行游戏。

 `悔棋 或者 chess --repent` 进行悔棋，游戏会向前倒退一步。

 `跳过回合 或者 chess --skip` 跳过一个回合。

`查看棋局 或者 chess --view` 查看当前棋局。


### nonebot_plugin_remake | 人生重开模拟器 

`@机器人 remake/liferestart/人生重开/人生重来 ` 开始人生重开模拟器 

### nonebot_plugin_withdraw | 撤回插件 

方式1：

```
@机器人 撤回 [num]
```

`num`指机器人发的倒数第几条消息，从0开始，默认为0

`num`不需要加`[]`，仅为了说明是可选参数，如：

```
@机器人 撤回    # 撤回最近一条消息
@机器人 撤回 1    # 撤回倒数第二条消息
```

方式2：

`回复需要撤回的消息，回复“撤回”`

### haruka_bot | B站推送

注意

群里使用命令前**需要** @机器人，如 `@HarukaBot 帮助`。



`主播列表`获取**当前位置**（群聊/私聊）订阅的所有主播信息，以及相对应的各类推送信息的开关情况。



`开启权限 | 关闭权限`每个群一开始都**默认**为**开启权限**状态。

注意

即使关闭权限，普通群员也**无法使用** 开启权限、关闭权限、开启全体、关闭全体。

`开启权限` 后，当前群内只有群主、管理员、和机器人主人（superuser）可以使用 HarukaBot。

`关闭权限` 后，所有人都可以使用 HaurkaBot。



`添加主播 | 删除主播 UID`**默认**会开启直播推送和动态推送

注意

每个群聊、私聊的推送列表都是相互独立的。你在任何位置的添加、删除以及其他修改操作都**不会影响**到其他位置的推送。

在**当前位置**（群聊/私聊）添加或删除一位主播。

`添加主播` 后，在该主播开播、更新动态、发布视频时均会在**添加的位置**收到推送消息。

`删除主播` 后，将不会在**当前位置**（群聊/私聊）继续推送。



`开启动态 | 关闭动态 [UID]`新添加的主播**默认开启**动态推送。

注意

`开启动态` 后，会在**当前位置**（群聊/私聊）推送主播新发的动态。

`关闭动态` 后，将不会在**当前位置**（群聊/私聊）继续推送。



`开启直播 | 关闭直播 [UID] `新添加的主播**默认开启**直播推送。

注意

`开启直播` 后，会在**当前位置**（群聊/私聊）推送主播的开播提醒。

`关闭直播` 后，将不会在**当前位置**（群聊/私聊）继续推送。



`开启全体 | 关闭全体 [UID]`新添加的主播**默认**关闭全体。

注意

`开启全体` 后，机器人将会在该主播的开播提醒消息前 @全体成员。

`关闭推送` 后，则不会 @全体成员。

一个 QQ号 一天只能 @全体成员 十次。这个次数**所有群**共享，不是每个群一天十次。开通会员可以提高次数上限。

------



## 非指令插件（无需前缀指令）

### nonebot_plugin_analysis_bilibili |bilibili视频、番剧解析

`私聊或群聊发送bilibili的小程序/链接`

### nonebot_plugin_emojimix | emoji 合成器

`emoji表情+emoji表情`

示例：

![img](https://camo.githubusercontent.com/27618e810ef63cf979791ecf8c3d41bb81f00cddfbf03a95031a3834d7ec2079/68747470733a2f2f73322e6c6f6c692e6e65742f323032322f30312f32332f45796f41314248653959704a5a55442e706e67)

### nonebot_plugin_repeater | 复读插件

复读+1 若需开启请联系QQ：877067309

------



## 无用插件（仅提供编写机器人代码支持）

### nonebot_plugin_apscheduler

###  nonebot_plugin_htmlrender 

[^备注]: author：方任斌   qq：877067309



