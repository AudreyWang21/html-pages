# html-pages

[English](README.md) | [中文](README.zh-CN.md)

这是一个 [Claude Code](https://docs.claude.com/en/docs/claude-code) 技能，专门让 Claude 做 HTML 页面：概念讲解页、规划页、测验、小工具。怎么做，它有自己的一套主张。

它会把 Claude 往这几个方向推：

- **从内容出发设计。** 每个页面都从自己的信息出发去设计，不套固定模板，也不照搬别的页面。欢迎大胆尝试；最怕的是稳妥却千篇一律。
- **要导航，不要一滚到底。** 几个主题各占一个标签页或区域，刷新后停在原处。正文不限宽度，先照顾横屏。
- **可交互的讲解。** 交互顺着想法本身的结构来；测验带 "I don't know"（我不知道）选项；答案会保存；结果能导出，直接粘回 Claude 会话。
- **审查者。** 每个页面都要在真实浏览器里过一遍，其中一位审查者是对页面一无所知的"局外人"。

## 在线试玩样例

不用下载，在浏览器里直接打开：

- [模拟考试](https://audreywang21.github.io/html-pages/html-pages/references/Mock%20Exam%20Sample.html)：一份练习卷，带题目导航栏，答案自动保存，还能重新打乱。
- [搭建演化树](https://audreywang21.github.io/html-pages/html-pages/references/Tree%20Building%20Sample.html)：把动物类群拖到一起搭成一棵树，再给各个演化支命名。
- [拼写测试](https://audreywang21.github.io/html-pages/html-pages/references/Spelling%20Test%20Sample.html)：拼写练习，只重考你拼错的词。

## 安装

把 `html-pages/` 文件夹复制到 Claude Code 的技能文件夹：

```
~/.claude/skills/html-pages/
```

（Windows 上，`~` 就是你的用户文件夹。）只想在某个项目里用，就放进那个项目的 `.claude/skills/`。新开一个 Claude Code 会话，问 Claude 有哪些技能，列表里应该有 `html-pages`。之后 Claude 每次要写 HTML 页面都会自动加载它，你也可以点名让它用。

技能里提到另外几个技能（`artifact-design`、`artifact-diagramming`、`dataviz`、`frontend-design`）。这些都是可选的：你装了哪个，Claude 就加载哪个。Claude 能运行子 agent、驱动无头 Chrome（比如通过 Playwright）时，审查环节效果最好。

技能的中文译本在 `html-pages/SKILL.zh-CN.md`，供阅读参考。Claude 加载的是英文的 `SKILL.md`；想让它用中文版，把中文版改名为 `SKILL.md` 即可。

## 改成你自己的

`html-pages/SKILL.md` 开头附近有一小节 **Personal preferences**（个人偏好），写的是作者自己的语言习惯：拼写用加拿大英语；专业术语写英文，旁边附简体中文，再加国际音标。换成你自己的，或者干脆删掉。技能的其余部分也都是主张：不限宽度、横屏优先、每个做完的页面都在浏览器里打开、始终安排一位局外人审查。这些主张正是它的价值所在；不过这份是你自己的，哪里不合适就改哪里。

## 样例

`html-pages/references/` 里有三个能直接运行的页面。Claude 可以借用它们的行为，但要重做样式，不能照抄。在任何现代浏览器里双击就能打开。

- **Spelling Test Sample.html**：拼写练习，共十个英文单词，用中文意思做提示：输入英文单词，按 Enter。每一轮只重考拼错的词，结果表列出每个词错了几次。单词表可以换成你自己的。
- **Tree Building Sample.html**：拖放游戏。把十二个零散的类群搭成一棵入门生物学里的动物树，再给各个演化支（clade）命名。绿色对勾只说明这一组到目前为止和目标树对得上，不代表已经搭完。本技能说的"本身就是游戏的测验"，标杆就是它。
- **Mock Exam Sample.html**：入门生物学的选择题模拟考试，侧边有一条题目导航栏。本技能的各条测验规则，在这里都能看到实际效果："I don't know" 选项、刷新后不丢的答案、打乱顺序、可撤销的重置，以及错题导出。

`html-pages/references/image-sources/` 里还有一份注明日期的免费图片网站清单，agent 可以从中找真实照片（屏蔽 agent 的网站也单独列出），每个网站都附有用法。先从 [Image Sources](html-pages/references/image-sources/Image%20Sources.md) 看起。

## 许可证

MIT。详见 [LICENSE](LICENSE)。
