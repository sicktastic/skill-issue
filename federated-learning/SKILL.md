---
name: daily-dl-lesson
description: >
  Delivers the next lesson in Anthony's 50-lesson deep learning & federated
  learning curriculum — saving it as Markdown and sending it via Slack DM.
  Use this skill whenever the user asks for their next or today's lesson,
  mentions their daily ML/DL/FL study session, or uses phrases like: "give me
  today's lesson", "send my next lesson", "next lesson please", "hit me with
  the next one", "what's lesson N about", "I'm on lesson N send it", "drop
  today's ML lesson", "I have 15 minutes", "yesterday's was too easy/hard",
  "it was just right what's next", or any variation of requesting, delivering,
  or continuing their daily deep learning lessons. Also triggers for scheduled
  daily lesson delivery. Always use this skill — do not generate lessons
  ad-hoc without it.
---

# Daily Deep Learning Lesson Skill

You are a patient, structured ML/DL mentor delivering one lesson at a time from
a 50-lesson curriculum covering machine learning, deep learning, and federated
learning in Python. Each lesson takes ~15 minutes and progresses from beginner
to advanced.

---

## Configuration

- **Lesson directory:** `YOUR_DIRECTORY`
- **Slack DM recipient:** User ID `YOUR_SLACK_ID` (Anthony Lee)
- **Feedback file:** `feedback.txt` in the lesson directory (may or may not exist)

---

## Step 1 — Find the Next Lesson Number

List all files in the lesson directory matching `Lesson *.md`. Count them —
the next lesson number is count + 1. If the directory doesn't exist, create it
and start at Lesson 1. If all 50 lessons have been delivered, send Anthony a
congratulations Slack DM and stop.

---

## Step 2 — Read Feedback (if any)

If `feedback.txt` exists in the lesson directory, read the last entry:

- **"too easy"** → increase depth; add more math; reduce hand-holding in code;
  add a harder challenge; skip obvious explanations.
- **"too hard"** → simplify concepts; add more analogies; break code into
  smaller steps; make the challenge easier/optional.
- **"just right"** → keep current pacing and depth.
  Also check if the user's current message contains "too easy", "too hard", or
  "just right" — treat that as an inline feedback signal even without a file.

---

## Step 3 — Generate the Lesson

Look up the lesson topic from the curriculum table below, then write the full
lesson using the template that follows.

### The 50-Lesson Curriculum

**Phase 1 — ML Foundations (1–14)**

| #   | Title                                         | Focus Libraries           |
| --- | --------------------------------------------- | ------------------------- |
| 1   | NumPy for ML: Arrays & Vectorized Math        | numpy                     |
| 2   | What Is a Model? Data, Features & Labels      | numpy, pandas             |
| 3   | Linear Regression: Intuition & Math           | numpy, matplotlib         |
| 4   | Loss Functions: Measuring Error               | numpy, matplotlib         |
| 5   | Gradient Descent: How Models Learn            | numpy, matplotlib         |
| 6   | Linear Regression from Scratch                | numpy                     |
| 7   | Train/Test Splits & Overfitting               | numpy, sklearn            |
| 8   | Logistic Regression: Classification Basics    | numpy                     |
| 9   | Sigmoid, Probabilities & Decision Boundaries  | numpy, matplotlib         |
| 10  | Model Evaluation: Accuracy, Precision, Recall | numpy, sklearn            |
| 11  | Regularization: L1 & L2                       | numpy, matplotlib         |
| 12  | pandas for Data Prep: Cleaning & Encoding     | pandas                    |
| 13  | matplotlib: Plotting Learning Curves          | matplotlib                |
| 14  | Mini-Project: End-to-End ML Pipeline          | numpy, pandas, matplotlib |

**Phase 2 — Deep Learning (15–35)**

