# English Learning Coach Skill

English Learning Coach is an adaptive Codex Skill for English learning. It routes learners by age, goal, level, available time, and material type, then creates a focused learning activity with feedback and a learning record.

It supports learners from early childhood to university, IELTS, TOEFL, workplace English, self study, speaking practice, writing correction, reading, listening, vocabulary, role play, study plans, and HTML practice pages.

## Core Value

This Skill turns a broad English learning request into a concrete practice session.

It can:

1. Ask a short intake and identify the learner profile.
2. Choose the right training mode for children, students, test candidates, workplace learners, or self learners.
3. Convert user materials into practice tasks.
4. Create visual HTML learning pages.
5. Add browser TTS or generated audio when useful.
6. Give focused correction and simulated scoring.
7. Produce a learning record and ask whether to save progress.

## Installation

Copy this folder into your Codex skills directory:

```text
~/.codex/skills/english-learning-coach
```

The folder should contain:

```text
english-learning-coach/
  SKILL.md
  README.md
  agents/
    openai.yaml
```

Restart Codex after installation so the Skill can be discovered.

Then invoke it with:

```text
Use $english-learning-coach to assess my English goal and start a focused practice session.
```

## Required Dependencies

The base Skill has no required runtime dependency beyond an Agent tool that supports Codex Skills.

Base features work without extra packages:

1. Learner intake.
2. English practice generation.
3. Material processing.
4. Role play.
5. Writing and speaking feedback.
6. Simulated scoring.
7. Study plans.
8. Learning records.

## Optional TTS Dependencies

TTS is optional. The Skill should ask the user before installing or configuring TTS.

Recommended prompt:

```text
需要为本次英语练习安装或配置 TTS 吗？
1. 不需要，使用浏览器内置朗读
2. 需要，帮我安装 edge-tts 生成 mp3
3. 需要，帮我配置 Azure AI Speech
4. 需要，帮我配置 Amazon Polly
```

### Browser Built In TTS

Use this for most HTML practice pages, especially children and short interactive lessons.

No install is required.

Requirements:

1. Open the HTML page with Microsoft Edge for the most reliable speech output.
2. Chrome or other browsers may have missing voices or may fail to speak on some systems.
3. The page should use click based listen buttons and avoid autoplay.

Best for:

1. Vocabulary cards.
2. Sentence drills.
3. Dynamic model answers.
4. Quiz prompts.
5. Short speaking practice.

### edge-tts

Use this only when the user wants fixed mp3 audio assets, offline audio packs, or repeatable course audio.

Requirements:

1. Python.
2. The `edge-tts` package.

Install command:

```bash
python -m pip install edge-tts
```

Basic voice check:

```bash
python -m edge_tts --list-voices
```

Example mp3 generation:

```bash
python -m edge_tts --voice en-US-JennyNeural --rate=-10% --text "I like rabbits." --write-media i-like-rabbits.mp3
```

Important rule:

Do not generate mp3 only for isolated words when the lesson also needs full sentences, quiz prompts, dialogue turns, or model answers. Build an audio manifest first, then generate every utterance needed by the page.

For dynamic pages, prefer browser built in TTS unless every sentence variant is known and generated.

### Azure AI Speech

Use this for product quality, stable voice selection, and repeated use with caching.

The user must provide:

1. Speech key.
2. Region.
3. Endpoint or equivalent configuration.

After credentials are provided:

1. Store credentials in a secure local configuration or environment variables.
2. Test one English voice and one Chinese voice.
3. Cache generated audio to avoid repeated cost.
4. Never write credentials into HTML, logs, learning records, or memory records.

### Amazon Polly

Use this for AWS based projects or batch audio generation.

The user must provide AWS credentials with permission to call Polly.

After credentials are provided:

1. Verify AWS access.
2. Test one English voice and one Chinese voice.
3. Cache generated audio.
4. Never write credentials into HTML, logs, learning records, or memory records.

## How To Use

### Quick Start

