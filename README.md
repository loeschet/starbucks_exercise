# starbucks_exercise

Take-home Data Science exercise for Starbucks applicants, provided in the [Udacity Data Scientist Nanodegree](https://www.udacity.com/course/data-scientist-nanodegree--nd025) course.

## Introduction

The task is to analyze an A/B test of a promotion with customers which got sent a promotional offer to buy a product and a control group which did not receive the promotion.

The first task is to analyze whether the experiment had a significant impact on purchasing behaviour and to compute the incremental response rate (IRR) and net incremental revenue (NIR). The second task is to build a model to select the best customers to target in order to further increase NIR and IRR based on customer data containing 7 features.

Further details and my results can be found in the main jupyter notebook: `Starbucks.ipynb`.

## Recommended software stack

I recommend to use an up-to-date `python` data science software stack to run the notebook. In particular, the following packages must be available:

- numpy
- scipy
- pandas
- scikit-learn
- matplotlib
- catboost

## Results

We saw that the response rate is significantly higher for the treatment group when compared to the control group. However, when computing the NIR, we saw that the incremental effect is too small to make up for the cost of sending out the promotion. That is, Starbucks would be loosing money with the current promotion strategy.

Looking at the feature distributions, we also saw that purchasing behaviour was significantly different in control and treatment groups. Given this observation and the fact that selecting customers in the treatment group that actually purchased the product has the highest impact on NIR, I chose to train a simple linear model on the training data, but only on customers in the treatment group. Evaluating the results on the test set (now again on treatment and control groups combined) yielded an improved result of an NIR of 276.30$ while retaining an IRR of 1.92%. However, there is a rather thin "peak" where good performance in terms of NIR is achieved and thus performance depends on cautious selection of the model output threshold. Results on a real-world dataset might change, or datasets might shift over time which makes constant model observation necessary.

Thus, I also tested the same approach using a `catboost` model. The results improved significantly over the simple linear logistic regression model, with an IRR of 1.98% and an NIR of 478$. In addition, the range of model output thresholds where we achieve a positive NIR is much broader than in the linear model and thus seems like a more stable and reliable result for a production model.

## Licensing, Authors, Acknowledgements

All data used in this exercise is based on simulated data provided by Starbucks.

And that's it! I hope you find this exercise interesting. Feel free to explore beyond what I did. Also, feel free to reach out if you are experiencing any bugs or have questions about the current code. Happy coding!