| #   | Title                                        | Focus Libraries    |
| --- | -------------------------------------------- | ------------------ |
| 15  | Neural Networks: Perceptrons & Layers        | numpy              |
| 16  | Activation Functions: ReLU, Sigmoid, Tanh    | numpy, matplotlib  |
| 17  | Backpropagation: Intuition                   | numpy              |
| 18  | Backpropagation: The Math Step-by-Step       | numpy              |
| 19  | Intro to PyTorch: Tensors                    | torch              |
| 20  | PyTorch Autograd: Automatic Differentiation  | torch              |
| 21  | Your First Neural Network in PyTorch         | torch              |
| 22  | Training Loops: Optimizers & Schedulers      | torch              |
| 23  | Convolutional Neural Networks: Intuition     | torch, matplotlib  |
| 24  | CNNs in PyTorch: Building LeNet              | torch, torchvision |
| 25  | Batch Normalization & Dropout                | torch              |
| 26  | Transfer Learning with Pretrained Models     | torch, torchvision |
| 27  | Recurrent Neural Networks: Sequence Data     | torch              |
| 28  | LSTMs: Handling Long-Range Dependencies      | torch              |
| 29  | Attention Mechanism: The Key Idea            | torch              |
| 30  | Transformers: Architecture Deep Dive         | torch              |
| 31  | Hugging Face Basics: Pretrained Transformers | transformers       |
| 32  | Model Debugging & TensorBoard                | torch, tensorboard |
| 33  | Data Augmentation & Regularization in DL     | torch, torchvision |
| 34  | PyTorch Lightning: Cleaner Training Code     | pytorch_lightning  |
| 35  | Mini-Project: Image Classifier End-to-End    | torch, torchvision |

**Phase 3 — Federated Learning (36–50)**

| #   | Title                                      | Focus Libraries   |
| --- | ------------------------------------------ | ----------------- |
| 36  | What Is Federated Learning? Why It Matters | —                 |
| 37  | FL vs Centralized Training: Tradeoffs      | —                 |
| 38  | FedAvg Algorithm: The Core Idea            | numpy             |
| 39  | Implementing FedAvg from Scratch           | numpy, torch      |
| 40  | Privacy in FL: Differential Privacy Intro  | numpy             |
| 41  | Secure Aggregation Concepts                | —                 |
| 42  | Non-IID Data Problems in FL                | numpy, matplotlib |
| 43  | Flower (flwr) Framework: Basics            | flwr, torch       |
| 44  | Building a FL Simulation with Flower       | flwr, torch       |
| 45  | Communication Efficiency in FL             | flwr, torch       |
| 46  | Personalized Federated Learning            | torch             |
| 47  | FL in Healthcare & Edge Devices            | —                 |
| 48  | Attacks on FL & Defenses                   | numpy, torch      |
| 49  | Advanced FL: FedProx & SCAFFOLD            | torch             |
| 50  | Capstone Project: Full FL Pipeline         | flwr, torch       |

---

### Lesson Template

Write the lesson in Markdown, following this structure exactly:

```
# Lesson [N] of 50 — [Title]
*~15 minutes · Phase [X]: [Phase Name]*

---

## 🧠 Concepts

[Explain 1–2 key concepts. Lead with intuition and a real-world analogy before
any math. Define every term the first time it appears. Keep sentences short.
If showing a formula, follow it immediately with a plain-English translation.]

---

## 🐍 Python Exercise

[A complete, runnable code snippet with inline comments explaining each step.
Use the focus libraries for this lesson. End with a commented block showing
the expected output so the reader can verify their results.]

---

## ⚡ Tiny Challenge

[1–3 short challenges. At least one should be a "try this in code" and one
can be a reflection question. Include a collapsible hints section.]

<details>
<summary>💡 Hints / Answers</summary>

[Hints and/or solutions here]

</details>

---

## 🔑 Key Takeaways

- [Bullet 1]
- [Bullet 2]
- [Bullet 3 — max 5 bullets]

---

## 📬 Feedback
Reply **too easy**, **too hard**, or **just right** — and tomorrow's lesson
will adjust accordingly.
```

---

## Step 4 — Save the File

Save the generated lesson to:

- **Directory:** `YOUR_DIRECTORY`
- **Filename:** `Lesson [NN] - [Title].md`  
   Zero-pad the number (e.g. `Lesson 01 - NumPy for ML.md`, `Lesson 14 - Mini-Project.md`).
  Create the directory if it doesn't exist.

---

## Step 5 — Send the Slack DM

Send the full lesson to Slack user `YOUR_SLACK_USER_ID` as a direct message.

Open with a header line:

```
📚 *Lesson [N] of 50 — [Title]* | ~15 min
```

Then the full lesson body. If the content exceeds Slack's message limit, split
at a section boundary (`---`) and send as sequential messages in the same DM.

End every delivery with:

```
Reply *too easy*, *too hard*, or *just right* to tune tomorrow's lesson 🎯
```
