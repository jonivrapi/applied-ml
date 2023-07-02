-Do you find the model predictions for the digit images as successful? Would you deploy the developed ML model now that you see the performance?
 
Answering this question, in my opinion, requires knowing a lot about how the model would be used in the real world. This model was trained on roughly 850 samples of a hand-curated data set from 20 years ago, which contains images that are 64 pixels in resolution. A lot has changed in 20 years. People's handwriting has changed, cameras have changed, and this dataset is not broadly indicative of the entire problem space of handwritten characters across cultures and writing styles.
 
While I do find the predictions for the digit images to be successful, I do so only within the context of this dataset. We did not perform the full gamut of testing involving looking at our validation accuracy, recall, f1 score, etc. We must also compare the accuracy of this model to the previous way mail was sorted. Is 97% accuracy (on single digit recognition, zip codes have a minimum of 5 digits, so real life accuracy is much lower -> [0.97^5, 0.97^9] or roughly 76%-86% accurate on identifying a full zip code) better than the person/machine that was sorting the mail before? If it was, is that enough information to make a decision on deploying this model? 
 
I personally would not deploy this model until the training dataset was much larger, more current and diverse, and the accuracy of recognizing digits was substantially higher. 
    
-Your customer requests the model you just developed. What should be the steps you conduct before model delivery?
 
Before delivering this model, I would need to make sure the client fully understands how I evaluated the performance of the model, and on which kind of data it was trained. I would also like to perform an analysis of how/where/when it makes mistakes, hopefully identifying a bounding-box of sorts that I could articulate to the client such that the model is well understood and not misused.
 
On the practical side of delivery, there would of course need to be lots of documentation, as well as production level code quality and tests, and an environment with which the model can be deployed and hosted. There would also need to be API's that allow the outside world to interface with the model.
    
-Before model delivery, will you train the model with all the available data?
 
I would first run experiments, likely by stepping up the proportion of the training data that was used in 10% increments, to see if I could squeeze any more performance from the model while not over-fitting it to this particular dataset. If it turned out to be true that some mix other than 50/50 was more performant, I would deliver a model trained on that proportion. I would likely not ever train this particular model on all of the available data due to the fact that there are only 1700 or so records to train off of. Such little data indicates that the data does not cover a wide range of digit variations which already increases the risk of overfitting. Using all the data to train further increases that risk. 