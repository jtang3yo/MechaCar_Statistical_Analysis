# MechaCar_Statistical_Analysis - AutoRUs

## Overview of Project 

AutosRUs’ newest prototype, the MechaCar, is suffering from production troubles that are blocking the manufacturing team’s progress. AutosRUs’ upper management has called on Jeremy and the data analytics team to review the production data for insights that may help the manufacturing team.

In this challenge, you’ll help Jeremy and the data analytics team do the following:

  * Perform multiple linear regression analysis to identify which variables in the dataset predict the mpg of MechaCar prototypes
  * Collect summary statistics on the pounds per square inch (PSI) of the suspension coils from the manufacturing lots
  * Run t-tests to determine if the manufacturing lots are statistically different from the mean population
  * Design a statistical study to compare vehicle performance of the MechaCar vehicles against vehicles from other manufacturers. For each statistical analysis, you’ll write a summary interpretation of the findings.

## Deliverables: 

  *Deliverable 1: Linear Regression to Predict MPG
  *Deliverable 2: Summary Statistics on Suspension Coils
  *Deliverable 3: T-Test on Suspension Coils
  *Deliverable 4: Design a Study Comparing the MechaCar to the Competition

## Data Resource, Tools and Software 
  * Data Source: MechaCar_mpg.csv and Suspension_Coil.csv
  * Data Tools: tidyverse, dplyr, ggplot2 and MechaCarChallenge.RScript. 
  * Software: RStudio and R 

### Deliverable 1: Linear Regression to Predict MPG
  * Use the library() function to load the dplyr package.
  * Import and read in the MechaCar_mpg.csv file as a dataframe.
  * Perform linear regression using the lm() function. In the lm() function, pass in all six variables (i.e., columns), and add the dataframe you created in       Step 4 as the data parameter.
  * Using the summary() function, determine the p-value and the r-squared value for the linear regression model.
  * Resulting Model: 
    **mpg = (6.267)vehicle_length + (0.0012)vehicle_weight + (0.0688)spoiler_angle + (3.546)ground_clearance + (-3.411)AWD + (-104.0)**
    **Linear Regression**: <img width="767" alt="Screen Shot 2021-07-30 at 4 26 36 PM" src="https://user-images.githubusercontent.com/82353749/127708619-e203b147-c8fc-4467-ad21-3143a631dae7.png">
    **Statistical Summary**: 
    1. The vehicle length, and vehicle ground clearance are statistically likely to provide non-random amounts of variance to the model. That is to say, the          vehicle length and vehicle ground clearance have a significant impact on miles per gallon on the MechaCar prototype. Conversely, the vehicle weight,            spoiler angle, and All Wheel Drive (AWD) have p-Values that indicate a random amount of variance with the dataset.
    2. The p-Value for this model, p-Value: 5.35e-11, is much smaller than the assumed significance level of 0.05%. This indicates there is sufficient evidence        to reject our null hypothesis, which further indcates that the slope of this linear model is not zero.
    3. This linear model has an r-squared value of 0.7149, which means that approximately 71% of all mpg predictions will be determined by this model.                Relatively speaking, his multiple regression model **does predict mpg of MechaCar prototypes effectively**.
    4. If we remove the less impactful independent variables (vehicle weight, spoiler angle, and All Wheel Drive), the predictability does decrease, but not          drastically: the r-squared value falls from 0.7149 to 0.674. <img width="642" alt="Screen Shot 2021-07-30 at 4 28 46 PM" src="https://user-images.githubusercontent.com/82353749/127708836-4d0b1ceb-1326-4ae5-96e8-66ddbc06f1b8.png">
    
### Deliverable 2: Summary Statistics on Suspension Coils

  * Using the summarize() function to get the mean, median, variance, and standard deviation of the suspension coil’s PSI column.
  <img width="465" alt="Screen Shot 2021-07-30 at 4 36 53 PM" src="https://user-images.githubusercontent.com/82353749/127709158-e3463e84-1c80-40bc-9908-75744e7faac6.png">
  
  * creates a lot_summary dataframe using the group_by() and the summarize() functions to group each manufacturing lot by the mean, median, variance, and standard deviation of the suspension coil’s PSI column.
  <img width="617" alt="Screen Shot 2021-07-30 at 4 38 23 PM" src="https://user-images.githubusercontent.com/82353749/127709265-27b0494a-d6ac-43f0-b5df-6204397975a7.png">
  
  * **Statistical Summary**: 
  1. The Suspension Coil dataset provided for the MechaCar contains the results of testing the weight capacities of multiple suspension coils from multiple          production lots to determine consistency.
  2. With the understanding that the design specifications for the MechaCar suspension coils mandate that **the variance of the suspension coils cannot exceed        100 pounds per square inch (PSI)** .
  3. When looking at the entire population of the production lot, the variance of the coils is 62.29 PSI, which is well within the 100 PSI variance                  requirement.

