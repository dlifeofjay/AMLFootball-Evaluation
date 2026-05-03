# AML Football Evaluation

## Mission & Purpose
AML Football sits at the intersection of football, machine learning, and mathematics. Inspired by the principles of *Moneyball*, the platform uses AI and data science to break down what makes teams win and discover hidden patterns inside the beautiful game. This is not for gambling, but rather to give football fans, analysts, data professionals, and ML/AI enthusiasts a deep statistical perspective on what to expect from a match before it kicks off. 

This repository contains the evaluation notebooks for the **Laliga** and **Serie A** models. The evaluation focuses heavily on goal-related predictions, but the vision extends further into position predictions, player heatmap forecasting, and more.

---

## Test & Evaluation Results

Extensive testing was carried out to evaluate the reliability of the AML Football system. Predicting exact match outcomes in football is notoriously difficult, so the focus shifted to predicting goals and managing the margins of error. The evaluation was carried out on test data (unseen matches) representing the last ten percent of games played by each team in the dataset.

### 1. Initial Accuracy for Three-Way Outcome
The initial attempt involved predicting win, lose, or draw (W/L/D). 
- **La Liga Model:** 44% accuracy
- **Serie A Model:** 49% accuracy

Because this three-way prediction fell below a reliable accuracy threshold for real-world performance, the platform pivoted away from outright match prediction toward predicting goal output and intervals.

### 2. Regression Metrics
To evaluate how accurately the model predicts goals, we used two standard regression metrics:
- **Mean Absolute Error (MAE):** Measures the average absolute difference between predicted and actual goals (average margin of error per match).
- **Root Mean Squared Error (RMSE):** Penalizes large errors more heavily, providing insight into the magnitude of prediction misses.

| League | Metric Type | Home Goals | Away Goals |
| :--- | :--- | :--- | :--- |
| **La Liga** | MAE | 0.90 | 0.93 |
| | RMSE | 1.14 | 1.21 |
| **Serie A** | MAE | 0.90 | 0.91 |
| | RMSE | 1.10 | 1.12 |

These results indicate that if the model predicts 2 goals for a team, the actual result is typically expected to be 1 or 3 goals.

### 3. Acceptable Prediction Rate
Football is filled with unpredictable events. To measure systemic accuracy, we evaluated how consistently the model predicted actual goals within a margin of **+1 and -1 goals**.
- **La Liga Home Goals 0, +1 & -1 Error Accuracy:** ~83%
- **La Liga Away Goals 0, +1 & -1 Error Accuracy:** ~79%
- **Serie A Home Goals 0, +1 & -1 Error Accuracy:** ~84%
- **Serie A Away Goals 0, +1 & -1 Error Accuracy:** ~83%

### 4. Total Match Error
To evaluate overall match-level accuracy, we measured the combined absolute error across both home and away goal predictions per match. This metric shows how often the model's total goal prediction lands within an acceptable range of the actual outcome.
- **La Liga:** 92.9% of matches fall within a combined error of 3 goals or less
- **Serie A:** 92.5% of matches fall within a combined error of 3 goals or less

---

## App Features & Guide

### Match Summary
This section contains a short most probable summary for the entire game:
1.  **AI Analyses:** The AI reviews all predictions and recommends the best and safest outcome based on the percentage likelihood of the most probable scenario.
2.  **Goals Prediction Summary:** Surfaces the single most likely option covering total over/under goals, the total goals interval, and the individual goal interval for each team.

### Full AI Forecast
A full breakdown of the probabilities assigned to different match scenarios. While it covers several metrics, we recommend focusing on the **total goal interval** as it tends to be the more reliable indicator. Individual team intervals are best explored via the Team Insight section.

#### Analysis Breakdown Example:
Using the system's probability outputs, the data can be interpreted as follows:
*   **Over/Under Section:** "There is a 99.9% probability that the match will have over 1 goal and over 2 goals. However, there is only a 24% chance it will *not* produce 4 or more goals, meaning there is a 76% chance the total goals will be 4 and above."
*   **Total Goals Interval:** "There is a 62% chance the match will have exactly 4 goals, an 86% chance of 3 to 4 goals, and a 99.9% chance the result falls within 3 to 5 goals."

---

## App Limitations & Risks

The model's reliability drops significantly during **unexpected in-game events**, which fall outside the patterns the model was trained to recognize:
- Early red cards
- Unusual weather conditions
- Unusual goal outbursts (particularly from the home team)

Even a match showing highly consistent historical patterns is not immune to these unpredictable occurrences.

---

## Conclusion
AML Football was built on a simple but ambitious idea: that mathematics and machine learning can give football fans and analysts a clear expectation of what to see before a match kicks off.

Version one proves the concept with an Acceptable Prediction Rate averaging approximately 81% for La Liga and 83% for Serie A, with over 92% of matches in both leagues falling within a total combined error of 3 goals or less. For this initial phase, performance is judged primarily on the accuracy of the LLM recommendations in matches where teams show consistent and predictable patterns.

The unpredictability of football is not a problem to be solved—it's what makes the sport worth watching. AML Football doesn't claim to remove that uncertainty; it simply helps you understand it better.
