---
layout:     post
title:      Using Software To Predict The Healthiness Of Food Items
date:       2018-07-19
summary:    Predicting the healthiness of food items using a range of macro-nutrional and personal inputs.
---
*NEEDS SPELL CHECKING*

## Background
For my final year university dissertation project, I investigated the feasiblity of predicting the healthiness of food items for a given individual based on a range of inputs. This involved programming a desktop application with Java and JavaFx and researched thoroughly into acceptable nutrition literature from which the key rules were derived from.

## Implementation
The method of processing the inputs that was decided upon was a heuristic scoring technique, which involved scoring individul components of the input vector and then determining the final classification based on the range of scores given. This 

The following code segment gives an example structure of the scoring methods used in the main decision making step. The decision making was built up from a large set of similar rules.
{% highlight java %}
else if (person.getActivityLevel() == ActivityLevel.HIGH) {
                if (person.getGoal() == Goal.LOSE) {
                    carbsComments.add("Consuming large quantities of carbohydrates whilst at a high level of activity " +
                            "and whilst trying to lose weight could be unproductive.");
                    returnScore += 10;
                } else if (person.getGoal() == Goal.MAINTAIN) {
                    carbsComments.add("Consuming large quantities of carbohydrates whilst at a high level of activity " +
                            "and whilst trying to maintain weight could cause weight gain.");
                    returnScore += 10;
                } else if (person.getGoal() == Goal.GAIN) {
                    carbsComments.add("Consuming large quantities of carbohydrates whilst at a high level of activity " +
                            "and whilst trying to gain weight could cause weight gain.");
                    returnScore += 0;
                }
            }

{% endhighlight %}