# AI201 Project 3 – TakeMeter

# Milestone 1: Community and Label Design

## Community

**Chosen Community:** r/nba (Reddit NBA Discussion)

### Community Description

This project focuses on r/nba, one of the largest online basketball discussion communities. Users discuss NBA games, players, trades, coaching decisions, and league news through a mixture of statistical analysis, opinions, emotional reactions, and questions. Distinguishing between these types of posts is valuable because members often debate whether a take is well-supported or simply an emotional opinion.

---

# Label Taxonomy

## Label 1: Analysis

### Definition

A post that supports its main claim using evidence such as statistics, historical comparisons, tactical reasoning, or detailed explanations.

### Clear Example 1

"The Celtics' defense has improved significantly since the All-Star break. Their defensive rating dropped from 115 to 109 because they're switching more effectively on pick-and-rolls."

### Clear Example 2

"Denver's offense falls nearly eight points per 100 possessions whenever Jokic sits, showing how important he is beyond scoring."

### Uncertain Example

"LeBron is overrated because his playoff record against top-seeded teams is below .500."

---

## Label 2: Hot Take

### Definition

A bold opinion stated confidently without enough supporting evidence or reasoning.

### Clear Example 1

"Wembanyama will become the greatest basketball player of all time before he turns 25."

### Clear Example 2

"Analytics completely ruined basketball."

### Uncertain Example

"LeBron is overrated because his playoff record against top-seeded teams is below .500."

---

## Label 3: Reaction

### Definition

A post whose primary purpose is expressing an emotional response to a recent game, player performance, or NBA event.

### Clear Example 1

"Luka's game winner was absolutely insane!!"

### Clear Example 2

"These referees are terrible. Worst officiating I've seen all season."

### Uncertain Example

"The referees clearly favored Boston tonight."

---

## Label 4: Information Seeking

### Definition

A post whose primary purpose is asking a genuine question or requesting information.

### Clear Example 1

"Can someone explain how Bird Rights work?"

### Clear Example 2

"Why do NBA teams intentionally foul near the end of games?"

### Uncertain Example

"Should the Lakers trade for another center?"

---

# Hardest Edge Case

### Example

"LeBron is overrated because his playoff record against top-seeded opponents is below .500."

### Possible Labels

- Analysis
- Hot Take

### Decision Rule

If the evidence forms part of a structured argument with multiple supporting points, the post will be labeled **Analysis**.

If the evidence is only used to strengthen a provocative opinion without additional reasoning, it will be labeled **Hot Take**.

---

# Mutual Exclusivity

These labels are designed so that each post belongs to exactly one category.

| Post Type | Assigned Label |
|------------|----------------|
| Uses evidence and reasoning | Analysis |
| Unsupported opinion | Hot Take |
| Emotional response | Reaction |
| Genuine question | Information Seeking |

Priority Rules:

1. If the primary purpose is asking a question, label it **Information Seeking**.
2. Otherwise, if the post contains substantial evidence and reasoning, label it **Analysis**.
3. Otherwise, if the post mainly expresses emotion, label it **Reaction**.
4. All remaining opinion-based posts become **Hot Take**.

---

# Why These Labels Matter

NBA discussions contain many different styles of communication. Some users support their opinions with statistics and logical reasoning, while others simply react emotionally or make bold predictions. By distinguishing between Analysis, Hot Take, Reaction, and Information Seeking, the classifier can better capture the quality and intent of basketball discussions rather than simply identifying whether a post is positive or negative.
