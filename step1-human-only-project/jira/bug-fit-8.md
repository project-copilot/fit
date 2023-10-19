# Bug
## ID: FIT-8
## Title: Wrong calories value calculated
## Description:
In the FIT-5 user story, the formula to calculate the calories burned in a day is not specified, and the implementation only calculates calories based on steps, omitting other factors that contribute to the average daily burned calories: 

- Basal Metabolic Rate (BMR): On average, BMR can range from around 1,200 to 2,400 calories per day for adults, depending on factors like age, gender, weight, and muscle mass. The Harris-Benedict equation is commonly used to estimate BMR based on these factors.
- Non-Exercise Activity Thermogenesis (NEAT): NEAT can vary significantly but may account for an additional 100 to 800 calories per day on average.
- Thermic Effect of Food (TEF): TEF typically accounts for about 10% of your daily calorie intake. If you consume 2,000 calories a day, TEF would be approximately 200 calories.
- Adaptive Thermogenesis: This factor is highly variable and can range from negligible to a few hundred calories per day.

We can use the following simplified formula:

Total Daily Calories = (Average BMR) + (Average NEAT) + (Average TEF) + Adaptive Thermogenesis + (Step Count * Calories Burned per Step)

We can use some rough average values:
- Average BMR: 1,800 calories per day (a mid-range estimate for adults)
- Average NEAT: 450 calories per day (a mid-range estimate)
- Average TEF: 200 calories per day (10% of a 2,000-calorie diet, as mentioned earlier)
- Adaptive Thermogenesis: This can vary, so you may or may not include an estimate here. If you want to account for it, you can use a value like 100 calories per day as a rough average.

With these values, the simplified formula becomes:

Total Daily Calories = 1,800 + 450 + 200 + 100 + (Step Count * Calories Burned per Step)