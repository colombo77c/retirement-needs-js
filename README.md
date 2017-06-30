# Background Info
A clickable wireframe for the onboarding process of the personal pension is available here: https://projects.invisionapp.com/share/BTBOJW1CE#/screens/234549145

## Inputs
The user is starting the process of creating their own personal pension. In this process the user gives us some basic personal information:

1. Whether the pension is just for them or if they are including their spouse
2. Whether they have saved for retirement and if so, how much
3. Gender
4. Birthdate
5. Annual Income
6. Zipcode

## Display Page
![screen shot 2017-05-25 at 11 18 19 am](https://user-images.githubusercontent.com/2508473/27715608-6250ad8a-5d06-11e7-8e9d-ae471fc622c0.png)

After we get this info, we estimate a couple things and show them to the user on the “Display” page:
1. The total amount of income per month they will need in retirement. This is based off their annual income and current age.
2. The social security benefit they will receive when they retire. Calculating this accurately requires more information than we have asked (we need their full salary history) so this is an estimate as well.
3. The amount of money they should put into a personal pension which is #1 - #2
(https://projects.invisionapp.com/share/BTBOJW1CE#/screens/234849932)

## Editing
![screen shot 2017-05-25 at 11 18 19 am](https://user-images.githubusercontent.com/2508473/27715554-1c9d67b0-5d06-11e7-8572-28cb629ce6f0.png)

From the “Display” page, a user can edit their inputs by clicking “I’d like to modify this”. They will then be taken to the “Edit” page.

“Edit” Page
<img width="952" alt="screen shot 2017-06-29 at 8 08 43 pm" src="https://user-images.githubusercontent.com/2508473/27715665-c74830d2-5d06-11e7-8d48-9d621ce66303.png">


# Project
The project is to implement the “Edit” page in isolation. The functionality of this page including what is in scope and what is out of scope for this project is described below.

## Text Items
The left side of the “Edit” page has several text items, some are editable text fields, some are just displayed text. The fields are related by the logic described below: 
1. Retirement Age: The age the user is going to retire at
2. Spouse Retirement Age: The age the user’s spouse will be when the primary user retires
3. Retirement Income Goal: The user’s goal for total monthly income in retirement
4. Social Security: The amount that the user plans to collect from social security per month
5. Spouse’s Social Security (Assume for now that the user told us they have a spouse) - The amount that the user expects his/her spouse to collect from social security per month
6. Other Income Source: The amount of ‘other’ income that the user expects to collect per month
7. Total Existing Income: #4 + #5 + #6
8. Retirement Income Gap: MAX(#3 - #7 , 0)
9. Portion to fill: The % of the ‘Retirement Income Gap’ to fill
10. Personal Pension Target: #8 * (#9 / 100)

## Bar Chart
1. The bar has a fixed height
2. The bar has up to 3 sections, that each have height proportional to the income sources that they represent. The sections are:
   - Total Existing Income (#7)
   - Personal Pension Target (#8)
   - Gap
      - If Portion to Fill (#9) is less than 100%, then there will be some Retirement Income Gap (#8) that is not accounted for. This is a ‘Gap’ and should have its own section in the bar chart. If there is no Gap then this section isn’t shown
3. The bar shows Retirement Age (#1) at the bottom
4. The bar should label the different sections. These labels don’t necessarily need to look like they do in the wireframes (In particular, putting labels in the bar itself is known to be potentially problematic and can be replaced by something that works better).
## Desired Functionality
### User’s can edit any of the income amount (#3, #4, #5, #6) or portion to fill (#9) fields
1. Any linked text items should update by following the calculations detailed in Text Fields
2. Bar chart should update according to the new values
![portion-to-fill](https://user-images.githubusercontent.com/2508473/27715705-fa2b45e8-5d06-11e7-8cf8-158143a3d1f0.gif)

### User can edit Retirement Age (#1)
1. When a user updates his/her Retirement Age (#1) it makes our estimated values for Retirement Income Goal (#3), Social Security (#4) and Spouse Social Security (#5) outdated. After the user updates his/her retirement age, we should show refresh indicators next to the outdated fields (#3, #4, #5). The user can click on these refresh buttons to get an updated estimate for what his/her retirement income goal should be as well as what Abaris estimates his/her social security payments will be.'
![retirement-age](https://user-images.githubusercontent.com/2508473/27715716-0d756ca0-5d07-11e7-91f7-ae88435ab52a.gif)


### Currency fields format currency correctly
All dollar formatted fields should display currency values correctly. They should not allow the user to enter cents

## Out of Scope
1. “Nevermind, take me back.” and “All set to continue!” buttons. These go to other pages and don’t need to be included.
2. Calculations for updating Retirement Income Goal and Social Security fields referenced in User can edit Retirement Age (#1). Please return static or random data.
3. Anything outside of the red box shown below. You don’t need to make any containing page, it can just be a component on a white page.
<img width="870" alt="screen shot 2017-05-25 at 11 48 26 am" src="https://user-images.githubusercontent.com/2508473/27715733-1f0df338-5d07-11e7-8ea2-defb51f0f092.png">

