# code_3000
Collection of Assignments for CSE 3000: Contemporary Issues in Computer Science and Engineering

_Note_: Odd-numbered assignments are in HuskyCT, while even-numbered assignments are found in this repo and can be submitted to Gradescope via a Github connection.

## Outline of Assignments

### Module 02: Bot Predictor
Your goal is to build a machine learning model using given data and a Python template. You'll make changes to the GradientBoostingClassifer in mod02_build_bot_predictor.py and then test your changes in mod02_test_bot_predictor.ipynb. Can you minimize the misclassification rate on the test set?

### Module 04: Model Bias
You are given a model that was built to predict a mystery variable using zip code, income, and education level. The variable "group" represents a demographic that is prohibited and was NOT used in the model. Your goal is to use the SHAP package to review this model for bias.

### Module 06: Data De-Anonymization
Your goal is to connect anonymized data back to its source data and check the match rate. To complete this activity, write functions in the "deanonymize" script to (1) link the records in the two datasets and (2) calculate the rate at which you are successful doing so. 

### Module 08: Sustainability in Computing
You will be given a toy dataset and have the opportunity to explore the potential effects of choosing sustainable energy sources to perform computations. You'll code the energy calculation in "sustainability calculations" script, and then you can review the results of various decisions in the "check calculations" notebook. 

## Personal Statement on Ethics

One thing that really stood out to me in Chapter 5 of *Ethical Machines* was Blackman's argument that most AI ethics statements are too vague to actually make a difference. A company can say it values fairness, but what does that really mean if the statement doesn't stop it from releasing a harmful system? I think his point is that ethics should be more than something companies say to make themselves look responsible. It should actually influence the decisions they make.

Before taking this course, I mostly thought about AI ethics in terms of having good intentions and trying not to build anything harmful. But the activities we worked on made me realize that even when nobody intends to cause harm, the technology can still produce unfair outcomes. For example, in Module 04, the model predicted 12.8 points lower for one group even though it never directly used the protected attribute. The zip code was basically acting as a substitute. In Module 06, we were able to re-identify 42% of an anonymized dataset using just three general pieces of information, and every match was correct. That honestly surprised me because I had assumed removing personal identifiers would make a dataset much safer.

These examples changed how I look at responsibility in AI development. I now think it's not enough for developers to say they care about fairness or privacy. They need to actually test their systems, look for possible biases, and consider who might be affected before releasing them. To me, an ethical commitment only means something if it can influence what gets built, changed, or even prevented from being released.
