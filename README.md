## Recipe Recommendation System with Dietary Restriction Embeddings
It can be hard to continuously come up with new and interesting recipes to cook, especially if you have certain dietary restrictions. Many people use websites such as food.com to find, try, and rate recipes. From user and recipe data from Food.com, can we provide users with recommendations for the next recipes that users should try, taking into account their dietary specifications?
Taking into account user preferences, shown by recipes they have rated highly in the past, as well as their certain dietary restriction categories of recipes, we create a model that is able to provide the top 3 recommendations for next recipes to try that the user is most likely to rate highly.

<img src= "images/recipes.jpg" alt = "Recipe Image">

## Business Understanding and Data Understanding
<!--(data, target, rationale), Using data, can we predict target? This would be useful because rationale.-->

The proposed recipe recommendation system would be useful, because it can be time consuming and repetitive for people to come up with new recipes to make all the time, especially when their options are narrowed down due to dietary restrictions. If a recommender system took into account not only a user's preferences, based on past recipes that the user has rated highly, but also the type of diet category that the user is most likely to enjoy a recipe from, then this can simplify this task for the user and in turn, make them favor our service more for finding recipes in the future.


<!--  Explain the project context, using at least one citation to demonstrate your domain understanding
- Consider including visualizations here as well

- There are plenty of recommendation systems for recipes already out there, but I wanted to include the added features of different dietary restrictions, because that is something that is relevant to me. -->

## Data Preparation
(Feature engineering for diet-type)
In the miscellaneous notebook associated with this project, the different features of the recipe data were compared to see which ones would contain the most information about each of the three diet types that will be taken into account (vegetarian, vegan, and gluten-free). It was determined that the 'tags' feature contained the most information about diets that were gluten-free, while a different approach, ingredient filtering, would be necessary for recipes of the vegan and vegetarian diet-types.

A text cleaning function removed punctuation, numbers, and symbols from the relevant text data columns, and made all letters lowercase. Using food category information sourced from the <a href="https://www.ars.usda.gov/ARSUserFiles/80400530/pdf/1720/Food_Category_List_2017-March%202020.pdf">USDA</a>, I compiled an extensive list of the ingredient words that would be used in recipes containing meat, seafood, and other animal products. Recipe's that did not contain any of the animal product ingredients were labeled vegan, and recipes that did not contain specifically meat or seafood were labeled vegetarian. Recipes can be all or none of these diet types. A new column was created that combined the designations for each of these diet types for each recipe to be used as a single embedding in the nerual network model.

## Modeling and Evaluation
<!--What kind of model(s) did you use?
-How well did your final model perform, compared to the baseline?-->

This is essentially a regression task, achieved by Collaborative Filtering. We are trying to predict a user's rating of recipes they have not yet tried, and we are doing so by comparing the user to other similar users and the recipes that they've rated highly (user-user similarity).
<!--<a href= "https://blog.searce.com/recommendation-systems-using-tensorflow-recommenders-d7d12167b0b7">
    
</a>
<img src="images/multitask_model.png" alt = "Multi-Task Model">-->

Using  <a href="https://www.tensorflow.org/recommenders/examples/multitask">TensorFlow Recommenders </a>, I created an initial (baseline) multi-task neural network model that contained only the embeddings for the user IDs and recipe IDs and made recommendations only based on previous rating data from users, and that completed both retrieval and ranking tasks for recommendations. 
 
 (vis. to show that joint model did best overall) 
 
As it was shown in the TensorFlow Recommenders guide, the weights of both the retrieval and ranking tasks are able to be assigned when compiling the model. This way, we are able to see how each task performs separately as well as together.

This model had a Top-100 Retrieval Accuracy of about __ and an RMSE of about __.

In the next model, I added in an embedding for the diet-type feature that I created.

While I experimented with adding various additional feature embeddings to the model along with the diet-type embedding, none of those models performed as well as the model with only the diet-type embedding added.

I then used ScaNN (Scalable Nearest Neighbors), with tuned hyperparameters, in an attempt to optimize the speed and performance of the retrieval task. This produced my final model with a top-100 Retrieval accuracy of __ and an RMSE of __.
 
 (vis. to show that scann model did best overall) 


<!--"In our training data we have positive (user, movie) pairs. To figure out how good our model is, we need to compare the affinity score that the model calculates for this pair to the scores of all the other possible candidates: if the score for the positive pair is higher than for all other candidates, our model is highly accurate.

To do this, we can use the tfrs.metrics.FactorizedTopK metric. The metric has one required argument: the dataset of candidates that are used as implicit negatives for evaluation."-->
## Conclusion
<!--How would you recommend that your model be used?-->


### Limitations:
- Model takes a long time to run and is computationally expensive
- Diet type classifications of recipes are not 100% reliable


### Next Steps:
Next Steps:
- Deploy model
- Update model with new data
- Add more diet types 
- Try to improve model metrics:
    - experiment with different depths
    - try using a feature cross
    - further tune model parameters



###### Sources:
- youtube playlist: https://www.youtube.com/playlist?list=PLQY2H8rRoyvy2MiyUBz5RWZr5MPFkV3qz
- TF site
- blogpost(s):https://blog.searce.com/recommendation-systems-using-tensorflow-recommenders-d7d12167b0b7
https://medium.com/@jaayush12/streamlining-recommendation-systems-with-tensorflow-recommenders-tfrs-f77801d3f059