AI201 Project 3 – TakeMeter
Community

Chosen Community: r/nba (Reddit NBA Community)

Why this community?

I chose r/nba because it is one of the largest and most active basketball discussion communities on Reddit. Every day, users post game reactions, player evaluations, trade discussions, statistical analyses, and questions about the NBA. This variety makes it an excellent dataset for a text classification project because posts naturally differ in both content and writing style.

The community is also a good fit because there are meaningful differences between evidence-based basketball analysis and unsupported opinions. These distinctions matter to regular members of the community and create a realistic machine learning classification task.

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
