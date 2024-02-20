## Title

Elevator Pitch

Header image
## Business Problem:
(data, target, rationale), Using data, can we predict target? This would be useful because rationale.

It can be hard to continuously come up with new and interesting recipes to cook, especially if you have certain dietary restrictions. Many people use websites such as food.com to find, try, and rate recipes. From user and recipe data from Food.com, can we provide users with the top 3 recommendations for the next recipes that users should try, taking into account their dietary specifications?

From the user's point of view this could eliminate some of the work in finding new recipes that they will actually like. From the perspective of the business, providing more relevant reviews to users will lead to those users to favor our service more for finding recipes in the future.



This would be useful, because it can be time consuming and repetitive for people to come up with new recipes to make all the time, especially when their options are narrowed down due to dietary restrictions. If a recommender system took into account not only a user's preferences, based on past recipes that the user has rated highly, but also the type of diet category that the user is most likely to enjoy a recipe from, then this can simplify this task for the user and in turn, make them favor our service more for finding recipes in the future.

## Business Understanding and Data Understanding

- Explain the project context, using at least one citation to demonstrate your domain understanding
- Consider including visualizations here as well

- There are plenty of recommendation systems for recipes already out there, but I wanted to include the added features of different dietary restrictions, because that is something that is relevant to me. 

## Data Preparation
Feature engineering for diet-type
## Modeling and Evaluation
-What kind of model(s) did you use?
-How well did your final model perform, compared to the baseline?

I used TensorFlow Recommenders to create a neural network recommendation system. 


I chose to create a neural network, as you can add in additional embedding layers for other features of the data. For this, I used TensorFlow Recommenders (TFRS) (Link). TFRS makes it easy to create a recommendation system as a neural network...


## Conclusion
-How would you recommend that your model be used?


### Limitations:

### Next Steps:
- experiment with different depths for the neural network model (https://www.tensorflow.org/recommenders/examples/deep_recommenders)
- look at user reviews (and other text features of the recipes). I didn't do this in this project, because the goal was not sentiment analysis.
- cross network



###### Sources:
- youtube playlist: https://www.youtube.com/playlist?list=PLQY2H8rRoyvy2MiyUBz5RWZr5MPFkV3qz
- TF site
- blogpost(s):https://blog.searce.com/recommendation-systems-using-tensorflow-recommenders-d7d12167b0b7
https://medium.com/@jaayush12/streamlining-recommendation-systems-with-tensorflow-recommenders-tfrs-f77801d3f059