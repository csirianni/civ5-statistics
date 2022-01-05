# Civ 5 Statistics

Cedric Sirianni

## Background

In the video game Sid Meier’s Civilization 5, each player represents a leader of a civilization and must guide its growth over the course of thousands of years. The game ends when one player achieves one of the victory conditions (conquer the world, be elected world leader, send a rocket ship to space, etc.). At the beginning of the game, players must select the settlement location of their capital. Settlement locations have different attributes e.g. the presence of a mountain, river, ocean, etc.

## About
In this data analysis, I investigate *if starting conditions influence the player’s chance of winning*. My hypothesis is that certain characteristics (presence of a mountain, river, or ocean) have dramatic effects.

To view the accompanying presentation for this project, click [here](https://docs.google.com/presentation/d/1FT_cNBsll4tAzSqiaOMsJ6y-Qid2bP_ji7U1uy0_pWY/edit?usp=sharing).

### Data Collection

I collected data from FilthyRobot's Civilization 5 videos on YouTube. This [playlist](https://www.youtube.com/watch?v=joO1AF1aFWQ&list=PLQFX9B_9L4-mCLbc4tUl5EejZDqsGJjsz) includes a sample. In total, there are close to 400 games. In my data collection process, I tracked a number of variables:

- Score: Quantitative (Discrete)
- Number of turns: Quantitative (Discrete)
- Win/Lose: Categorical (Nominal)
- Capital adjacent to a mountain? (yes/no): Categorical (Nominal)
- Capital on a river? (yes/no): Categorical (Nominal)
- Capital on the ocean? (yes/no): Categorical (Nominal)

Collecting data from the entire population was too time intensive (~20 hours). Instead, I only sampled (n = 72) the games in which FilthyRobot played Arabia, Aztec, China, Greece, Huns, Maya, Russia, Shoshone, or Spain. These civilizations are similar in caliber but diverse in their start biases and win strategies, reducing multicollinearity (though certainly not eliminating it).

### Data Analysis

To analyze the data, I used a **logistic regression** between each starting condition and the outcome of the game (win/lose):

| Start Condition | P-value |
|:---------------:|:-------:|
|    Mountain     |  .206   |
|      River      |   .16   |
|      Ocean      |  .683   | 
|      Hill       |  .034   |

Hill is the only statistically significant start condition ( p < .05). It appears that settling the capital on a hill increases the chances of winning. 

The logistic regression also includes an *odds ratio* which can be used to determine by how much the odds of winning increase. When settling on a hill, the odds of winning increase by **2x**.

### Conclusion

It appears that skill plays a larger role than luck in a player winning. All starting conditions except for hill had little to no impact on win rate.

### Sources of Error

Here are some potential sources of error in this analysis:

- Selection bias: I did not prove that my sample was representative of the population. Ideally, I would sample the entire population of 400 games. Furthermore, these findings do not necessarily generalize to every Civilization 5 player, since every data point is from FilthyRobot. However, using data from multiple players also introduces significant problems.
- Insufficient sample size: Logistic regressions typically require n to be significantly larger than 72.
- Multicollinearity: There are a number of other factors that could influence the chances of winning besides the attributes I measured.
