# AML Football Evaluation

## Mission & Purpose
AML Football sits at the intersection of football, machine learning, and mathematics. Inspired by the principles of *Moneyball*, the platform uses AI and data science to break down what makes teams win and discover hidden patterns inside the beautiful game. This is not for gambling, but rather to give football fans, analysts, data professionals, and ML/AI enthusiasts a deep statistical perspective on what to expect from a match before it kicks off. 

This repository contains the evaluation notebooks for the **Laliga** and **Serie A** models. The evaluation focuses heavily on goal-related predictions, but the vision extends further into position predictions, player heatmap forecasting, and more.

---

## Test & Evaluation Results

Extensive testing was carried out to evaluate the reliability of the AML Football system. Predicting exact match outcomes in football is notoriously difficult, so the focus shifted to predicting goals and managing the margins of error. The evaluation was carried out on test data (unseen matches) representing the last ten percent of games played by each team in the dataset.

### 1. Initial Accuracy for Three-Way Outcome
The initial attempt involved predicting win, lose, or draw (W/L/D). 
- **La Liga Model:** 42% accuracy
- **Serie A Model:** 47% accuracy

Because this three-way prediction fell below a reliable accuracy threshold for real-world performance, the platform pivoted away from outright match prediction toward predicting goal output and intervals.

### 2. Regression Metrics
To measure how accurately the model predicts goals, two standard regression metrics were computed for home and away goals:
- **Mean Absolute Error (MAE):** Represents the typical error per match (average goals off). The MAE is approximately 0.96-0.99 for La Liga and 0.86-0.88 for Serie A.
- **Root Mean Squared Error (RMSE):** Gives more weight to larger mistakes. The RMSE ranges between 1.07 and 1.33.

These metrics indicate that if the model predicts 2 goals for a team, the actual result is most often within a margin of 1 (i.e., 1 or 3 goals).

### 3. Acceptable Prediction Rate
Football is filled with unpredictable events. To measure systemic accuracy, we evaluated how consistently the model predicted actual goals within a margin of **+1 and -1 goals**.
- **La Liga 0, +1 & -1 Error Accuracy:** ~80%
- **Serie A 0, +1 & -1 Error Accuracy:** ~87%

---

## Matches Segmentation

Because teams exhibit different levels of reliability and consistency, matches are segmented based on the total combined prediction error recorded for the participating teams:

*   **A. Excellent Matches**  
    The most predictable tier. The model has identified highly consistent patterns for both teams. A match is classified as *Excellent* when the combined count of unique prediction errors across both teams is **3 or fewer**.
*   **B. Medium Matches**  
    Somewhat predictable but less consistent. They carry a wider error distribution and goal interval. The combined count of unique prediction errors falls between **4 and 5**.
*   **C. Low Matches**  
    Teams with highly unpredictable scoring patterns and diverse prediction errors. The system intentionally gives these games wide goal intervals (e.g., 0–7 or 0–9). The combined error count is **6 or above**.

---

## App Features & Guide

### Match Summary
The platform offers a short "most probable" summary for the game:
1.  **AI Analyses:** Recommends the best and safest outcome based on the percentage likelihood of the most probable scenario.
2.  **Goals Prediction Summary:** Surfaces the single most likely option across total over/under goals, total goals interval, and individual goal intervals.

### Full AI Forecast
A breakdown of all probabilities assigned to different match scenarios, including over/under margins and exact goal intervals. The **total goal interval** is the most reliable indicator, while individual team intervals can be explored at the team-insight level.

*Example:* Analysis might state an 86% probability that teams score 3 to 4 goals combined, but a 99.9% probability they score from 2 to 5 goals. The forecast helps define the "safe zones" of statistical likelihood.

---

## App Limitations & Risks

The model's reliability drops significantly during **unexpected in-game events**, such as:
- Early red cards
- Unusual weather conditions
- Out-of-the-ordinary goal outbursts (especially from the home team)

Even a match classified as *Excellent* is not immune to unpredictable occurrences. The segmentation strictly reflects historical pattern reliability—not a guarantee of outcome. 

**Conclusion:** AML Football proves the concept that AI can offer a measurable, reliable edge to understanding football matches pre-kickoff. The unpredictability of football isn't a problem to be solved; it's what makes the game beautiful. This platform simply helps you understand it better.