```text
Use $english-learning-coach. I am an IELTS candidate. My target is Band 7.0. I want to practice Speaking Part 2 for 15 minutes.
```

```text
Use $english-learning-coach. Create a 10 minute English practice page for a Grade 3 student learning animal words.
```

```text
Use $english-learning-coach. Please correct this IELTS Task 2 essay and give simulated feedback.
```

### Default Intake

If the user does not provide enough context, the Skill asks five questions:

1. Who is the learner?
2. What is the learning goal?
3. What is the current level?
4. How much time is available today?
5. What should be practiced, or does the user have material?

Use a detailed intake only when the user asks for assessment, long term planning, test preparation planning, or a child learning plan.

## Learner Routing

The Skill routes the user into one of these modes:

1. Preschool child: exposure, songs, picture words, parent child dialogue, imitation.
2. Primary student: phonics, vocabulary, textbook support, sentence building.
3. Middle school student: grammar, reading, listening, writing, school exam tasks.
4. High school student: school exam strategy, cloze, reading, grammar fill in, writing.
5. University student: CET style practice, oral English, academic reading, resume, interview.
6. IELTS or TOEFL candidate: timed practice, rubrics, simulated scoring, weakness drills.
7. Workplace learner: emails, meetings, presentations, interviews, negotiation.
8. Self learner: dramas, podcasts, news, novels, papers, and user supplied materials.

## HTML Practice Pages

When the learner profile and plan are clear, the Skill can generate a standalone HTML page.

The page should be the learning activity itself.

Good page structure:

1. Goal and learner group.
2. Warm up.
3. Main practice.
4. Timed task or quiz.
5. Feedback or review.
6. Learning record.
7. Optional listen buttons.

For young learners, use large tap targets, simple language, friendly spacing, and visual cards.

For IELTS, TOEFL, university, and workplace learners, use a cleaner practice interface with timed tasks and specific feedback.

## Feedback Rules

Feedback must be realistic.

Before giving feedback, check whether the user input is valid. If the input is random letters, too short, repeated fragments, or not meaningful English, say that it cannot be scored yet and ask for a real answer.

Default correction should focus on the three most important issues:

1. Serious issue that affects meaning, score, politeness, or tone.
2. Repeated pattern in grammar, vocabulary, collocation, pronunciation clue, or logic.
3. Expression upgrade for a more natural or accurate version.

Detailed line by line correction should be used only when the user asks for it or submits exam work for score improvement.

## Simulated Scoring

Scores are only for learning reference.

Always label them as simulated.

Use dimension based feedback for IELTS and TOEFL. Avoid scoring children unless a parent or teacher asks for it.

If the prompt, rubric, or task requirement is missing, say the score is incomplete and ask for the missing context.

## Learning Records

At the end of a meaningful session, output a learning record.

Default fields:

1. Learner type.
2. Current goal.
3. Current level.
4. Recent training.
5. Main weak points.
6. Common errors.
7. Learning preferences.
8. Next recommended task.

The Skill should ask whether to save the record to the Agent memory system.

Save only when the user explicitly requests saving and the current Agent environment supports memory writing.

Do not save sensitive personal information. For children, save learning relevant summaries only.

## Security Notes

Do not include secrets in:

1. HTML pages.
2. README files.
3. Learning records.
4. Memory records.
5. Git commits.
6. Logs.

For Azure AI Speech or Amazon Polly, wait for the user to choose that provider before asking for credentials.

## Validation

Validate the Skill structure with:

```bash
python C:/Users/Admin/.codex/skills/.system/skill-creator/scripts/quick_validate.py path/to/english-learning-coach
```

Expected result:

```text
Skill is valid!
```

## Maintenance

When updating this Skill:

1. Keep `SKILL.md` concise and action oriented.
2. Keep TTS guidance practical and explicit.
3. Test generated HTML pages in a real browser.
4. For browser speech pages, verify sound in Microsoft Edge.
5. For generated mp3 pages, verify the audio manifest covers all required utterances.
6. Re run `quick_validate.py` after every structural change.

