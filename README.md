# AI Learning Engine – Task Creation & Auto‑Grading FREE API

## 🚀 Overview
**AI Learning Engine** is an advanced multilingual API that empowers developers, educators, and organizations to instantly generate and auto‑grade intelligent learning tasks. It’s built on next‑generation AI technology and trained on billions of examples of educational content, quizzes, exercises, and real‑world test data.

<p align="center">
  🆓 <b>FREE API</b> — use instantly on 
  <a href="https://rapidapi.com/vintarok-vintarok-default/api/ai-learning-engine-task-creation-auto-grading-api" target="_blank"><b>RapidAPI</b></a> 🚀
</p>

<p align="center">
  <a href="https://rapidapi.com/vintarok-vintarok-default/api/ai-learning-engine-task-creation-auto-grading-api">
    <img src="logo.png" width="120" alt="AI Learning Engine API Logo">
  </a>
</p>

With a single API call, you can create **open questions**, **coding exercises**, or **multiple‑choice quizzes/tests** — all with accurate answers, explanations, and difficulty levels. Designed for seamless integration into any learning platform, it transforms how knowledge is delivered, practiced, and assessed.

---

## 💡 Key Features
- **Multilingual Support (100+ languages)** – generate and grade content in English, Spanish, French, Chinese, Arabic, Russian, Hindi, Japanese, and many more.
- **Three Task Types:**
  - **Open Questions** – conceptual, analytical, and theory‑based prompts.
  - **Exercises** – practical, hands‑on or coding tasks with concise solutions or hints.
  - **Tests/Quizzes** – single‑choice questions with 4 options, correct index, and explanations.
- **Levels of Difficulty:** beginner, intermediate, expert.
- **Instant AI Evaluation:** answers are auto‑checked with reasoning and feedback.
- **Domain‑Agnostic:** works with *any* subject — from computer science to management, medicine, linguistics, philosophy, or aerospace engineering.
- **Trained on Billions of Examples:** powered by advanced AI reasoning models fine‑tuned for educational data.
- **Adaptive Output:** customize topic, notes, and language to fit your audience.

---

## 🧠 Why It’s Unique
Unlike generic AI models, **AI Learning Engine** specializes in **educational intelligence** — it understands how students learn, how questions are structured, and how accurate grading should feel. Its vast training corpus covers:
- Academic test banks and educational materials
- Real exam questions and quizzes across multiple fields
- Thousands of pedagogical datasets used in modern LMS systems
- Billions of multilingual examples with human‑validated answers

That means your generated content is not random — it’s **didactically sound**, balanced by difficulty, and optimized for real learning impact.

---

## 🎯 Ideal Use Cases
**Perfect for integrating into:**
- Learning Management Systems (LMS)
- E‑learning platforms & course builders
- Corporate training and onboarding systems
- University and K‑12 educational apps
- Tutoring and test‑prep apps
- AI chat‑tutors and education bots
- Recruitment & interview preparation tools
- Self‑learning or language‑practice platforms

---

## 🌍 Language Coverage
Supports over **100 languages**, including English, German, French, Spanish, Italian, Portuguese, Russian, Arabic, Chinese, Japanese, Korean, Hindi, Thai, Turkish, and more. The API automatically adapts explanations and answers to the target language for a natural learning experience.

---

## ⚙️ How It Works
### 1. Generate a Task
Send a `POST /generate` request with parameters like:
```json
{
  "topic": "Project management principles",
  "type": "test",
  "level": "intermediate",
  "lang": "English"
}
```
✅ Returns a structured JSON with question, options, correct answer, and explanation.

### 2. Check the Answer
Use `POST /check-answer` to validate learner responses:
```json
{
  "type": "test",
  "level": "intermediate",
  "topic": "Project management principles",
  "task": "Which process defines project scope?",
  "options": ["Planning", "Executing", "Closing", "Monitoring"],
  "correctIndex": 0,
  "userAnswer": 0
}
```
✅ Returns:
```json
{
  "correct": true,
  "explanation": "Planning defines and documents the project scope and objectives."
}
```

---

## 🧩 Integration Possibilities
You can integrate the **AI Learning Engine** into virtually any ecosystem:
- **Web apps** – deliver dynamic lessons or quizzes.
- **Mobile apps** – language trainers or exam practice tools.
- **Chatbots** – conversational tutors that teach interactively.
- **APIs & Plugins** – LMS extensions, browser tools, Slack or Discord bots.
- **Corporate dashboards** – internal skill testing and e‑learning automation.

---

## ⚡ Why Developers Love It
- Clean, JSON‑based REST API
- Consistent schemas across endpoints
- Fast generation and grading (usually under 3 seconds)
- Transparent pricing on RapidAPI
- No model tuning required – plug and play

