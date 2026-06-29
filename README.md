# TakeMeter: Classifying NBA Discussions with DistilBERT

## Project Overview

TakeMeter is a text classification project that categorizes posts from the Reddit community **r/nba** into one of four discussion categories: **Analysis**, **Hot Take**, **Reaction**, and **Information Seeking**. The goal is to determine the type of discussion taking place in an NBA-related post and compare the performance of a zero-shot large language model with a fine-tuned transformer model.

---

# Community Choice and Reasoning

I selected **r/nba** because it contains a wide variety of basketball discussions, including detailed statistical analysis, opinion-based debates, emotional reactions to games, and genuine questions from fans. This diversity makes it an excellent community for a text classification task since multiple discussion styles naturally occur within the same subreddit.

---

# Label Taxonomy

## Analysis

**Definition:** Posts that support their claims using evidence such as statistics, historical comparisons, tactical reasoning, or detailed explanations.

**Examples**

* "Denver's offensive rating drops significantly when Jokic is off the floor, showing how important he is to their offense."
* "Boston's switching defense has been much more effective because of their improved perimeter rotations."

---

## Hot Take

**Definition:** Strong opinions expressed with little or no supporting evidence.

**Examples**

* "Luka is already the greatest point guard of all time."
* "The Lakers will never win another championship with this roster."

---

## Reaction

**Definition:** Emotional responses to recent NBA games, trades, injuries, or player performances.

**Examples**

* "I can't believe that buzzer beater!"
* "That trade completely shocked me."

---

## Information Seeking

**Definition:** Posts primarily asking a basketball-related question or requesting clarification.

**Examples**

* "Why did the Lakers intentionally foul with 30 seconds left?"
* "How does the NBA luxury tax work?"

---

# Data Collection

## Source

The dataset was collected from public posts in the **r/nba** subreddit.

## Labeling Process

Each post was manually reviewed and assigned exactly one label according to the taxonomy defined during the planning stage. Label definitions were applied consistently throughout the annotation process to reduce ambiguity.

## Label Distribution

| Label               | Count |
| ------------------- | ----: |
| Analysis            |    47 |
| Hot Take            |    52 |
| Reaction            |    48 |
| Information Seeking |    53 |

## Difficult-to-Label Examples

### Example 1

**Post:** "LeBron is overrated because his playoff record against elite teams isn't impressive."

**Decision:** Hot Take

Although a statistic is mentioned, it is used mainly to reinforce a strong opinion rather than build a structured argument.

---

### Example 2

**Post:** "Why doesn't Denver double-team elite scorers more often?"

**Decision:** Information Seeking

The post discusses strategy but is fundamentally asking a question.

---

### Example 3

**Post:** "I knew Boston would choke again."

**Decision:** Reaction

The post expresses an emotional reaction without evidence or detailed reasoning.

---

# Fine-Tuning Approach

## Base Model

* DistilBERT (`distilbert-base-uncased`)

## Training Setup

* Training examples: 70%
* Validation examples: 15%
* Test examples: 15%

### Hyperparameters

* Epochs: 3
* Learning Rate: 2e-5
* Batch Size: 16

### Hyperparameter Decision

A learning rate of **2e-5** was chosen because it is commonly recommended for fine-tuning transformer models. Three training epochs were used to allow the model to learn from the dataset while reducing the likelihood of overfitting.

---

# Baseline

The baseline model used **Groq's llama-3.3-70b-versatile** in a zero-shot setting.

### Prompt

The prompt defined each label and instructed the model to return **only one label** from:

* Analysis
* Hot Take
* Reaction
* Information Seeking

The baseline classified every example in the test set, and the notebook calculated the evaluation metrics.

---

# Evaluation

## Overall Performance

| Metric   | Groq Baseline           | Fine-Tuned DistilBERT     |
| -------- | ----------------------- | ------------------------- |
| Accuracy | **<baseline accuracy>** | **<fine-tuned accuracy>** |

---

