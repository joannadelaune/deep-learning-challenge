# Neural Network Analysis

### Overview

The purpose of this analysis is to investigate whether we can predict the success of applicants for funding from the Alphabet Soup foundation, using a dataset of historical information about past funding recipients and whether or not they were successful.

### Files

[Initial Model with Data Preprocessing](https://github.com/joannadelaune/deep-learning-challenge/blob/main/AlphabetSoup_Initial_Model.ipynb)

[Optimized Model](https://github.com/joannadelaune/deep-learning-challenge/blob/main/AlphabetSoupCharity_Optimization.ipynb)

### Discussion

#### Target and Features

The **IS_SUCCESSFUL** variable is our target. Our features are:
* APPLICATION_TYPE
* AFFILIATION
* CLASSIFICATION
* USE_CASE
* ORGANIZATION *(Note -- this is a type and not a proper name)*
* STATUS
* INCOME_AMT
* SPECIAL_CONSIDERATIONS
* ASK_AMT

The EIN and NAME of the organizations are irrelevant in our analysis and are removed in advance.

I began with two layers of 500 and 250 neurons using the ReLU activation function because it is a good all-purpose choice.

I started with 50 epochs and figured I could dial back if that was too many.

The model came out at 72.9% accuracy and, interestingly, it seemed to reach that point after only the first few epochs. As a result, I concluded immediately that adding *more* epochs was not going to help.

I did some further investigation of the data and found that there were only a tiny number of values (less than 10 each) in the STATUS and SPECIAL_CONSIDERATIONS columns that differed from the rest of the data. So I decided to drop those two columns because realistically they were not adding much if anything to the analysis.

I also re-binned the Classification Types. While there were a great many CLASSIFICATION entries that had only one value in the whole dataset, I kept everything else in its own classification the second time around and grouped the singles together in an 'Other' category.

The model's accuracy improved... to 73.1%. And again it didn't improve much after the first few epochs.

So I tried again with a 3rd hidden layer and more nodes in each of the three layers, this time with only 10 epochs to save time.  Still a very similar result, but the model seemed to still be learning after 10 iterations, so I tried more epochs again and got to 73.48%.

It was interesting that no matter what I tried the accuracy of the model didn't change much. I suppose I didn't hit on the right things to change.  Possibly a different model altogether could be helpful. Random forests is useful for being able to see how much individual things contribute to a prediction and could be interesting to try here.