---

## 🏆 The Future of Education Starts Here
AI Learning Engine bridges the gap between **AI intelligence** and **human teaching**. Whether you’re building a learning app, launching an ed‑tech startup, or upgrading a corporate LMS — this API gives you the brainpower to **create, adapt, and evaluate knowledge at scale**.

Let AI handle the heavy lifting — so your users can focus on learning, creating, and growing.

---

**Ready to revolutionize learning?**  
👉 Try **AI Learning Engine – Task Creation & Auto‑Grading API** today on RapidAPI!

---

# AI Learning Engine – Generate Task Endpoint Documentation

## Overview
The **Generate Task API** allows developers to create unique, AI-generated learning items of various types: open questions, coding exercises, or single-choice tests. Each task is tailored to a given topic, difficulty level, and optionally a target language or notes for guidance. The API returns structured JSON with all relevant fields and omits `null` values automatically.

---

## Endpoint Summary
**Endpoint:** `/generate.php`  
**Method:** `POST`  
**Content-Type:** `application/json`  
**Authentication:** Requires `X-RapidAPI-Proxy-Secret`

---

## Description
Generates one learning task based on your provided topic, type, and difficulty level. The task can be theoretical (`open`), practical (`exercise`), or multiple-choice (`test`). You can optionally specify `lang` for multilingual output and `notes` to influence style, tone, or subject depth.

Each response is strictly formatted JSON containing the generated task, answer, and additional metadata.


---

## Request Body Schema
| Field | Type | Required | Allowed Values | Description |
|--------|------|:---------:|----------------|--------------|
| `topic` | string | ✅ | Any (≤320 chars) | The topic or subject for the generated task. |
| `type` | string | ✅ | `open`, `exercise`, `test` | Defines the kind of task to generate. |
| `level` | string | ✅ | `beginner`, `intermediate`, `expert` | Difficulty level. |
| `lang` | string | ❌ | ≤20 characters | Target language for the task and answer. Default is **English**. |
| `notes` | string | ❌ | up to several KB | Additional context or hints to guide the AI. |

&gt; **Notes**
&gt; - `lang` defaults to English if not specified.
&gt; - `notes` can be long — use POST to avoid URL length limits.
&gt; - The API returns only valid fields (no `null`s).

---

## Sample Requests

### 1️⃣ Open Question (Beginner)
```json
{
  "topic": "Java basics: variables",
  "type": "open",
  "level": "beginner"
}
```

### 2️⃣ Open (Advanced, English + Notes)
```json
{
  "topic": "Distributed systems: consensus protocols",
  "type": "open",
  "level": "expert",
  "lang": "English",
  "notes": "Focus on trade-offs: leader election, CAP theorem, latency vs consistency. Avoid trivial definitions."
}
```

### 3️⃣ Exercise (Intermediate, Russian)
```json
{
  "topic": "Array processing",
  "type": "exercise",
  "level": "intermediate",
  "lang": "Russian"
}
```

### 4️⃣ Test (Expert, Deutsch)
```json
{
  "topic": "SQL query optimization",
  "type": "test",
  "level": "expert",
  "lang": "Deutsch"
}
```

### 5️⃣ Test (Intermediate, English + Notes)
```json
{
  "topic": "HTTP caching directives",
  "type": "test",
  "level": "intermediate",
  "notes": "Highlight Cache-Control vs ETag; avoid confusing wording."
}
```

---

## Success Responses
&gt; Envelope (null fields omitted):
```json
{
  "ok": true,
  "data": { ... }
}
```

### ✅ Example A – Open Question
```json
{
  "ok": true,
  "data": {
    "topic": "Java basics: variables",
    "lang": "English",
    "taskId": "4f0c1b2a3d4e5f67890123456789abcd",
    "task": "Explain the purpose of the 'final' keyword in Java.",
    "type": "open",
    "level": "beginner",
    "answer": "It defines constants or prevents a method or class from being modified or overridden."
  }
}
```

### ✅ Example B – Exercise
```json
{
  "ok": true,
  "data": {
    "topic": "Array processing",
    "lang": "Russian",
    "taskId": "f1e2d3c4b5a697887766554433221100",
    "task": "Напишите функцию, которая возвращает сумму всех элементов массива.",
    "type": "exercise",
    "level": "intermediate",
    "answer": "Используйте цикл или функцию sum(); проверьте, что массив не пуст."
  }
}
```

