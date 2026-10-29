# project-workspace-setup

一个 Claude skill：帮你把一项长期工作搭建成新版 Claude 项目（Projects：一个协调器 + 多个讨论串），并设计好之后怎么维护。适用于团队项目管理、日常生活管理、求职等。

内容来自真实实践，每次实践后都会更新。目前已实践的场景：大学 5 人团队项目（用户担任 PM）。

> 新版 Claude 项目在 2026 年 10 月仍是公开测试版，按钮、限制和默认值可能会变。skill 会要求 Claude 先对照[官方文档](https://code.claude.com/docs/en/claude-projects.md)核对。

## 它能帮你做什么

- 问清你的需求，设计项目里放哪些文件、项目记忆放什么、哪些留在外部系统
- 交叉核对你准备的文件：编号撞车、和已定决策冲突、过时内容、重复内容
- 写项目指令、初始化项目记忆、开长期讨论串并试运行
- 设计每天、每周、阶段结束的维护流程
- 提供一套可以直接复制的提示词

## 核心思路

- **对话是工作台，文件才是记忆**：要长期保留的东西，都写进项目记忆或 Library 文件
- **按变化频率存放**：基本不变的放 Library；经常变的放项目记忆；每天都在变的留在外部系统（GitHub Issues、日历、表格）
- **同一个事实只放一处**，冲突时以《决策记录》为准
- **你不亲手改文件**：让负责的讨论串改好，你只负责确认和上传

完整内容见 [`project-workspace-setup/SKILL.md`](project-workspace-setup/SKILL.md)。

## 文件结构

```
project-workspace-setup/          skill 本体（打包时压缩这个文件夹）
├── SKILL.md                      核心原则和 7 步搭建流程
├── references/                   用到某一步时才读
│   ├── product-facts.md          产品事实（标注官方 / 观察和核对日期）
│   ├── file-design.md            文件和记忆的设计
│   ├── maintenance.md            日常与定期维护
│   ├── pitfalls.md               踩过的坑
│   └── scenarios/                各场景的参考（团队项目已实践，其余待实践）
└── assets/                       可以直接复制的模板
    ├── project-instructions.md   项目指令模板
    ├── file-templates.md         各文件骨架
    └── prompts.md                常用提示词
practice-logs/                    每次实践的复盘记录（已匿名化，不打包进 skill）
CHANGELOG.md                      版本记录
project-workspace-setup.zip       打包好的 skill，可以直接上传
```

## 安装

**claude.ai / 桌面端**

1. 下载仓库根目录的 `project-workspace-setup.zip`，或者自己打包：在仓库根目录运行 `zip -r project-workspace-setup.zip project-workspace-setup/`。注意不要用 GitHub 的"Download ZIP"，那样打出来的结构不对
2. 打开 [Customize → Skills](https://claude.ai/customize/skills)，上传 ZIP，并打开这个 skill
3. 在新对话里说"帮我搭一个 Claude 项目来管理……"试试

**Claude Code**

把 `project-workspace-setup/` 文件夹复制到 `~/.claude/skills/`。

## 怎么改进

每次用它搭完一个项目、运行一段时间后：

1. 用 `assets/prompts.md` 里的"让协调器复盘"提示词收集经验
2. 复盘原文去掉个人信息后，放进 `practice-logs/`
3. 把能通用的经验更新进 `references/`
4. 在 `CHANGELOG.md` 里记一笔
5. 重新打包 `project-workspace-setup.zip`

## 许可

[MIT](LICENSE)：可以自由使用、修改和分发，保留版权声明即可。
