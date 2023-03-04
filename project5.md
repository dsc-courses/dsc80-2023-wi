---
layout: page
title: Project 5
description: Description of Project 5.
nav_exclude: true
---

<script src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML" type="text/javascript"></script>


# Project 5 – Model Building 🛠
{:.no_toc}

### Due Date: Thursday, March 23rd at 11:59PM (NO SLIP DAYS!)
{:.no_toc}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

{: .warning }
If you've somehow come across this page already, it's **not** ready.

---

## Overview

Welcome to Project 5, the final assignment of the quarter! 👋

In Project 5, you will conduct an open-ended investigation into the dataset you chose for [Project 3](https://dsc80.com/project3) (Recipes and Ratings, League of Legends, or Power Outages). **Specifically, you will pose a prediction problem and train a model to solve it.** Use the [Example Prediction Problems](#example-prediction-problems) section for inspiration.

**Project 5 is due on Thursday, March 23rd at 11:59PM. This is a hard deadline; you may NOT use slip days on this project.** This is because we need to start grading projects right when you turn them in, so that there is enough time for you to make regrade requests before we submit grades to campus.) Note that we will not be able to hold many office hours during Finals Week, so make sure to start early.

Like Project 3, there is no checkpoint. Also, like in Project 3, you'll need to submit both a notebook and report.

---

## Part 1: Analysis