### ✅ Example C – Test
```json
{
  "ok": true,
  "data": {
    "topic": "SQL query optimization",
    "lang": "Deutsch",
    "taskId": "aabbccddeeff00112233445566778899",
    "task": "Welche SQL-Klausel entfernt doppelte Zeilen?",
    "type": "test",
    "level": "expert",
    "options": ["GROUP BY", "DISTINCT", "HAVING", "UNION ALL"],
    "answer": 1,
    "explanation": "DISTINCT filtert doppelte Datensätze in der Ergebnismenge."
  }
}
```

---

## Error Responses

### ❌ 400 — Missing or invalid fields
```json
{
  "ok": false,
  "error": "Missing required fields: topic, type, level"
}
```

### ❌ 403 — Invalid proxy secret
```json
{
  "ok": false,
  "error": "Forbidden: invalid proxy secret"
}
```

### ❌ 405 — Wrong method
```json
{
  "ok": false,
  "error": "Method Not Allowed. Use POST."
}
```

### ❌ 502 — AI API error
```json
{
  "ok": false,
  "error": "Upstream AI error",
  "detail": "AI API error: &lt;message&gt;"
}
```

---

## Field Notes & Behavior
- `topic`, `type`, and `level` are **required**.
- `lang` ≤ 20 characters; defaults to **English** if omitted.
- `notes` is optional and can be long.
- `type` options: `open`, `exercise`, `test`.
- `level` options: `beginner`, `intermediate`, `expert`.
- Null fields are filtered before response (`array_filter`).
- `answer` for `test` is an integer index (0–3); for others, a text string.
- `options` appear only in `test` tasks.

---

## Example Integration (Node.js)
```js
const axios = require("axios");

const data = {
  topic: "SQL joins",
  type: "test",
  level: "beginner"
};

axios.post("https://YOUR_HOST/rapidapi/generate", data, {
  headers: { "X-RapidAPI-Proxy-Secret": process.env.RAPIDAPI_PROXY_SECRET }
}).then(res =&gt; console.log(res.data));
```

---

## Summary
The **Generate Task API** creates customized, multilingual learning tasks with correct answers and explanations. It supports multiple task types, difficulty levels, and 100+ languages, making it ideal for LMS platforms, learning

# AI Learning Engine – Check Answer Endpoint Documentation

## Overview
The **Check Answer API** allows developers to validate learner responses against generated learning tasks. It supports all task types generated by the AI Learning Engine: **open**, **exercise**, and **test**. The endpoint provides a consistent JSON structure, omits null fields, and handles multilingual explanations when a `lang` parameter is provided.

---

## Endpoint Summary
**Endpoint:** `/check-answer.php`  
**Method:** `POST`  
**Content-Type:** `application/json`  
**Authentication:** Requires `X-RapidAPI-Proxy-Secret`

---

## Description
This endpoint verifies user-submitted answers for any generated task, returning whether the response is correct and providing a brief explanation. The system is stateless: you must include the full task payload in your request along with the learner’s answer.

- For **tests**, you may submit either the **answer index (0–3)** or the **option text**.
- For **open** and **exercise** tasks, the answer is compared to a reference solution using AI grading.
- When `lang` is provided, the explanation is returned in that language.
- No sessions, databases, or rate limits are used — RapidAPI handles quotas.


---

## Request Body Schema
The request must include all required task details and the learner’s answer.

### Common Fields
| Field | Type | Required | Allowed Values | Description |
|--------|------|:---------:|----------------|--------------|
| `type` | string | ✅ | `open`, `exercise`, `test` | Type of task being checked. |
| `level` | string | ✅ | `beginner`, `intermediate`, `expert` | Difficulty level. |
| `topic` | string | ✅ | Any string (≤320 chars) | The topic of the question. |
| `task` | string | ✅ | — | The question text. |
| `lang` | string | ❌ | ≤20 characters | Output language for explanation. |
| `userAnswer` | string or integer | ✅ | — | The learner’s answer. For tests, can be an index (0–3) or option text. |

### Fields for `test` Type
| Field | Type | Required | Description |
|--------|------|:---------:|--------------|
| `options` | array[string] | ✅ | Exactly 4 options. |
| `correctIndex` | integer | ✅ | Index of correct answer (0–3). |
| `explanation` | string | ❌ | Original rationale (optional). |

### Fields for `open` / `exercise` Type
| Field | Type | Required | Description |
|--------|------|:---------:|--------------|
| `referenceAnswer` | string | ✅ | The model’s correct answer or hints for grading. |

---

## Sample Requests

### 1️⃣ Test – numeric index
```json
{
  "type": "test",
  "level": "intermediate",
  "topic": "OOP basics",
  "task": "Which principle hides internal details?",
  "lang": "English",
  "options": ["Inheritance", "Encapsulation", "Polymorphism", "Abstraction"],
  "correctIndex": 1,
  "explanation": "Encapsulation hides internal state; access via methods.",
  "userAnswer": 1
}
```

