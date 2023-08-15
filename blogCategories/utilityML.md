# An ML Exploration of Utility Companies  

This project was an experiment in trying to use some basic machine learning techniques to create a trading strategy that performs better than random. This isn’t a coding or a math tutorial, it is an exploration of how we might be able to work with our data to make more accurate models. I will explain whatever math and code needed, but all you need is an interest to learn more about machine learning or trading strategies. With that, let’s get started !

## Premise
We want to build a trading strategy that accurately tells us when to buy or sell stock of major Utility Companies in the S&P 500. The reason we are choosing the Utilities industry is because there is relatively little differentiation in business models and products across companies. As a result, I hypothesize that a similar set of factors are most influential for the majority of companies in this industry. In an industry like tech on the other hand, the big players each have their own specialization and set of services. Microsoft and Amazon for example, have many differences between their business models and core services, so it would be harder to train an effective model on the industry as a whole.


## Getting Data
I retrieved the monthly data for 10 of the major utility companies in the S&P500 from 2000-2015. The data included 70 factors for each month including some common ones you’ve probably heard of like the PE and PEG ratios, as well as some more obscure metrics. I retrieved the data from the Wharton Research Database.

## Prepping Data
In order to create an accurate model, we need to “teach” our program when to buy and when to sell. To do this we will train our program on a part of our data that we have labeled. When I say label, I mean for each month we are literally going to place a buy or sell signal 1 or 0 based off of the change in price  in the next month. For example if the stock goes up 3%  from the current month to the next month  that means the current month will be labeled a buy : 1 . For example :

![image info](blog_images/LabeledData.png)

Just keep in mind that the actual data set we have 70 different factors and a dozen or so companies.  We will be storing all this labeled data in an output file simply named “outCopy.csv”  

One thing is left before we start building models, we need to normalize our data.  Currently you see that each factor is on a widely  different scale. pe_op_basic fluctuates between 10 and 15 while bm really stays at around 1.1-1.4, meaning that even small changes in it are potentially a big deal. However, the computer just sees numbers and as a result  may put undue weight on pe_op_basic as a factor in its prediction, simply because its numbers are larger. To avoid this we will subtract every value in each column by the minimum of that column and divide that value by the max of col - min col

![image info](blog_images/unNormalData.png)  ![image info](blog_images/normalizedData.png) 




