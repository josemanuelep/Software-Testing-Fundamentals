Let’s use a simple program as an example in this section.  Let’s assume that we are building a small program that employees at a company can use to determine how much their insurance will cost.  Here are the requirements for the application.

Requirement #1 An employee must have health insurance to get vision or dental insurance.

Requirement #2 There are two types of health insurance: HMO costs $100 a month; PPO costs $150 a month.

Requirement #3 Vision costs $25 a month

Requirement #4 Dental costs $20 a month

The user interface might look like this. The user selects a health insurance plan and might check boxes to get vision or dental insurance.  Then the user clicks the Calculate button.  The calculated cost appears in the text field beside the label “Total Cost”.

Form with a drop down box labeled "Health Insurance" that has two items displayed: 1) HMO and 2) PPO.  The option HMO is highlighted.  In addition there are two checkboxes labeled: "Add Vision" and "Add Dental".  Both of these are unchecked.  There is a button labeled "Calculate"  The last component on the screen is a textbox labeled "Total Cost" and it is blank.

A Black-Box test suite might look something like this.  For simplicity only Execution Steps and Expected Behavior is shown.

Execution Steps

Expected Behavior

HMO, check Vision, click Calculate

$125 is the output

PPO, check Dental, click Calculate

$170 is the output

I might really like this test suite.  I test HMO and PPO.  I test Vision and non-Vision.  I test Dental and non-Dental.  It is perfect, right? 

But there are a few of ways that the calculation can be coded.  Here is one of them.  Line numbers have been added to the far left to make it easy to reference sections of the code. 

Code Example 1

 1 public float calculateInsurance(String health, boolean vision, boolean dental)
 2    {
 3        float tempCalculation;     // create a variable to hold total
 4       
 5        if (health.equals("HMO"))  // if HMO is select
 6            tempCalculation = 100.0f;   // start with $100 insurance total
 7        else                       // if it isn't HMO, it must be PPO
 8           tempCalculation = 150.0f;   // start with $150 insurance total
 9       
10        if (vision == true)        // if vision is selected
11           tempCalculation = tempCalculation + 25.0f;  // add $25 to total
12       
13        if (dental == true)        // if dental is selected
14            tempCalculation = tempCalculation + 20.0f;  // add $20 to total
15       
16        return tempCalculation;   // return variable that holds the total
17    }

But it is not the only way to code these requirements.  Here is another option. 

Code Example 2

 1   public float calculateInsurance(String health, boolean vision, boolean dental)
 2    {
 3        float tempCalculation;     // create a variable to hold total
 4        
 5        if (health.equals("HMO"))  // if HMO is select
 6        {
 7            tempCalculation = 100.0f;   // start with $100 insurance total
 8            if (vision == true)        // if vision is selected
 9                tempCalculation = tempCalculation + 25.0f;  // add $25 to total
10       
11            if (dental == true)        // if dental is selected
12                tempCalculation = tempCalculation + 20.0f;  // add $20 to total
13        }
14        else                       // if it isn't HMO, it must be PPO
15        {
16            tempCalculation = 150.0f;   // start with $150 insurance total
17            if (vision == true)        // if vision is selected
18                tempCalculation = tempCalculation + 25.0f;  // add $25 to total
19       
20            if (dental == true)        // if dental is selected
21                tempCalculation = tempCalculation + 20.0f;  // add $20 to total
22        }
23
24        return tempCalculation;   // return variable that holds the total
25    }
