## Guide to our data creation process

1. Heart Rate & Blood Pressure:
    - For every 10 bpm increase in resting heart rate, systolic BP might increase by 3-5 mmHg
    - Correlation coefficient: around 0.3 to 0.5
2. Body Fat Percent & BMI:
    - Correlation coefficient: approximately 0.7 to 0.8
    - For every 1 point increase in BMI, body fat % might increase by 1.1-1.5% in men and 1.2-1.6% in women
3. Active Energy & Steps:
    - Correlation coefficient: around 0.8 to 0.9
    - Roughly 100 calories burned per 2000-2500 steps (varies by individual)
4. Sleep Habits & Sleep Quality:
    - Correlation coefficient: approximately 0.5 to 0.7
    - Each additional hour of sleep (up to the recommended amount) might improve sleep quality score by 5-10%
5. Cardio Fitness & Resting Heart Rate:
    - Correlation coefficient: around -0.6 to -0.7 (negative correlation)
    - For every 1 MET increase in cardio fitness, resting heart rate might decrease by 1-2 bpm
6. Heart Rate Variability & Stress Level:
    - Correlation coefficient: approximately -0.4 to -0.6 (negative correlation)
    - A 10% decrease in HRV might correspond to a 5-15% increase in stress level
7. Respiratory Rate & Heart Rate:
    - Correlation coefficient: around 0.3 to 0.5
    - For every 2-3 breaths per minute increase, heart rate might increase by 5-10 bpm
8. Screen Time & Time Outside:
    - Correlation coefficient: approximately -0.3 to -0.5 (negative correlation)
    - For every hour increase in screen time, time outside might decrease by 15-30 minutes
9. Electrodermal Activity & Stress Level:
    - Correlation coefficient: around 0.4 to 0.6
    - A 20-30% increase in EDA might correspond to a 10-20% increase in stress level
10. Steps & Time Outside:
    - Correlation coefficient: approximately 0.5 to 0.7
    - Every 30 minutes spent outside might correlate with an additional 1000-1500 steps
11. BMI & Cardio Fitness:
    - Correlation coefficient: around -0.3 to -0.5 (negative correlation)
    - For every 1 point increase in BMI, cardio fitness (in METs) might decrease by 0.1-0.2
12. Stress Level & Heart Rate:
    - Correlation coefficient: approximately 0.3 to 0.5
    - A 10% increase in stress level might correspond to a 3-7 bpm increase in heart rate
13. Sleep Quality & Active Energy:
    - Correlation coefficient: around 0.2 to 0.4
    - A 10% improvement in sleep quality might lead to a 5-8% increase in active energy the next day
14. Body Temperature & Activity Level:
    - Correlation coefficient: approximately 0.2 to 0.3
    - During exercise, body temperature might increase by 0.1-0.2°C for every 10% increase in activity level
15. Cardio Fitness & Active Energy:
    - Correlation coefficient: around 0.5 to 0.7
    - For every 1 MET increase in cardio fitness, daily active energy expenditure might increase by 50-100 calories

---

Here's an updated set of Mockaroo formulas that avoid circular logic:

1. Heart Rate (based on Activity Trend, assuming Activity Trend is on a 1-10 scale):
2. health heart rate limit:  **multiplying the age by 0.7 and subtracting the total from 208**. 

```python

HeartRate = 60 + (field("Activity Trend") * 5) + random(-10, 10)

```

1. Blood Pressure Systolic (based on Heart Rate):
2. According to the American Heart Association, a healthy blood pressure reading is **less than 120 millimeters of mercury (mmHg) systolic and less than 80 mmHg diastolic**:

```python

100 + (heart_rate - 60) * 0.5 + random(-5, 5)
100 + (field("Heart Rate(bpm)") - 60) * 0.5 + random(-5, 5)

```

