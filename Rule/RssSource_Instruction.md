## Legado订阅源规则说明
更新时间：2024-02-27
### 概况

  - 1、语法说明
  - 2、Legado的特殊规则
  - 3、解析流程
  - 4、规则概述
  - 5、附录

------

### 1、语法说明 (已404)
  + 详见[书源规则](https://alanskycn.gitee.io/teachme/)

### 2、Legado的特殊规则 (已404)
  + 详见[书源规则](https://alanskycn.gitee.io/teachme/)

### 3、解析流程

- 订阅源的解析

  1. 访问`源URL(sourceUrl)`

  2. 检查是否存在`列表规则(ruleArticles)`

     若为空，则认为是标准RSS源，采用默认规则解析。否则，请看第3点。

  3. 解析`列表规则(ruleArticles)`

     返回一个列表，`列表下一页规则(ruleArticles)`只在上拉时触发，且不存在页数`{{page}}`

  4. 解析`标题规则(ruleTitle)`、`时间规则(rulePubDate)`、`图片url规则(ruleImage)`、`链接规则(ruleLink)`和`链接规则(ruleLink)`

  5. 检查是否存在`描述规则(ruleDescription)`

     若存在，则解析`描述规则(ruleDescription)`，到这里就解析结束。否则，请看第6点。

  6. 检查是否存在`内容规则(ruleContent)`

     若存在，则解析`内容规则(ruleContent)`，然后结束解析。否则，直接结束解析。

- 根据订阅源的解析，可以发现订阅源有三种：标准RSS源、有列表规则和描述规则的源以及有列表规则无描述规则的源。	

  ▲ 标准RSS源
    - 特征：只填写了`源名称(sourceName)`、`源URL(sourceUrl)`。
    - `图标(sourceIcon)`和`源分组(sourceGroup)`可有可无，不影响解析。

  ▲ 有列表规则和描述规则的源
    - 特征：一定填写了`源名称(sourceName)`、`源URL(sourceUrl)`、`列表规则(ruleArticles)`、`标题规则(ruleTitle)`、`描述规则(ruleDescription)`和`链接规则(ruleLink)`。
    - `列表下一页规则(ruleArticles)`根据实际需求来填写，不填也可以。`图标(sourceIcon)`和`源分组(sourceGroup)`可有可无，不影响解析。

  ▲ 有列表规则无描述规则的源
    - 特征：一定填写了`源名称(sourceName)`、`源URL(sourceUrl)`、`列表规则(ruleArticles)`、`标题规则(ruleTitle)`和`链接规则(ruleLink)`。
    - `列表下一页规则(ruleArticles)`和`内容规则(ruleContent)`根据实际需求来填写，不填也可以。`图标(sourceIcon)`和`源分组(sourceGroup)`可有可无，不影响解析。

### 4、规则概述

  + 源URL(sourceUrl)
    - 必填
    - 唯一标识，不可重复
    - 与其他源相同会覆盖
  + 源名称(sourceName)
    - 必填
    - 名字可重复
+ 图标(sourceIcon)
    - 可不填
+ 源分组(sourceGroup)
    - 可不填
+ 列表规则(ruleArticles)
    - 根据实际需求填写
    - 判断是否是标准RSS的标志
+ 列表下一页规则(ruleArticles)
    - 根据实际需求填写，一般和`列表规则(ruleArticles)`一起搭配使用
    - 规则解析的结果必须是字符串
    - 无页数`{{page}}`，想实现页数加一请使用JS
+ 标题规则(ruleTitle)
    - 填写`列表规则(ruleArticles)`后，为必填项
+ 时间规则(rulePubDate)
    - 可不填，根据实际需求填写
+ 描述规则(ruleDescription)
    - 根据实际需求填写
    - 区分`有列表规则和描述规则的源`和`有列表规则无描述规则的源`的标志
+ 图片url规则(ruleImage)
    - 可不填，根据实际需求填写
+ 链接规则(ruleLink)
    - 填写`列表规则(ruleArticles)`后，为必填项
    - 文章的唯一标识
+ 内容规则(ruleContent)
    - 根据实际需求填写，不填打开网页，填写可修改样式
+ 请求头(header)
    - 根据实际需求填写

### 5、附录

- 订阅源

  ```
  {
      "customOrder": 0,
      "enableJs": true,
      "enabled": true,
      "loadWithBaseUrl": true,
      "ruleArticles": "$.list[*]",
      "ruleContent": "<js>result</js>",
      "ruleImage": "$.pic",
      "ruleLink": "$.url",
      "rulePubDate": "$.time",
      "ruleTitle": "$.title",
      "sourceGroup": "VIP",
      "sourceIcon": "https://gitee.com/alanskycn/yuedu/raw/master/JS/icon.jpg",
      "sourceName": "阅读3.0",
      "sourceUrl": "https://gitee.com/alanskycn/yuedu/raw/master/JS/RSS/custom/customRss.json"
  }
  ```

[
    {
    "articleStyle": 0,
    "customOrder": -24967,
    "enableJs": true,
    "enabled": true,
    "enabledCookieJar": false,
    "header": "{\n\"User-Agent\": \"Mozilla/5.0 (Linux; U; Android 8.1.0; zh-CN; MI 8 Lite Build/OPM1.171019.019) AppleWebKit/537.36 (KHTML, like Gecko) Version/4.0 Chrome/78.0.3904.108 UCBrowser/13.2.0.1100 Mobile Safari/537.36\"\n}",
    "lastUpdateTime": 1675946926480,
    "loadWithBaseUrl": true,
    "ruleArticles": "id.content@h3",
    "ruleLink": "a@href",
    "ruleTitle": "a@textNodes",
    "singleUrl": true,
    "sortUrl": "首页::http://yuedu.miaogongzi.net/gx.html",
    "sourceGroup": "书源",
    "sourceIcon": "https://i.loli.net/2021/06/23/S7rvWRZtPIq34MJ.png",
    "sourceName": "喵公子书源管理",
    "sourceUrl": "http://yuedu.miaogongzi.net/gx.html"
}
]