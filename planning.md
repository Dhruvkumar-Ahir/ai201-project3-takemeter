Label Taxonomy
Label 1 – Analysis

Definition

A post that supports its main claim using evidence such as statistics, historical comparisons, tactical reasoning, or detailed explanations.

Example 1

"The Celtics improved their defense after the All-Star break by switching more often, lowering opponents' three-point percentage."

Example 2

"Denver's offensive rating drops nearly eight points per 100 possessions whenever Jokic leaves the floor."

Label 2 – Hot Take

Definition

A post that makes a bold opinion without providing substantial evidence or reasoning.

Example 1

"Wembanyama will become the greatest NBA player ever before he turns 25."

Example 2

"Analytics completely ruined basketball."

Label 3 – Reaction

Definition

A post that mainly expresses an emotional response to a recent game, player performance, or NBA event.

Example 1

"Luka's game winner was unbelievable!"

Example 2

"Those referees were absolutely terrible tonight."

Label 4 – Information Seeking

Definition

A post whose main purpose is asking a genuine basketball-related question.

Example 1

"Can someone explain how Bird Rights work?"

Example 2

"Why do NBA teams intentionally foul near the end of games?"

Hard Edge Cases

One difficult case is a post that contains both an opinion and a statistic.

Example:

"LeBron is overrated because his playoff record against top-seeded opponents is below .500."

This could be labeled as either Analysis or Hot Take.

Decision Rule

If the statistic is part of a structured argument that explains the conclusion, the post will be labeled Analysis.

If the statistic is only included to strengthen a provocative opinion without further reasoning, it will be labeled Hot Take.

Data Collection Plan

I will collect public posts and comments from r/nba using Reddit.

My goal is to collect at least 200 labeled examples.

Target distribution:

Analysis: 50 posts
Hot Take: 50 posts
Reaction: 50 posts
Information Seeking: 50 posts

If one label is underrepresented after collecting 200 examples, I will search for posts related to that category until the dataset is reasonably balanced. Maintaining a balanced dataset will help reduce model bias during training.

Evaluation Metrics

I will evaluate the classifier using several metrics instead of relying only on accuracy.

Accuracy

Measures the overall percentage of correct predictions.

Precision

Measures how often predictions for each label are correct. This is important because confusing Hot Take and Analysis could reduce the usefulness of the classifier.

Recall

Measures how many posts from each class are correctly identified. A high recall ensures that important categories are not frequently missed.

F1 Score

Balances precision and recall and provides a better measurement when class distributions are not perfectly balanced.

Confusion Matrix

The confusion matrix will help identify which labels the model confuses most often, especially between Analysis and Hot Take.

Definition of Success

I would consider this project successful if:

Overall test accuracy is at least 80%.
Every class has an F1-score of at least 0.75.
The model consistently distinguishes Analysis from Hot Take, since this is expected to be the most difficult classification task.
The fine-tuned model performs better than the zero-shot Groq Llama baseline on the same test set.

A classifier meeting these goals would be useful as a moderation or content-analysis tool that categorizes NBA discussions with reasonable reliability.

# AI Tool Plan

## Label Stress-Testing

Before beginning annotation, I will use Groq's **llama-3.3-70b-versatile** model to generate 5–10 NBA posts that intentionally fall between two labels. If any generated examples cannot be classified consistently using my label definitions, I will revise the definitions before labeling the full dataset.

---

## Annotation Assistance

I will not use Groq to automatically label my dataset. All 200 examples will be manually reviewed and labeled to ensure consistency and to maintain complete control over the annotation process. Groq may only be used to generate additional practice examples for testing the label definitions.

---

## Failure Analysis

After evaluating the model, I will use Groq's **llama-3.3-70b-versatile** model to analyze the incorrectly classified examples and identify common error patterns, such as confusing Analysis with Hot Take or Reaction with Hot Take. I will verify any suggested patterns by comparing them with the confusion matrix and the original test examples before including them in my evaluation report.
