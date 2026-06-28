# AI Tool Plan

## Label Stress-Testing

Before beginning annotation, I will use Groq's **llama-3.3-70b-versatile** model to generate 5–10 NBA posts that intentionally fall between two labels. If any generated examples cannot be classified consistently using my label definitions, I will revise the definitions before labeling the full dataset.

---

## Annotation Assistance

I will not use Groq to automatically label my dataset. All 200 examples will be manually reviewed and labeled to ensure consistency and to maintain complete control over the annotation process. Groq may only be used to generate additional practice examples for testing the label definitions.

---

## Failure Analysis

After evaluating the model, I will use Groq's **llama-3.3-70b-versatile** model to analyze the incorrectly classified examples and identify common error patterns, such as confusing Analysis with Hot Take or Reaction with Hot Take. I will verify any suggested patterns by comparing them with the confusion matrix and the original test examples before including them in my evaluation report.