1. Blood Pressure Diastolic (based on Systolic):
2. According to the American Heart Association, a healthy blood pressure reading is **less than 120 millimeters of mercury (mmHg) systolic and less than 80 mmHg diastolic**:

```python

field("Blood Pressure Systolic(mmHg)") * 0.6 + random(-5, 5)

```

1. Body Fat Percent (based on BMI):

```rust
(field("Body Mass Index") - 18.5) * 1.3 + random(-2, 2)

```

1. Body Mass Index (generate this independently, then use it for other calculations):

```

random(18.5, 35)

```

1. Body Temperature (based on Activity Trend):

```

36.5 + (activity_trend * 0.05) + random(-0.2, 0.2)

```

1. Electrodermal Activity (based on Activity Trend and Time Outside):

```rust

(field("Activity Trend") * 0.5) + (field("Time Outside(min)") / 60) + random(-2, 2)

```

1. Active Energy (based on Steps):

```python

ActiveEnergyBurned = field("Steps") * 0.05 + random(-50, 50)

```

1. Activity Trend (generate independently):

```

random(1, 10)

```

1. Screen Time (inversely related to Time Outside):

```rust

720 - field("Time Outside(min)") + random(-60, 60)

```

1. Hearing Level (assuming lower is better, generate independently):

```

random(0, 40)

```

1. Heart Rate Variability (based on Cardio Fitness):

```rust

40 + (field("Cardio Fitness(V02 max)") * 2) + random(-10, 10)

```

1. Respiratory Rate (related to Heart Rate):

```rust

12 + (field("Heart Rate(bpm)") - 60) * 0.1 + random(-2, 2)

```

1. Time Outside (generate independently):

```

random(30, 480)

```

1. Sleep Habits (generate independently, on a 1-10 scale):

```

random(1, 10)

```

1. Sleep Quality (based on Sleep Habits):

```
sleep_habits * 0.7 + random(-1, 1)

```

1. Steps (based on Activity Trend):

```

activity_trend * 1000 + random(-500, 500)

```

1. Cardio Fitness (inversely related to BMI):

```rust
50 - (field("Body Mass Index") - 18.5) * 0.5 + random(-2, 2)

```

For the Level of Distress, which is what we are trying to predict, we could generate it independently or create a complex formula based on multiple factors. However, it's often better to generate this independently and then use our model to try to predict it based on the other variables.

```rust
round(
  (
    (heart_rate - 60) / 40 * 2 +
    (blood_pressure_systolic - 120) / 40 * 1.5 +
    (blood_pressure_diastolic - 80) / 30 * 1.5 +
    (bmi - 25) / 10 * 1 +
    (body_temperature - 36.5) / 1 * 2 +
    electrodermal_activity / 10 * 1.5 +
    (3000 - active_energy) / 1000 * 1 +
    (10 - activity_trend) * 0.5 +
    screen_time / 120 * 1 +
    (40 - heart_rate_variability) / 20 * 2 +
    (respiratory_rate - 12) / 6 * 1.5 +
    (480 - time_outside) / 120 * 1 +
    (10 - sleep_quality) * 0.8 +
    (10000 - steps) / 3000 * 1 +
    (50 - cardio_fitness) / 20 * 1.5
  ) / 10 + 5
, 1)
```

```rust
round(
  (
    (field("Heart Rate(bpm)") - 60) / 40 * 2 +
    (field("Blood Pressure Systolic(mmHg)") - 120) / 40 * 1.5 +
    (field("Blood Pressure Diastolic(mmHg)") - 80) / 30 * 1.5 +
    (field("Body Mass Index")  - 25) / 10 * 1 +
    field("Electrodermal Activity(microsiemens)") / 10 * 1.5 +
    (3000 - field("Active Energy(cal)")) / 1000 * 1 +
    (10 - field("Activity Trend") * 0.5 +
    field("Screen Time(min)") / 120 * 1 +
    (40 - field("Heart Rate Variability(ms)")) / 20 * 2 +
    (field("Respiratory Rate(bpm)") - 12) / 6 * 1.5 +
    (480 - field("Time Outside(min)")) / 120 * 1 +
    (10 - field("Sleep Quality(hours)")) * 0.8 +
    (10000 - field("Steps")) / 3000 * 1 +
    (50 - field("Cardio Fitness(V02 max)")) / 20 * 1.5
  ) / 10 + 5
, 1)
```

