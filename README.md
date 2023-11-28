## Challenge: machine failure prediction

Challenge for a DS position in the field of machine failure prediction.

--- 

Applicant name: **Mauricio Branbilla Junior**

--- 

### Challenge description

To enable the operations of an FPSO, we use sensors to make sure the equipment does not fail. These sensors measure different parameters of the equipment in different setup configurations (preset 1 and preset 2) over time. We want you to investigate one piece of equipment in different time cycles to understand what characteristics and parameters of the sensors might indicate that the equipment is on the verge of failing. To solve this problem, we expect you to answer a few questions regarding the attached dataset:

    1 – Calculate how many times the equipment has failed.

    2 – Categorize equipment failures by setups configurations (preset 1 and preset 2).

    3 – Categorize equipment failures by their nature/root cause according to parameter readings (temperature, pressure, and others).

    4 – Create a model using the technique you think is most appropriate and measure its performance.

    5 – Analyze variable importance.



**Few Tips:**

Please write down any insights and conclusions throughout your code when you think it is necessary, keeping them as clear and complete as possible. Think of this exercise as your first technical report.
We value clean, concise, and production-ready code.
Once you’re done, please send us your analyses and answers in an Html notebook, but also other conclusions and insights that you think are relevant to the project. We value creativity!
Feel free to discuss how you think you would put the models in production.


**What do we expect you to do:**

Present storytelling of data and analyses performed.
Problem comprehension.
Data exploration.
Logic and concise model definition.
Rationale explanation.
Results evaluation.


**What you DON'T need to do?**

Super complex models with no logic or rationale behind them.

---

### Some notes about my solution:

**What will be my approach?**

Keeping in mind the bias-variance tradeoff and the fact of the dataset has just a few predictors, I'll look for the simplest model (i.e. with the less complexity as possible) that can leads to satisfatory predictions. Given that, I'll test two models:

- (A) Logistic Regression: a linear classification model
- (B) Randon Forest: a non-linear (tree-based) classification model

The choose between these models will be done by comparing the performance metric. If the performance metrics are similar, we'll choose that have lower complexity (in this case, the Logistic Regression Model) - in other words, we just choose a more complex model if we have a realistic gain in that approach. Both of these models will give a inference of the probability of failure.


**What are the performance metrics that I'll use?**

One fact about the provided dataset is that the data is **unbalanced** (about 8.25% of the data was labeled as failure). 

Looking for the costs envolved in machinary maintence and thinking about the impact of false negatives or false positives classifications at this cost:

- False positives means that the preventive maintenance may be done without needed
- False negatives means that the preventive maintenance will not be done and the equipment may presents a failure, reprensenting a corrective maintence cost - this cost tends to be significant higher than the preventive maintenance and we want to avoid that.

Given that poits, we want to be focused in reduce the false negative rate (i.e. the sensibility). Given that, the PR AUC Score (Area Under Precision-Recall Curve) might be more adequated than ROC AUC Score for this case. 

---