Similarly, but significantly more consistent, Lot 1 and Lot 2 are well within the 100 PSI variance requirement; with variances of 0.98 and 7.47            respectively. However, it is Lot 3 that is showing much larger variance in performance and consistency, with a variance of 170.29. It is Lot 3 that is disproportionately causing the variance at the full lot level.
![Rplot](https://user-images.githubusercontent.com/82353749/127709775-f537d03c-4ae6-4c61-acca-7417817075d0.png)

### Deliverable 3: t-Tests on Suspension Coils
  * Using the t.test() function to determine if the PSI across all manufacturing lots is statistically different from the population mean of 1,500 pounds per square inch.
  * Using the t.test() function and its subset() argument to determine if the PSI for each manufacturing lot is statistically different from the population mean of 1,500 pounds per square inch.
 
  * **Statistical Summary of all manufacturing lots**: 
    <img width="414" alt="Screen Shot 2021-07-30 at 5 14 46 PM" src="https://user-images.githubusercontent.com/82353749/127712192-3bda69de-8188-4175-abce-b2e70ab88315.png">
    From here we can see the true mean of the sample is 1498.78, which we also saw in the summary statistics above. With a p-Value of 0.06, which is higher than the common significance level of 0.05, there is NOT enough evidence to support rejecting the null hypothesis. That is to say, the mean of all three of these manufacturing lots is statistically similar to the presumed population mean of 1500.
   
  * **Statistical Summary of each individual lot **
    1. Lot 1 sample actually has the true sample mean of 1500, again as we saw in the summary statistics above. With a p-Value of 1, clearly we cannot reject          (i.e. accept) the null hypothesis that there is no statistical difference between the observed sample mean and the presumed population mean (1500).
     <img width="440" alt="Screen Shot 2021-07-30 at 5 20 17 PM" src="https://user-images.githubusercontent.com/82353749/127712651-c89924e5-d617-4cc5-b100-0e71012c849b.png">

    2. Lot 2 has essentially the same outcome with a sample mean of 1500.02, a p-Value of 0.61; the null hypothesis cannot be rejected, and the sample mean and        the population mean of 1500 are statistically similar.
     <img width="416" alt="Screen Shot 2021-07-30 at 5 21 33 PM" src="https://user-images.githubusercontent.com/82353749/127712725-1cfa172f-9572-4fbe-9d34-2c168fae2960.png">

    3. However, Lot 3, not surprisingly is a different scenario. Here the sample mean is 1496.14 and the p-Value is 0.04, which is lower than the common      significance level of 0.05. All indicating to reject the null hypothesis that this sample mean and the presumed population mean are not statistically different.
     <img width="405" alt="Screen Shot 2021-07-30 at 5 22 29 PM" src="https://user-images.githubusercontent.com/82353749/127712787-de10404d-099f-49a0-83cb-aa46fdea033a.png">
     Clearly, something went awry in Lot 3's production cycle. The process needs to be checked for system fails and the suspension coils from this lot need to be inspected to remove those not meeting quality criteria.
     
### Deliverable 4: Study Design: MechaCar vs Competition.
Write a short description of a statistical study that can quantify how the MechaCar performs against the competition. In your study design, think critically about what metrics would be of interest to a consumer: for a few examples, cost, city or highway fuel efficiency, horse power, maintenance cost, or safety rating
  * What metric or metrics are you going to test?
  **Metrics**
    1. Current Price (Selling): **Dependent Variable**
    2. Drive Package: **Independent Variable**
    3. Safety Feature Rating: **Independent Variable**
    4. Engine (Electric, Hybrid, Gasoline / Conventional): **Independent Variable**
    5. Average Annual Cost of ownership (Maintenance): **Independent Variable**
    6. Resale Value: **Independent Variable**
    7. MPG (Gasoline Efficiency): **Independent Variable**
    
  * What is the null hypothesis or alternative hypothesis?
    * Null Hypothesis (H0): MechaCar is NOT priced correctly based on performance of key factors/metrics for its genre after determining which factors/metrics are critical to MechaCar's genre. 
    * Alternative Hypothesis (Ha): MechaCar is priced correctly based on its performance of key factors/metrics for its genre.
  
  * What statistical test would you use to test the hypothesis? And why?
  **Statistical Tests**
    **Multiple linear regression** will be used to determine the factors that have the highest correlation/predictability with the list selling price (dependent variable); which combination has the greatest impact on price or it may be related to all of the factors. 
  
  * What data is needed to run the statistical test?
    **Data Source**: Data that contains the above mentioned metrics will be used to run statistical tests. 



    


 
