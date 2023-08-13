# A/B Testing - Cookie Cats

![cokkie cats](https://github.com/EDJR94/ab_test/assets/128603807/d0b2d223-d13d-4c13-882d-2865c62283d4)

## Business Problem

Cookie Cats is a hugely popular mobile puzzle game developed by Tactile Entertainment. It's a classic "connect three" style puzzle game where the player must connect tiles of the same color in order to clear the board and win the level. It also features singing cats. We're not kidding!

As players progress through the game they will encounter gates that force them to wait some time before they can progress or make an in-app purchase. In this project, we will analyze the result of an A/B test where the first gate in Cookie Cats was moved from level 30 to level 40. In particular, we will analyze the impact on player retention.

## Data

| Column Name | Description |
| --- | --- |
| userid | A unique number that identifies each player. |
| version | Whether the player was put in the control group (gate_30 - a gate at level 30) or the test group (gate_40 - a gate at level 40). |
| sum_gamerounds | The number of game rounds played by the player during the first week after installation. |
| retention_1 | Did the player come back and play 1 day after installing? |
| retention_7 | Did the player come back and play 7 days after installing? |

## Solution Strategy

The strategy used was the CRISP method, a scientific method based on cycles:

![crisp](https://github.com/EDJR94/ab_test/assets/128603807/0cc84409-1daa-45c0-85e2-c78c1ed18674)

The project cycles were divided into the following parts:

- Understanding business problem & data
- Detect and resolve problems in the data (Missing Value, Outliers, Unexpected Value)
- Look summary stats and plots
- Experiment Design
- Apply Hipothesis Test
- Test Conclusion
- Business Performance

## Results

This were my Experiment Parameters:

- Gate 30 = Control Group
- Gate 40 = Treatment Group
- H0: Moving the gate does not make a difference in retention
- H1: Moving the gate makes a difference in retention
- Significance Level: 0.05

Because I’m working with categorical variables, I decide to apply Chi-Squared Test aiming for 5% of Confidence Level. First I applied the level 30 and level 40 gates for 1 Day Player Retention and then the same test for 7 Days Player Retention.

P-Value 1 Day Retention: `0.075`

P-Value 7 Days Retention:`0.00164`

## Conclusion

The P-Value was lower than my confidence level in my 7 Days Retention, based on this, we can confirm that **there is statistical evidence to reject the null hypothesis.** This suggests that a **significant association exists** between the game version and player retention after 7 days.

## Business Performance

Based on the Retention Rate of players using each Gate Level and projecting that rate for Retained Players(You can see more details of the calculations in the notebook), moving the gate to level 40 will **actually decreases** the potential revenue by \$17,238.80 assuming a LTV(Life-Time Value) of each player equal to \$100.

**Conclusion: It is better for the company to keep the gate at level 30 rather than at level 40.**