```rust
round(((field('Heart Rate(bpm)') - 60) / 40 * 2 
+ (field('Blood Pressure Systolic(mmHg)') - 120) / 40 * 1.5 
+ (field('Blood Pressure Diastolic(mmHg)') - 80) / 30 * 1.5 
+ (field('Body Mass Index') - 25) / 10 * 1 
+ field('Electrodermal Activity(microsiemens)') / 10 * 1.5 
+ (3000 - field('Active Energy(cal)')) / 1000 * 1 
+ (10 - field('Activity Trend')) * 0.5 
+ field('Screen Time(min)') / 120 * 1 
+ (40 - field('Heart Rate Variability(ms)')) / 20 * 2 
+ (field('Respiratory Rate(bpm)') - 12) / 6 * 1.5 
+ (480 - field('Time Outside(min)')) / 120 * 1 
+ (10 - field('Sleep Quality(hours)')) * 0.8 
+ (10000 - field('Steps')) / 3000 * 1 
+ (50 - field('Cardio Fitness(V02 max)')) / 20 * 1.5) / 10 + 5, 1)\

#Calculate the initial score
initial_score = ((field('Heart Rate(bpm)') - 60) / 40 * 2 
+ (field('Blood Pressure Systolic(mmHg)') - 120) / 40 * 1.5 
+ (field('Blood Pressure Diastolic(mmHg)') - 80) / 30 * 1.5 
+ (field('Body Mass Index') - 25) / 10 * 1 
+ field('Electrodermal Activity(microsiemens)') / 10 * 1.5 
+ (3000 - field('Active Energy(cal)')) / 1000 * 1 
+ (10 - field('Activity Trend')) * 0.5 
+ field('Screen Time(min)') / 120 * 1 
+ (40 - field('Heart Rate Variability(ms)')) / 20 * 2 
+ (field('Respiratory Rate(bpm)') - 12) / 6 * 1.5 
+ (480 - field('Time Outside(min)')) / 120 * 1 
+ (10 - field('Sleep Quality(hours)')) * 0.8 
+ (10000 - field('Steps')) / 3000 * 1 
+ (50 - field('Cardio Fitness(V02 max)')) / 20 * 1.5) / 10 + 5

#Apply the threshold
if initial_score > 5 then 1 else 0 end

```

```rust
#for zero and 1 

if (((field('Heart Rate(bpm)') - 60) / 40 * 2 
+ (field('Blood Pressure Systolic(mmHg)') - 120) / 40 * 1.5 
+ (field('Blood Pressure Diastolic(mmHg)') - 80) / 30 * 1.5 
+ (field('Body Mass Index') - 25) / 10 * 1 
+ field('Electrodermal Activity(microsiemens)') / 10 * 1.5 
+ (3000 - field('Active Energy(cal)')) / 1000 * 1 
+ (10 - field('Activity Trend')) * 0.5 
+ field('Screen Time(min)') / 120 * 1 
+ (40 - field('Heart Rate Variability(ms)')) / 20 * 2 
+ (field('Respiratory Rate(bpm)') - 12) / 6 * 1.5 
+ (480 - field('Time Outside(min)')) / 120 * 1 
+ (10 - field('Sleep Quality(hours)')) * 0.8 
+ (10000 - field('Steps')) / 3000 * 1 
+ (50 - field('Cardio Fitness(V02 max)')) / 20 * 1.5) / 10 + 5) > 5 then 1 else 0 end

```

