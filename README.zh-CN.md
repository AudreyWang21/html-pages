# html-pages

[English](README.md) | [中文](README.zh-CN.md)

一个 [Claude Code](https://docs.claude.com/en/docs/claude-code) 技能，用来做教学和讲解类的 HTML 页面，带着作者自己的偏好：每个页面按自己的内容来设计；用标签页，不一滚到底；交互顺着想法本身的结构来；测验会记住你的答案。

## 样例

不用下载，在浏览器里直接打开。它们放在 `html-pages/references/`，Claude 会借用其中的交互，再换一套样式。

- [模拟考试](https://audreywang21.github.io/html-pages/html-pages/references/Mock%20Exam%20Sample.html)：入门生物学选择题模拟考试，带题目导航栏、"I don't know" 选项、自动保存的答案、打乱顺序、可撤销的重置和错题导出。
- [搭建演化树](https://audreywang21.github.io/html-pages/html-pages/references/Tree%20Building%20Sample.html)：把十二个动物类群拖到一起搭成一棵树，再给各个演化支命名。本技能说的"本身就是游戏的测验"，标杆就是它。
- [拼写测试](https://audreywang21.github.io/html-pages/html-pages/references/Spelling%20Test%20Sample.html)：十个英文单词，用中文意思做提示；每一轮只重考拼错的词。

`html-pages/references/image-sources/` 里还有一份免费图片网站清单，agent 可以从中找真实照片，每个网站都附有用法。

## 安装

把 `html-pages/` 文件夹复制到 `~/.claude/skills/`，新开一个 Claude Code 会话即可。`SKILL.md` 里的 **Personal preferences**（个人偏好）一节是作者自己的习惯（加拿大拼写、术语中英对照），可以改掉或删掉。中文译本在 `html-pages/SKILL.zh-CN.md`，供阅读参考。

## 许可证

MIT。详见 [LICENSE](LICENSE)。
