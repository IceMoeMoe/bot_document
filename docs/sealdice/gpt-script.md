# GPTScript 说明文档

如何使用 GPTScript，怎么更好地使用 GPTScript

## 这插件是干啥的？

很简单，用来让你的机器人连接上 https://openrouter.ai 提供的GPT模型，然后通过指令调用机器人就可以对话了

### 用法

```sh
.chat_bot <消息>
```
其中，消息可以为文本或图片，或者文本+图片

### 示例

.chat_bot 我饿了


### 插件选项

首先是黑白名单。黑白名单在sealdice的webui中设置，在插件选项里

而关于其他设置，你可以打开.js文件来编辑其中的内容

#### 参数

`chat_bot`：你可以一键替换所有该文本为你想要的指令。例如“聊天”或者“chat”

`const OPENROUTER_API_KEY = 'your-api-key'`：显然，你应该把`your-api-key`替换成你从网站获得的api key。这是所有操作的大前提

`if (this.context.length > 12) `：你可以在这里控制上下文的最大轮数。12是指最多保留5轮上下文，也就是保留用户的前5条信息

`model: "openai/gpt-4o-mini"`：你可以修改冒号后面的内容来修改你使用的模型类型。这里推荐就用这个

`max_tokens: 1000`：返回的最大token。如果你不想用户用一个“唐”字就烧掉你三四千token，那么最好把它设置成200,500，或者1000。这三个都是可接受的

`seal.replyToSender(ctx, msg, cqc+res);`cqc是用于实现“回复”效果的CQ码。如果你不希望机器人在回复的时候携带“回复”功能，那么就删掉"cqc+"这几个字符

### 结果

#### 示例输出

<chat-panel>
  <chat-message nickname="Alice">.chat_bot 我饿了！</chat-message>
  <chat-message nickname="海豹核心">没问题！我会为你生成一些菜谱，你可以根据菜谱来进行烹饪：...一大堆菜谱</chat-message>
</chat-panel>

## 更多

保存好你的APIKEY，不要弄丢，也不要发给别人，除非你真觉得TA是可信的。但总之，我不会为你弄丢APIKEY导致的问题提供任何帮助
