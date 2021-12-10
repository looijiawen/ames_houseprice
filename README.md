# Project 2 - Predicting Ames Housing Prices with Regression


## **Background**<br> 

House prices predictions are useful for *homebuyers* (primary stakeholder) plan their purchase for an ideal house and finances to buy a house. Being able to identify features which the value of the house is sensitive to, they may be in a better position to negotiate price. In addition, house price predictions are also beneficial for *homeowners* (secondary stakeholder) decide how they may want to renovate their houses to improve its marketability and sale price. 

## **Problem Statement**  <br> 
    
- How may homebuyers in Ames identify houses which have great appreciation value? <br>
- How may homesellers in Ames improve the values of their house? <br>

## **Objective** <br> 

With a [Ames Housing Dataset](https://www.kaggle.com/c/dsi-us-11-project-2-regression-challenge/data) from Kaggle, which consists of 2051 sold houses in Ames, where each of these houses have 80 features ([Data Dictionary](http://jse.amstat.org/v19n3/decock/DataDocumentation.txt)) that we will leverage upon to find patterns and correlations, we want to -</span>
   
    
- **identify features** which significantly affect housing prices
- **accurately** predict housing prices using those features
- build a **generalizable^** regression model to accurately predict housing prices <br>(i.e. ^model should be able to adapt to different sets of test data, and predict housing prices with a decent accuracy)
- identify features of a house which affects its value



**Evaluation** of model performance by -
    
    
1. coefficient of discrimination (R2 Score) 
2. root-mean-squared-error (RMSE)


## **Conclusions**
    
The Lasso model we have designed made a significant improvement as compared to the Baseline Model:

| Model: | Baseline | Lasso |
| --- | --- | --- | 
| R2 Score | 0.840 | 0.9183 |
| RMSE | 31609 | 21195 |


This addresses our problem statement of building a model to accurately predict housing prices.

## **Recommendations**

Perhaps, knowing the factors that will influence the house price may more valuable than the price predictions.
    
![Lasso Coefficients](https://github.com/looijiawen/ames_houseprice/blob/main/datasets/Lasso%20Coefficients.png)

10 unique house features might be **positively correlated** with our house prices:
    
- Above Grade (ground) Living Area (square feet)
- Overall Quality 
- Basement (Type 1) Finished Area (square feet)
- Garage Area
- Overall Condition
- Typical Functionality 
- Brick Face Exterior Covering on house
- Number of Fireplaces
- Good Basement Exposure

We found that the top 3 features positively correlated with SalePrice are Ground Living Area, Overall Quality, as well as Basement Finished Area. In other words, these features, when present in greater magnitude, are likely to produce higher SalePrice. For example, a house with a higher Overall Quality would likely fetch a higher price than a house with a lower overall Quality. 

Homeowners may be more inclined to improve on the housing features that are generally amenable. E.g.:

- Select a better material and finish of the house to improve Overall Quality
- Basement (Type 1) Finished Area (square feet)
- Have a larger garage space (area)
    

5 unique house features might be **negatively correlated** with our house prices:
- AgeSold (in Years)
- External Quality Material: Average/Typical
- Kitchen Quality: Average/Typical
- Kitchen Quality: Good
- Class D Neighborhood

In other words, according to the observations drawn from the dataset, houses with such features are likely to fetch lower prices. 

While Age and Class D Neighborhood are unsurprising, the External Quality & Kitchen Quality are somewhat unusual. It is plausible that Ames’ citizens (for some reason) emphasize greatly on the house’s exterior material and kitchens, the category of Average/Typical is not expected. This implies that even houses with poor Exterior material or kitchen quality might somehow fetch higher prices than houses with average exterior material or kitchen, which does not make logical sense. A possible reason for this phenomenon could be that given the small size of our dataset (which only has slightly more than 2k+ houses), we do not have sufficient data points in the other categories to verify the correlation.

Two-cents worth for homebuyers:

- Avoid old houses in class D neighborhoods
- Buy houses that are built not too long ago, since prices deteriorate with age

## **Caveats**


Sensitive to context; Our model is unlikely to be generalizable to other cities. The features we chose to build the model might not be the most ideal selection to determine house prices, because we did not have enough domain knowledge to perform manual feature selection.  In reality, two populations in different cities or countries may not share the same considerations for desirable features in a house. 

To make the model more generalizable, we could cut down on the number of variables and use only general features found and assessed within most houses in the world, such as distance to a transport system. This would of course come at an expense of the predictive power of the model.
