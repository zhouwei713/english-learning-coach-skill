<div align="center">

# English Learning Coach

**面向英语练习、雅思备考、可视化课程、TTS 和学习记录的自适应 Agent Skill**

![License](https://img.shields.io/badge/License-MIT-yellow)
![Platform](https://img.shields.io/badge/Platform-Codex-1d5fd1)
![Skill](https://img.shields.io/badge/Skill-english--learning--coach-0f8f83)
![IELTS](https://img.shields.io/badge/IELTS-Ready-e85d4f)
![TTS](https://img.shields.io/badge/TTS-Browser%20%7C%20edge--tts-e8b448)

把模糊的英语学习需求转成清晰练习、真实反馈和可复用学习记录。

[English README](README.md)

</div>

## 这是什么

English Learning Coach 是一个 Codex Skill，用来让 Agent 像自适应英语教练一样工作。

它会先理解学习者是谁，再选择合适的练习方式。它可以服务小学三年级孩子学动物单词，也可以服务雅思考生练 Speaking Part 2，还可以帮助成人修改职场邮件。

它的核心目标是把英语学习变成一次可以真正完成的练习：

1. 只问启动练习所需的信息。
2. 生成聚焦任务。
3. 给出真实反馈。
4. 生成学习记录。
5. 询问是否保存学习进度。

## 主要能力

### 自适应分流

Skill 会根据学习者类型进入不同模式：

| 学习者 | 典型支持 |
| --- | --- |
| 幼儿 | 英语启蒙、图片词汇、模仿、亲子练习 |
| 小学生 | 自然拼读、词汇、句子搭建、简单 HTML 页面 |
| 初中生 | 语法、阅读、听力、写作、校内考试题型 |
| 高中生 | 考试策略、阅读、完形、语法填空、写作 |
| 大学生 | 四六级风格练习、口语、学术阅读、面试 |
| 雅思或托福备考者 | 计时练习、评分标准、模拟评分、弱项训练 |
| 职场学习者 | 邮件、会议、汇报、面试、谈判 |
| 自学者 | 美剧、播客、新闻、小说、论文、用户材料 |

### 材料转练习

用户粘贴材料后，Skill 可以转成对应练习：

1. 英文文章转成分级阅读和复述任务。
2. 字幕转成听力、跟读和表达积累任务。
3. 邮件转成语气优化和回复草稿。
4. 作文和口语稿转成批改和模拟反馈。
5. 试题转成题型分析和复练任务。
6. 单词表转成记忆计划、例句和测验。

### 可视化 HTML 练习页

Skill 可以生成独立 HTML 页面，让练习更直观。

适合场景：

1. 小学三年级动物词汇练习页。
2. 雅思计时练习页。
3. 自然拼读练习页。
4. 职场邮件或会议表达练习页。

### TTS 朗读

可视化课程可以加入多种朗读方案：

| 方案 | 适合场景 | 注意事项 |
| --- | --- | --- |
| 浏览器内置朗读 | 互动式 HTML 页面 | 建议用 Microsoft Edge |
| edge-tts | 固定 mp3 课程音频 | 适合完整音频包 |
| Azure AI Speech | 产品化高质量音频 | 需要用户提供凭证 |
| Amazon Polly | AWS 批量音频 | 需要用户提供凭证 |

多数互动课程更适合浏览器内置朗读。它可以用于单词卡、句型练习、小测验题目和示范回答。

如果是可复用课程包，也可以提前生成 mp3 音频并附加到页面中。

### 真实反馈

反馈会尽量贴近真实学习任务。

雅思和托福练习会围绕任务要求、表达清晰度、结构、词汇、语法和下一步提分动作给出建议。

低龄学习者的反馈更简单、更鼓励。备考场景的反馈更严格，也更接近评分标准。

典型反馈包括：

1. 做得好的地方。
2. 影响理解或提分的问题。
3. 更好的表达版本或复练任务。

### 学习记录

一次练习结束后，Skill 可以输出这样的学习记录：

```text
学习者类型：雅思备考者
当前目标：口语 7.0
最近训练：Speaking Part 2
主要薄弱点：例子不够具体
学习偏好：计时任务、示范答案、Edge 浏览器 TTS
下次任务：用更具体的例子复练同一张 cue card
```

这份记录可以在后续学习中继续使用，避免每次都从零开始。

## 快速开始

把本文件夹安装到 Codex skills 目录：

```text
~/.codex/skills/english-learning-coach
```

重启 Codex 后使用：

```text
Use $english-learning-coach to start a focused English practice session.
```

## 示例提示词

### 小学生练习

```text
Use $english-learning-coach. Create a 10 minute English practice page for a Grade 3 student learning animal words.
```

### 雅思口语

```text
Use $english-learning-coach. I am preparing for IELTS Speaking. My target is Band 7.0. Practice Part 2 with me for 15 minutes.
```

### 雅思写作

```text
Use $english-learning-coach. Correct this IELTS Task 2 essay and give simulated band feedback.
```

### 职场英语

```text
Use $english-learning-coach. Help me rewrite this English email so it sounds professional but friendly.
```

### 材料转课程

```text
Use $english-learning-coach. Turn this English article into a reading lesson for an intermediate learner.
```

## 一次练习怎么开始

如果用户没有提供足够上下文，Skill 会默认问 5 个问题：

1. 学习者是谁？
2. 学习目标是什么？
3. 当前水平如何？
4. 今天有多少时间？
5. 想练什么内容，或者是否有材料？

然后它会选择练习模式并开始任务。

儿童练习通常优先生成直观 HTML 活动。

雅思、托福、大学和职场场景通常使用更克制的任务界面，重点放在计时练习和具体反馈。

## 音频选项

基础 Skill 不需要音频依赖。

当需要发音、听力或跟读训练时，可以再加入朗读能力。

### 浏览器朗读

无需安装。

建议用 Microsoft Edge 打开生成的 HTML 页面，发声最稳定。Chrome 或其他浏览器在部分系统上可能缺少 voice，或者无法发声。

### edge-tts

如果需要固定 mp3 课程包，可以在本地使用 `edge-tts`：

```bash
python -m pip install edge-tts
```

检查 voice：

```bash
python -m edge_tts --list-voices
```

生成音频：

```bash
python -m edge_tts --voice en-US-JennyNeural --rate=-10% --text "I like rabbits." --write-media i-like-rabbits.mp3
```

动态课程通常更适合浏览器朗读。

### Azure AI Speech 和 Amazon Polly

云端 TTS 适合产品化音色、稳定发音和更大的课程库。

这些服务需要凭证，凭证应保存在公开课程文件之外。

## 安装文件

```text
english-learning-coach/
  SKILL.md
  README.md
  README.zh-CN.md
  LICENSE
  agents/
    openai.yaml
  references/
    learning-loops.md
    skill-training-modes.md
    vocabulary-system.md
```

## 校验

使用下面命令校验 Skill 结构：

```bash
python C:/Users/Admin/.codex/skills/.system/skill-creator/scripts/quick_validate.py path/to/english-learning-coach
```

预期结果：

```text
Skill is valid!
```

## License

MIT