- Ranges and Values types
    - Timestamp:
        - Use Mockaroo's built-in date/time generator
        - Range: Current date minus 1 year to current date
    - Heart Rate: field(”Heart Rate(bpm)”)
        - Range: 60 to 110 bpm
        - Formula: random(60, 110)
    - Blood Pressure Systolic: field(”Blood Pressure Systolic(mmHg)”)
        - Range: 110 to 180 mmHg
        - Formula: random(110, 160)
    - Blood Pressure Diastolic:  field(”Blood Pressure Diastolic(mmHg)”)
        - Range: 60 to 100 mmHg
        - Formula: random(70, 100)
    - Body Fat Percent:
        - Range: 15 to 40%
        - Formula: random(15, 40)
    - Body Mass Index:
        - Range: 18 to 35
        - Formula: random(18, 35)
    - Body Temperature:
        - Range: 36.1 to 37.5°C (97 to 99.5°F)
        - Formula: round(random(36.1, 37.5), 1)
    - Electrodermal Activity: Electrodermal Activity(microsiemens)
        - Range: 0.1 to 30 microsiemens
        - Formula: round(random(0.1, 30), 1)
    - Active Energy: field(”Active Energy(cal)”)
        - Range: 500 to 3000 calories
        - Formula: round(random(500, 2500))
    - Activity Trend: field(”Activity Trend”)
        - Range: 1 to 8 (on a scale of 1-10)
        - Formula: round(random(1, 8))
    - Screen Time: Screen Time(min)
        - Range: 60 to 600 minutes (1 to 10 hours)
        - Formula: round(random(60, 600))
    - Hearing Level: Hearing Level(dB)
        - Range: 0 to 130 dB (higher numbers indicate more hearing loss)
        - Formula: round(random(10, 60))
    - Heart Rate Variability: field(”Heart Rate Variability(ms)”)
        - Range: 20 to 200ms
        - Formula: round(random(10, 50))
    - Respiratory Rate: field(”Respiratory Rate(bpm)”)
        - Range: 12 to 25 breaths per minute
        - Formula: round(random(12, 25))
    - Inertial:
        - Range: 1 to 10 (arbitrary scale, higher numbers indicate more movement)
        - Formula: round(random(1, 10))
        - A very wide variety of IMUs exists, depending on application types, with performance ranging: **From 0.1°/s to 0.001°/h for gyroscope**. **From 100 mg to 10 μg for accelerometers**.
    - Time Outside: field(”Time Outside(min)”)
        - Range: 0 to 300 minutes (0 to 5 hours)
        - Formula: round(random(0, 240))
    - Sleep Habits:
        - Range: 1 to 10 (higher numbers indicate better habits)
        - Formula: round(random(1, 10))
    - Sleep Quality: Sleep Quality
        - Range: 1 to 10 (higher numbers indicate better quality)
        - Formula: round(random(1, 10))
    - Steps: Steps
        - Range: 1000 to 8000 steps
        - Formula: round(random(1000, 8000))
    - Cardio Fitness: field(”Cardio Fitness (V02 max)”)
        - Range: 20 to 45 (VO2 max estimate)
        - Formula: round(random(20, 45))
    - Level of Distress:
        - Range: 1 to 10 (calculated based on other metrics)
        - Use the complex formula provided earlier, which takes into account all other variables

- Timestamp:
- Heart Rate(bpm)
- Blood Pressure Systolic(mmHg)
- Blood Pressure Diastolic(mmHg)
- Body Fat Percent
- Body Mass Index
- Electrodermal Activity(microsiemens)
- Active Energy(cal)
- Activity Trend
- Screen Time(min)
- Hearing Level(dB)
- Heart Rate Variability(ms)
- Respiratory Rate(bpm)
- Inertial
- Time Outside(min)
- Sleep Quality(hours)
- Steps
- Cardio Fitness(V02 max)
- Distress Level