### 2️⃣ Test – answer text
```json
{
  "type": "test",
  "level": "beginner",
  "topic": "Databases",
  "task": "Which index is best for equality lookups?",
  "options": ["Full-text", "B-Tree", "Hash", "Bitmap"],
  "correctIndex": 2,
  "userAnswer": "Hash"
}
```

### 3️⃣ Open – localized German explanation
```json
{
  "type": "open",
  "level": "beginner",
  "topic": "HTTP caching",
  "task": "Explain why ETag reduces bandwidth.",
  "lang": "Deutsch",
  "referenceAnswer": "ETag allows conditional requests (If-None-Match). If unchanged, server returns 304 and skips body.",
  "userAnswer": "Client sends If-None-Match and gets 304 when resource didn't change."
}
```

### 4️⃣ Exercise – Russian answer
```json
{
  "type": "exercise",
  "level": "intermediate",
  "topic": "Array processing",
  "task": "Return the max element of an integer array.",
  "lang": "Russian",
  "referenceAnswer": "Track a running maximum and compare each element; handle empty arrays.",
  "userAnswer": "Loop through and keep the largest value."
}
```

### 5️⃣ Test – incorrect answer
```json
{
  "type": "test",
  "level": "expert",
  "topic": "SQL isolation levels",
  "task": "Which level prevents non-repeatable reads?",
  "options": ["Read Uncommitted", "Read Committed", "Repeatable Read", "Serializable"],
  "correctIndex": 2,
  "userAnswer": "Read Committed"
}
```

---

## Success Responses
&gt; Envelope:
```json
{
  "ok": true,
  "data": { ... }
}
```

### ✅ Example A – TEST (correct)
```json
{
  "ok": true,
  "data": {
    "correct": true,
    "explanation": "Encapsulation hides internal state; access via methods."
  }
}
```

### ✅ Example B – TEST (incorrect)
```json
{
  "ok": true,
  "data": {
    "correct": false
  }
}
```

### ✅ Example C – OPEN (German feedback)
```json
{
  "ok": true,
  "data": {
    "correct": true,
    "explanation": "ETag ermöglicht 304-Antworten bei unveränderter Ressource und spart Datenübertragung."
  }
}
```

### ✅ Example D – EXERCISE (partially correct)
```json
{
  "ok": true,
  "data": {
    "correct": false,
    "explanation": "Correct logic but missing empty array handling."
  }
}
```

---

## Error Responses

### ❌ 400 — Missing or invalid fields
```json
{
  "ok": false,
  "error": "Missing required fields: type, level, topic, task, userAnswer"
}
```

### ❌ 400 — Invalid options count
```json
{
  "ok": false,
  "error": "\"options\" must be an array of exactly 4 strings"
}
```

### ❌ 403 — Invalid proxy secret
```json
{
  "ok": false,
  "error": "Forbidden: invalid proxy secret"
}
```

### ❌ 405 — Wrong method
```json
{
  "ok": false,
  "error": "Method Not Allowed. Use POST."
}
```

### ❌ 502 — AI or moderation error
```json
{
  "ok": false,
  "error": "Upstream AI error",
  "detail": "AI API error: &lt;message&gt;"
}
```

---

## Field Notes & Behavior
- `lang` ≤ 20 characters. If not provided, English is used by default.
- `type` ∈ {`open`, `exercise`, `test`}.
- `level` ∈ {`beginner`, `intermediate`, `expert`}.
- For **test**, prefer numeric index answers (0–3).
- Fields that are `null` are automatically omitted from response.
- The API does not use `temperature` or `reasoning` settings.
- AI grading logic ensures concise, natural explanations.

---

## Example Integration (Node.js)
```js
const axios = require("axios");

const data = {
  type: "test",
  level: "beginner",
  topic: "OOP Basics",
  task: "Which principle hides internal details?",
  options: ["Inheritance", "Encapsulation", "Polymorphism", "Abstraction"],
  correctIndex: 1,
  userAnswer: 1
};

axios.post("https://YOUR_HOST/rapidapi/check-answer", data, {
  headers: { "X-RapidAPI-Proxy-Secret": process.env.RAPIDAPI_PROXY_SECRET }
}).then(res =&gt; console.log(res.data));
```

---

## Summary
The **Check Answer API** provides instant evaluation of user answers for generated learning tasks. It supports multilingual feedback, consistent structured JSON, and a unified design across question types. Ideal for integrating into learning apps, LMS, AI tutors, and quiz systems.

