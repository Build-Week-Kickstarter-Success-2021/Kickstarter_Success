![image](https://github.com/Build-Week-Kickstarter-Success-2021/Kickstarter_Success/blob/main/predictor_app/static/images/kickstarter.png)

# Kickstarter Successs Predictor

Our goal with this project is to help determine whether a kickstarter campaign will succeed or fail based on the initial product proposal, by having an app the user can enter their project's data into and recieve a predicted result of "success" or "failure".

## What is Kickstarter?

**Kickstarter** is a website that lets a user describe an event, product, or service they wish to produce, and lets them attempt to raise a target amount of money for the project by allowing donors to donate through their service over a limited campaign period.  If the goal is met, funds are then transfered to the user's team, and production begins.  If the goal is not met, no funds are given, and all donors are refunded, which allows donors to support projects they want to see succeed in a low risk enviornment.

## Success Predictor & Instructions

#### **[Our Website](https://kickstarter--predictor-rasp.herokuapp.com)**

Go to the link above.  From first drop down menu, select the category your project will fall under (Our model does not have enough data to predict categories outside of those listed).  Then, manually input your target goal in USD, and your campaign duration in days.  To convert your local currency to USD, you can use **[this currency converter](https://finance.yahoo.com/currency-converter)**, or use another of your choice.  Next, Select your country from the dropdown menu.  If it is not listed, select "Other".  Finally, click on the "Submit" button on the right.  Scroll to the bottom of the page, on the lower left, in a blue box, your prediction of "Success" or "Failure" will show, along with the precent chance out of one of the predicted result (so .88 would translate to an 88% chance).

## How it works

Our website takes the information you input, then feeds it to a model trained on Kickstarter data from 2014 to 2021, predicts whether it will reach its goal funding, then returns that result to you as either "Success" or "Failure" so you can know whether your project will be more likely to succeed, or fail.

## Our methods, model selection, and tuning

We used data obtained with https://webrobots.io/kickstarter-datasets/, then did data cleaning/feature engineering to remove leaky columns, expunge unneeded data, and add features to train on.  You can find these steps in our data wrangling notebook in this repsoitory.

We then trained and tested 6 different kinds of models:

* An **artificial neural network** with two hidden layers, optimized with dropout to prevent overfitting
* 3 **linear regression** models
    * A logistic regression model with train test split
    * A logistic regression model trained using cross validation
    * An SGD classifier model
* A **random forest** model
* The **XGBoost** gradient boost model

We first tested the untuned accuracies, the 3 linear regression models and the neural network model did not perform as well as the random forest and gradient boost models, so we decided to focus on the random forest and gradient boost models for tuning.

After tuning using random search, our gradient boost model was giving the best results, so we selected it as our final model for use in the deployed product.

## Information

---

#### MIT License

Copyright (c) 2021 Zachary Rock, Youssef Al-Yakoob, Fadil Shaikh, Mark Porath

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

---

#### Contact Information

##### Zachary Rock

* https://www.linkedin.com/in/zacharycrock/
* https://github.com/ZacharyRock
* crkosmos@gmail.com

##### Youssef Al-Yakoob

* https://github.com/yalyakoob
* https://www.linkedin.com/in/youssefalyakoob/
* yalyakoob@gmail.com

##### Fadil Shaikh

* https://github.com/scoding2
* www.linkedin.com/in/fadil-s-11544df
* fscoder12@gmail.com


##### Mark Porath

* https://github.com/m-rath
* https://www.linkedin.com/in/mark-porath
* m.rath.oh@gmail.com
