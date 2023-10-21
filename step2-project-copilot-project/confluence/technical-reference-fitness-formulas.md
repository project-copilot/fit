# Technical Reference: Technical Reference: Fitness Formulas
## Title: Technical Reference: Technical Reference: Fitness Formulas
### Initial content:



### Actions in Project Copilot:
- Write custom instruction:
```xml
<instruction>...</instruction>
```
### Final content:

#### Calorie and Health Status Calculations
##### Calculating Calories Burned
The total calories burned in a day is made up of several components:
* Basal Metabolic Rate (BMR)
* Non-Exercise Activity Thermogenesis (NEAT)
* Thermic Effect of Food (TEF)
* Adaptive Thermogenesis
* Exercise Activity

**Average Values**:

```javascript
const averageBMR = 1800  
const averageNEAT = 450
const averageTEF = 200
const adaptiveThermogenesis = 100
```
**Total Calories Burned = BMR + NEAT + TEF + AdaptiveThermogenesis + (Steps x 0.04)**

Where:
* BMR: Basal calories to sustain vital functions
* NEAT: Calories burned through daily activities
* TEF: Calories burned digesting food
* Adaptive Thermogenesis: Calories burned adapting to exercise
* Steps: Number of steps walked
* 0.04: Avg calories per step
This provides a more comprehensive estimate of total daily calorie expenditure. The BMR can be calculated specifically for the user based on their attributes.

##### Estimating Health Status
The health status formula is based on:
* Average adult requires 2000-2500 calories to maintain weight
* WHO/AHA guidelines recommend 150 heart points per week (~21 per day)

```javascript
Health Score = (CaloriesBurned / 2250) + (HeartPoints / 21)

If Health Score < 1:
   Health Status = "Needs Improvement" 
Else If Health Score >= 1 and <= 2:
  Health Status = "Normal"
Else If Health Score > 2:
  Health Status = "Excellent"
```
Where:
* CaloriesBurned = User's actual calories burned
* 2250 = Midpoint of average calorie range
* HeartPoints = User's actual heart points
* 21 = Average recommended daily heart points

Using the midpoint of 2000-2500 calories as the norm provides a more realistic baseline. And basing heart points on the WHO/AHA guidelines ensures alignment with health authority recommendations.

With these updated averages as the denominators, the formula now generates a health assessment aligned with evidence-based calorie and exercise guidelines for a healthy adult.