Before beginning your analysis, you'll need to set up a few things.
1. Pull the latest version of the [`dsc80-2023-wi`](https://github.com/dsc-courses/dsc80-2023-wi/) repo. Within the `projects/05-prediction` folder, there is a `template.ipynb` notebook that you will use as a template for the project. If you delete the file or want another copy of the template, you can re-download it from [here](https://github.com/dsc-courses/dsc80-2023-wi/blob/master/projects/05-prediction/template.ipynb). **This is where your analysis will live; you will submit this entire notebook to us.**
2. Load the dataset you chose for Project 3 into your template notebook.

Once you have your dataset loaded in your notebook, it's time for you to find meaning in the real-world data you've collected! Follow the steps below.

***Tip***: For each step, we specify what must be done in your notebook and what must go on your website. We recommend you write everything in your notebook first, and then move things over to your website once you've completed your analysis.

### Requirement: Framing the Problem (15%)

| Step | Analysis in Notebook | Report on Website |
| --- | --- | --- |
| **Problem Identification** | Frame a prediction problem(including any further data cleaning you might need towards your problem).| Clearly state your prediction problem and type(classification or regression). If you are building a classifier, make sure to state whether you are performing binary classification or multiclass classification. Report the response variable (i.e. the variable you are predicting) and why you chose it, the metric you are using to evaluate your model and why you chose it over other suitable metrics (e.g. accuracy vs. F1-score). <br><br>***Note***: Make sure to justify what information you would know at the "time of prediction" and to only train your model using those features. For instance, if we wanted to predict your final exam grade, we couldn't use your Project 5 grade, because Project 5 is only due after the final exam! |

### Requirement: Baseline Model (35%)

| Step | Analysis in Notebook | Report on Website |
| --- | --- | --- |
| **Baseline Model** | Train a "baseline model" for your prediction task that uses at least two features. You can leave numerical features as-is, but you'll need to take care of categorical columns using an appropriate encoding. Implement all steps (feature transforms and model training) in a `sklearn` `Pipeline`. <br><br>***Note***: **Both now and in Final Model Step, make sure to evaluate your model's ability to generalize to unseen data!** <br><br>There is no "required" performance metric that your baseline model needs to achieve. | Describe your model and state the features in your model, including how many are quantitative, ordinal, and nominal, and how you performed any necessary encodings. Report the performance of your model, and whether or not you believe your current model is "good" and why. |

### Requirement: Final Model (35%)

| Step | Analysis in Notebook | Report on Website |
| --- | --- | --- |
| **Final Model** | Create a "final" model that improves upon the "baseline" model you created in Step 2. Do so by engineering at least two new features from the data, on top of any categorical encodings you performed in Baseline Model Step. (For instance, you may use `StandardScaler` or `QuantileTransformer` transformers on quantitative columns.) Again, implement all steps in a `sklearn` `Pipeline`. While deciding what model and features to use, you **must** perform a search for the best model and hyperparameters (e.g. tree depth) to use amongst a list(s) of options, either by using `GridSearchCV` or through some manual iterative method. <br><br>***Note***: You will not be graded on "how much" your model improved from Baseline Model Step to Final Model Step. What you will be graded on is on whether or not your model improved, as well as your thoughtfulness and effort in creating features, along with the other points above. | State the features you added and **why** they are good for the data and prediction task. Describe the model you chose, the hyperparameters that ended up performing the best, and the method you used to select a model. Report the improvement of your model.|


### Requirement: Fairness Analysis (15%)

| Step | Analysis in Notebook | Report on Website |
| --- | --- | --- |
| **Fairness Analysis** | Perform a "fairness analysis" of your final model from Step 3. That is, try and answer the question "does my model perform worse for individuals in Group X than it does for individuals in Group Y?", for an interesting choice of X and Y.<br><br>As always, when comparing some quantitative attribute (in this case, something like precision or RMSE) across two groups, we use a **permutation test**. Let's illustrate how this works with an example. Let's suppose we have a sample voter dataset with columns `'Name'`, `'Age'`, and `'Voted'`, among others. We build a classifier that predicts whether someone voted (`1`) or didn't (`0`).<br><br>Here, we'll say our two groups are <br><br>- "young people", people younger than 40 <br><br>- "old people", people older than 40<br><br>Note that in this example, we manually created these groups by **binarizing** the `'Age'` column in our dataset, and that's fine. (Remember, the `Binarizer` transformer with a threshold of 40 can do this for us.)<br><br>For our evaluation metric, we'll choose precision. (In Lectures we looked at other evaluation metrics and related parity measures for classifiers; choose the one that is most appropriate to your prediction task. If you built a regression model, you cannot use classification metrics like precision or recall; instead, you must use RMSE or $$R^2$$.)<br><br>Now, we must perform a permutation test. Before doing so, we must clearly state a null and an alternative hypothesis.<br><br>- Null Hypothesis: Our model is fair. Its precision for young people and old people are roughly the same, and any differences are due to random chance.<br><br>- Alternative Hypothesis: Our model is unfair. Its precision for young people is lower than its precision for old people.<br><br>From here, you should be able to implement the necessary permutation test. The only other guidance we will provide you with is that you should **not** be modifying your model to produce different results when computing test statistics; use only your final fitted model from Final Model Step. | Clearly state your choice of Group X and Group Y, your evaluation metric, your null and alternative hypotheses, your choice of test statistic and significance level, the resulting $$p$$-value, and your conclusion.<br><br>***Optional***: Embed a visualization related to your hypothesis test in your website.<br><br>***Tip***: When making writing your conclusions to the statistical tests in this project, **never** use language that implies an absolute conclusion; since we are performing statistical tests and not randomized controlled trials, we cannot prove that either hypothesis is 100% true or false.<br><br>_“Only a Sith deals in absolutes” - Obi-Wan Kenobi_ | 

### Style

While your website will neatly organized and tailored for public consumption, it is important to keep your analysis notebook organized as well. Follow these guidelines:
* Your work for each of the three project sections (Baseline Model, Final Model, and Fairness Analysis) described above should be completed in code cells underneath the Markdown header of that section's name.
* You should **only include work that is relevant** to posing, explaining, and answering the problem(s) you state in your report. You should include data quality, cleaning, though these should broadly be relevant to the question at hand.
* Make sure to clearly explain what each component of your notebook **means**. Specifically:
    - All plots should have titles, labels, and a legend (if applicable), even if they don't make it into your website. Plots should be self-contained – readers should be able to understand what they describe without having to read anything else.
    - All code cells should contain a comment describing how the code works (unless the code is self-explanatory – use your best judgement).

---

## Part 2: Report

The purpose of your website is to provide the general public – your classmates, friends, family, recruiters, and random internet strangers – with an overview of your project and its findings, without forcing them to understand every last detail. We don't expect the website creation process to take very much time, but it will certainly be rewarding. Once you've completed your analysis and know _what_ you will put in your website, start reading this section.

Your website must clearly contain four headings:
- Framing the Problem
- Baseline Model
- Final Model
- Fairness Analysis

The specific content your website needs to contain is described in the "Report on Website" columns above. Make sure to also give your website a creative title that relates to the question you're trying to answer, and clearly state your name(s).

Your report will be in the form of a _static_ website, hosted for free on GitHub Pages. More specifically, you'll use [Jekyll](https://jekyllrb.com), a framework built into GitHub Pages that allows you to create professional-looking websites just by writing Markdown ([dsc80.com](https://dsc80.com) is built using Jekyll!). GitHub Pages does the "hard" part of converting your Markdown to HTML.

---

## Example Prediction Problems

Below, we provide example prediction problems for all three datasets. However, don't restrict yourself to just these – feel free to come up with your own!

### Recipes and Ratings 🍽

* Predict ratings of recipes.
* Predict the number of minutes to prepare recipes.
* Predict the number of steps in recipes.
* Predict calories of recipes.

### Power Outages 🔋

* Predict the severity (in terms of number of customers, duration, or demand loss) of a major power outage.
* Predict the cause of a major power outage.
* Predict the number and/or severity of major power outages in the year 2022.
* Predict the electricity consumption of an area.

### League of Legends Competitive Matches ⌨️

* Predict if a team will win or lose a game.
* Predict which role (top-lane, jungle, support, etc.) a player played given their post-game data.
* Predict how long a game will take before it happens.
* Predict which team will get the first Baron.

---

## Grading and Submission

Unlike in Project 3, we will **not** be providing you with the exact rubric that we will evaluate your report on. This is because an exact rubric would specify exactly what you need to do to build a model, but figuring out what to do is a large part of the project. (However, you can see how much each step is worth in the headings above.)

With that said, **you will be graded on addressing all of the above requirements in your summary.** You should have your code included at bottom in a clearly done, commented fashion. Upon reading the summary, it should be easy for the grader to glance down at the code to see the supporting work.

To submit the project, generate a **PDF of your Jupyter Notebook** that contains all of the requirements above, and upload that PDF to Gradescope. You will not need to upload the raw notebook to Gradescope. Notes:
- While working, you may keep your code in a `.py` file and import it if you'd like. Just (1) be sure the output is clearly visible in the notebook, and (2) copy and paste the code from the file to the *very* bottom of the notebook before submitting.
- To export your notebook as a PDF, first, restart your kernel and run all cells. Then, go to "File > Print Preview". Then, save a print preview of the webpage as a PDF. There are other ways to save a notebook as a PDF but they may require that you have additional packages installed on your computer, so this is likely the most straightforward.
- There are three "Project 5" assignments on Gradescope, one for each dataset. Make sure to submit to the correct one, and to tag your partner!
- A final reminder – **you cannot use slip days on Project 5**!