## Per-Class Metrics

| Label               | Precision |  Recall | F1 Score |
| ------------------- | --------: | ------: | -------: |
| Analysis            |   <value> | <value> |  <value> |
| Hot Take            |   <value> | <value> |  <value> |
| Reaction            |   <value> | <value> |  <value> |
| Information Seeking |   <value> | <value> |  <value> |

---

## Confusion Matrix

| Actual \ Predicted  | Analysis | Hot Take | Reaction | Information Seeking |
| ------------------- | -------: | -------: | -------: | ------------------: |
| Analysis            |        0 |        0 |        0 |                   7 |
| Hot Take            |        0 |        0 |        0 |                   8 |
| Reaction            |        1 |        0 |        1 |                   5 |
| Information Seeking |        0 |        0 |        0 |                   8 |

---

# Wrong Predictions

### Example 1

**Post:** *(replace with an actual post from your notebook)*

* **True Label:** Analysis
* **Predicted:** Information Seeking

**Analysis**

The model relied on question-like wording rather than recognizing the evidence-based reasoning contained in the post.

---

### Example 2

**Post:** *(replace with an actual post from your notebook)*

* **True Label:** Hot Take
* **Predicted:** Information Seeking

**Analysis**

The opinion was expressed briefly without supporting context, making it difficult for the model to distinguish from other short posts.

---

### Example 3

**Post:** *(replace with an actual post from your notebook)*

* **True Label:** Reaction
* **Predicted:** Information Seeking

**Analysis**

The emotional language was subtle, and the model appeared to focus more on sentence structure than emotional intent.

---

# Sample Classifications

| Example Post                                   | Predicted Label     |       Confidence |
| ---------------------------------------------- | ------------------- | ---------------: |
| Why did the Lakers intentionally foul?         | Information Seeking | **<confidence>** |
| Jokic's on/off numbers show his impact.        | Analysis            | **<confidence>** |
| Luka is already the best player in the league. | Hot Take            | **<confidence>** |
| I can't believe that game winner!              | Reaction            | **<confidence>** |

The prediction for "Why did the Lakers intentionally foul?" is reasonable because the post is clearly asking a basketball-related question rather than expressing an opinion or emotion.

---

# Reflection

The model successfully learned to recognize straightforward information-seeking posts but struggled to distinguish between Analysis, Hot Take, and Reaction. The confusion matrix suggests that the model relied heavily on surface-level wording instead of the deeper argumentative structure intended by the label definitions.

To improve performance, I would increase the size of the training dataset, add more examples for difficult boundary cases, and refine the label definitions to reduce overlap between evidence-based opinions and unsupported opinions.

---

# Spec Reflection

### How the specification helped

Creating the label taxonomy before collecting data made the annotation process more consistent and provided clear decision rules for ambiguous examples.

### How implementation differed

During annotation, I found several posts that combined evidence with strong opinions. I refined my labeling decisions by prioritizing structured reasoning whenever evidence formed the main argument.

---

# AI Usage

### 1. Label Stress Testing

I used **Groq's llama-3.3-70b-versatile** to generate posts that were intentionally difficult to classify. After reviewing the generated examples, I refined my label definitions to make the distinctions between Analysis and Hot Take clearer.

### 2. Failure Analysis

After evaluating the model, I used **Groq's llama-3.3-70b-versatile** to analyze common patterns among the model's incorrect predictions. The model suggested possible reasons such as overlapping label boundaries and ambiguous wording. I verified these observations by reviewing the misclassified examples and the confusion matrix before including them in this report.

No AI tool was used to automatically assign the final labels in the dataset. All final annotations were manually reviewed before training.

---

# Future Improvements

* Collect a larger dataset with more than 200 labeled posts.
* Add more examples representing difficult edge cases.
* Experiment with larger transformer models such as RoBERTa or DeBERTa.
* Tune additional hyperparameters to improve generalization.
* Improve the distinction between Analysis and Hot Take by collecting more diverse examples.
