# html-pages

[English](README.md) | [中文](README.zh-CN.md)

一个 [Claude Code](https://docs.claude.com/en/docs/claude-code) 技能（skill），对如何让 Claude 制作 HTML 页面有自己鲜明的主张：概念讲解页、规划页、测验、小工具。

它会推动 Claude 做到：

- **从内容出发设计。** 每个页面都从自身的信息向外设计，而不是套用固定模板或照搬其他页面。欢迎大胆的创意尝试；安全但千篇一律的页面，才是要避免的失败。
- **有导航，不要无尽滚动。** 多个主题各有自己的标签页或空间，刷新后回到原来的位置。正文不设宽度上限，优先适配横屏。
- **交互式讲解。** 交互贴合想法本身的形状；测验带 "I don't know"（我不知道）选项，答案会保存，还能导出结果，直接粘贴回 Claude 会话。
- **审查。** 每个页面都会在真实浏览器中接受检查，其中包括一位对页面一无所知的"局外人"审查者。

## 安装

把 `html-pages/` 文件夹复制到 Claude Code 的技能文件夹中：

```
~/.claude/skills/html-pages/
```

（在 Windows 上，`~` 指你的用户文件夹。）如果只想在某个项目中使用，就放到该项目的 `.claude/skills/` 下。开启一个新的 Claude Code 会话，问问 Claude 有哪些技能，列表里应该会出现 `html-pages`。此后每当 Claude 要写 HTML 页面时，它都会自动加载，你也可以直接点名调用。

技能中提到了其他几个技能（`artifact-design`、`artifact-diagramming`、`dataviz`、`frontend-design`）。它们都是可选的：你有哪个，Claude 就加载哪个。审查环节在 Claude 能运行子 agent 并驱动无头 Chrome（例如通过 Playwright）时效果最好。

技能的中文译本位于 `html-pages/SKILL.zh-CN.md`，供阅读参考。Claude 加载的是英文的 `SKILL.md`；如需让 Claude 使用中文版，可将其重命名为 `SKILL.md`。

## 改成你自己的

`html-pages/SKILL.md` 开头附近有一小节 **Personal preferences**（个人偏好），记录了作者自己的语言习惯：加拿大英语拼写，专业术语用英文并在旁边附上简体中文，外加国际音标。把它们换成你自己的，或者直接删掉。技能的其余部分同样是主张（不设宽度上限、横屏优先、每个完成的页面都在浏览器中打开、始终安排一位局外人审查者）。这些主张正是它的价值所在，但这是你自己的副本，不合适的地方尽管改。

## 样例

`html-pages/references/` 中有三个可运行的页面，Claude 可以借用其中的行为（并被要求重新设计样式，而不是照抄）。在任何现代浏览器中双击即可打开。

- **Spelling Test Sample.html**：一个拼写练习，包含十个英文单词，以中文释义作为提示：输入英文单词后按 Enter。每一轮只重考你拼错的词，结果表显示每个词错了几次。可以把单词表换成你自己的。
- **Tree Building Sample.html**：一个拖放游戏，把十二个零散的类群搭成一棵入门生物学的动物树，然后给各个演化支（clade）命名。绿色对勾表示某个分组到目前为止符合目标树，并不代表已经完成。本技能所说的"本身就是游戏的测验"，就以它为标杆。
- **Mock Exam Sample.html**：一份入门生物学的选择题模拟考试，侧边有一条题目导航栏。它展示了本技能各项测验规则的实际效果："I don't know" 选项、刷新后仍保留的答案、打乱顺序、可撤销的重置，以及错题导出。

`html-pages/references/image-sources/` 中还有一份注明日期的免费图片网站清单，供 agent 查找真实照片（也列出了屏蔽 agent 的网站），每个网站附有使用方法。可以从 [Image Sources](html-pages/references/image-sources/Image%20Sources.md) 开始看。

## 许可证

MIT。见 [LICENSE](LICENSE)。
