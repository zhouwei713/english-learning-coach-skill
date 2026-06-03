<div align="center">

# English Learning Coach

**An adaptive Agent Skill for English practice, IELTS coaching, visual lessons, TTS, and learning records**

![License](https://img.shields.io/badge/License-MIT-yellow)
![Platform](https://img.shields.io/badge/Platform-Codex-1d5fd1)
![Skill](https://img.shields.io/badge/Skill-english--learning--coach-0f8f83)
![IELTS](https://img.shields.io/badge/IELTS-Ready-e85d4f)
![TTS](https://img.shields.io/badge/TTS-Browser%20%7C%20edge--tts-e8b448)

Turn a vague English learning request into a focused practice session with clear steps, realistic feedback, and a reusable learning record.

[中文 README](README.zh-CN.md)

</div>

## What This Is

English Learning Coach is a Codex Skill that helps an Agent act like an adaptive English tutor.

It starts by understanding the learner, then chooses the right learning path. It can support a young child learning animal words, a middle school student reviewing grammar, an IELTS candidate practicing Speaking Part 2, or an adult preparing for workplace communication.

The Skill is designed for practical learning sessions:

1. Ask only the context needed to start.
2. Create a focused task.
3. Give realistic feedback.
4. Generate a learning record.
5. Ask whether progress should be saved.

## What It Can Do

### Adaptive Learner Routing

The Skill routes different learners into different modes:

| Learner | Typical support |
| --- | --- |
| Preschool child | Exposure, picture words, imitation, parent child practice |
| Primary student | Phonics, vocabulary, sentence building, simple HTML pages |
| Middle school student | Grammar, reading, listening, writing, school exam tasks |
| High school student | Exam strategy, reading, cloze, grammar fill in, writing |
| University student | CET style practice, oral English, academic reading, interviews |
| IELTS or TOEFL candidate | Timed practice, rubrics, simulated scoring, weakness drills |
| Workplace learner | Email, meetings, presentations, interviews, negotiation |
| Self learner | Dramas, podcasts, news, novels, papers, user supplied materials |

### Material Based Practice

Paste in English learning material and the Skill can turn it into practice:

1. Articles become graded reading and retelling tasks.
2. Subtitles become listening, shadowing, and phrase mining tasks.
3. Emails become tone improvement and reply drafting tasks.
4. Essays and speaking scripts receive correction and simulated feedback.
5. Test questions receive question type analysis and retry tasks.
6. Word lists become memory plans, examples, and quizzes.

### Visual HTML Lessons

The Skill can generate standalone HTML practice pages for learners who need a more visual experience.

Good examples:

1. A Grade 3 animal vocabulary page with word cards and listen buttons.
2. An IELTS study page with timed practice and feedback.
3. A phonics page with sound groups and short drills.
4. A workplace English page for meeting or email practice.

### TTS Support

The Skill supports several TTS modes:

| Mode | Best for | Notes |
| --- | --- | --- |
| Browser speech | Interactive HTML lessons | Use Microsoft Edge for the most reliable sound |
| edge-tts | Fixed mp3 lesson assets | Best for complete audio packs |
| Azure AI Speech | Product quality audio | Requires user provided credentials |
| Amazon Polly | AWS based batch audio | Requires user provided credentials |

For short interactive lessons, browser speech is recommended. It can read newly generated sentences and does not need audio files.

For fixed mp3 lessons, the Skill should first create an audio manifest that covers every required utterance, including words, sentences, quiz prompts, dialogue turns, and model answers.

### Realistic Feedback

The Skill is expected to reject meaningless input before giving feedback.

For example, if a user enters random letters, it should say that the answer cannot be scored yet and ask for a real response.

For valid answers, feedback should focus on:

1. The most serious issue affecting meaning or score.
2. A repeated grammar, vocabulary, coherence, or expression pattern.
3. One upgrade that helps the learner retry immediately.

### Learning Records

At the end of a useful session, the Skill can output a compact learning record:

```text
Learner type: IELTS candidate
Current goal: Band 7.0 Speaking
Recent training: Speaking Part 2
Main weak point: examples are not specific enough
Learning preference: timed task, model answer, browser TTS
Next task: repeat the same cue card with one stronger example
```

If the Agent environment supports memory, the Skill asks whether the user wants to save the learning record.

## Quick Start

Install the folder into your Codex skills directory:

```text
~/.codex/skills/english-learning-coach
```

Restart Codex, then use:

```text
Use $english-learning-coach to start a focused English practice session.
```

## Example Prompts

### Primary Student

```text
Use $english-learning-coach. Create a 10 minute English practice page for a Grade 3 student learning animal words.
```

### IELTS Speaking

```text
Use $english-learning-coach. I am preparing for IELTS Speaking. My target is Band 7.0. Practice Part 2 with me for 15 minutes.
```

### IELTS Writing

```text
Use $english-learning-coach. Correct this IELTS Task 2 essay and give simulated band feedback.
```

### Workplace English

```text
Use $english-learning-coach. Help me rewrite this English email so it sounds professional but friendly.
```

### Material To Lesson

```text
Use $english-learning-coach. Turn this English article into a reading lesson for an intermediate learner.
```

## How A Session Works

When context is missing, the Skill uses a short five question intake:

1. Who is the learner?
2. What is the goal?
3. What is the current level?
4. How much time is available today?
5. What should be practiced, or does the user have material?

Then it chooses a mode and starts the learning task.

For child friendly pages, it should usually create a visual HTML activity.

For IELTS, TOEFL, university, and workplace practice, it should use a cleaner task based interface with timed practice and focused feedback.

## Optional TTS Setup

The base Skill works without TTS dependencies.

If the user wants audio, the Skill should ask:

```text
需要为本次英语练习安装或配置 TTS 吗？
1. 不需要，使用浏览器内置朗读
2. 需要，帮我安装 edge-tts 生成 mp3
3. 需要，帮我配置 Azure AI Speech
4. 需要，帮我配置 Amazon Polly
```

### Browser Speech

No install is required.

Open generated HTML pages with Microsoft Edge for the most reliable sound. Chrome or other browsers may have missing voices or may fail to speak on some systems.

### edge-tts

Install:

```bash
python -m pip install edge-tts
```

Check voices:

```bash
python -m edge_tts --list-voices
```

Generate an audio file:

```bash
python -m edge_tts --voice en-US-JennyNeural --rate=-10% --text "I like rabbits." --write-media i-like-rabbits.mp3
```

Use edge-tts for complete fixed audio packs. For dynamic lessons, browser speech is usually a better fit.

### Azure AI Speech And Amazon Polly

Use these only after the user chooses the provider and supplies credentials.

Never write credentials into generated HTML, README files, logs, learning records, memory records, or commits.

## Installable Files

```text
english-learning-coach/
  SKILL.md
  README.md
  README.zh-CN.md
  LICENSE
  agents/
    openai.yaml
```

## Validation

Validate the Skill structure with:

```bash
python C:/Users/Admin/.codex/skills/.system/skill-creator/scripts/quick_validate.py path/to/english-learning-coach
```

Expected result:

```text
Skill is valid!
```

## License

MIT
