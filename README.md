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

Chapter 5 of *Ethical Machines* is about why most AI ethics statements accomplish nothing. Blackman's sharpest example is fairness: it appears on nearly every corporate list, and it is so abstract that even the Ku Klux Klan would claim to value it. A principle everyone can endorse rules nothing out, and a principle that rules nothing out never blocks a decision.

The problem that stayed with me is his second one — that organizations fold ethical values together with engineering ones, then score well on accuracy, security, and reliability and conclude they have handled ethics. He recounts companies whose "Responsible AI" program turns out, under questioning, to be model testing and cybersecurity. I recognized that from this course. In Module 04 the model excluded the protected attribute entirely, exactly the kind of box a technical checklist marks complete, and it still predicted 12.8 points lower for one group because zip code carried the same information. In Module 06, three coarse fields re-identified 42% of an "anonymized" dataset, every match correct. Neither failure would show up as a defect on an engineering dashboard.

Blackman's remedy is to start from your ethical nightmares instead of your aspirations, and then say concretely what is off the table. I think that ordering is right, and it is the part I expect to carry into my own work. "We value fairness" costs nothing to say. "We will not ship a model before measuring its outcomes across groups" is a sentence that can be broken — which is the only reason it is worth writing down.
