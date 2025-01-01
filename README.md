Welcome, to the "Cow Pairing Algorithm for up to Size 4 Groups and 8 Modifiable Variables. Version 1."
(COPAL-4G8V-1, in short)

You are free to use it! So long as you give me the proper credits!

#Credits ----------------------------------------------------------------------

This code was written in December of 2024, by José Eduardo Nieto Domínguez 
(https://orcid.org/0009-0003-9136-1839)

If you require any assistance in running it, or have any questions,
please email me at: "nietodominguez.je@gmail.com"

I will be happy to help, in spanish or english!

#Brief description ------------------------------------------------------------

My code is extensively commented, explaining each section in further detail.

It was designed to assist in experiments that require grouping cows, as similar as possible,
in groups of 2, 3 or 4, considering up to 8 modifiable variables.

The code's results change depending on the modifications done by its user on the first
sections. Mainly, on the "Variables modifiable at the user's discretion", and
"Values modifiable at the user's discretion" sections. Before you do anything with the code,
It is advised to read thoroughly the comments in both sections, plus the ones left in 
the "Main data frame" section.

It works as follows:

1. The code creates a main data frame (DF_Main), using a file named "Base_Original_Vacas.csv".
2. Filters DF_Main by up to two variables that have upper and lower limits, set by its user.
3. Runs a 40-step loop that pairs the remaining cows in groups of a user-chosen size, looking for
their ideal parings. It does so by looking for cows that have the lowest total coefficient of variance (CV_TOTAL),
chosen between those who have a user-chosen maximum amount of coefficient of variance (MaxCV) in all their variables, and,
ideally, also have the same values in up to two variables. When all the cows are paired or filtered out, the loop ends.
4. Saves all the pairings created as a data frame (DF_TotalPairings).
5. Chooses randomly a user-set amount of pairings among DF_TotalPairings and saves them as another data frame (DF_Final).
6. Creates csv and xlsx files, for both DF_TotalPairings and DF_Final, and saves them on the working directory.
7. Prints an "All done!" confirmation message.

#General considerations ------------------------------------------------------------

1. You need the tidyverse and openxlsx libraries to work properly. The code has comments on how to install them. 
2. The code uses placeholder names for all its variables (it is explained in the "Variables modifiable at the user's discretion" section).
3. You might have to replace those names (using Ctrl + F).
4. IN YOUR ORIGINAL FILE (in this case, "Base_Original_Vacas.csv", YOU MUST HAVE ALL THE VARIABLES CONSIDERED IN THIS CODE, AND THEIR NAMES MUST BE EXACTLY THE SAME -- whether you renamed the placeholders or not --. If that is not the case, then the code will not work.
5. You can just have columns filled with 1's on your "Base_Original_Vacas.csv" file, named after the variables you are not going to use or consider.
6. You might have to replace the values in the "Values modifiable at the user's discretion" section.
7. The code only works with GroupSizeWanted 2, 3 and 4. If you save any other number as that object, the code will not work.
8. The code only works when the value saved as PairingsChosen is smaller than the total amount of observations in the DF_TotalPairings data frame. Because of that, it is adviced that you set that value as low as possible at first, and then tweak it and re-run the code as many times as you need it.
9. This code's objective is to save you time when pairing cows, but you first have to know what you want, what you are doing, and modify the variables and values you need! It does not read minds!
10. If you have any existing csv or xlsx file named "DF_Final", or "DF_TotalPairings" in your working directory, you should delete them, save them somewhere else, or rename them. Otherwise, the code will not save the files created when you run it.
11. This also happens when you re-run the code.
12. You can, of course, change the name of the file used to create DF_Main. "Base_Original_Vacas.csv" es merely an example.

#Example file: "Base_Original_Vacas.csv" ------------------------------------------

You can find it within this repository. It has only three relevant variables (besides ID), which are expected to be the replacements of:
1. "DIM" - Replaces "FilterMinMax_O" in the code.
2. "MAVG" - Replaces "Variable_A" in the code.
3. "LACT" - Replaces "FilterEquals_Y" in the code.

If you wish to use this file to do a trial run of the code, you should:
1. Un-comment (remove the "#" character before "install.packages") lines 34 and 35, so you install the tidyverse and openxlsx libraries.
2. Replace the working directory to the one you will be using.
3. Replace the three mentioned placeholder variables with DIM, MAVG and LACT. You can do that using Ctrl + F.
4. Set the value in Filter_FilterMinMax_O_LowerLimit (named Filter_DIM_LowerLimit, after the correct replacement) as 55.
5. Set the value in Filter_FilterMinMax_O_UpperLimit (named Filter_DIM_UpperLimit, after the correct replacement) as 133.
6. Set the value in PairingsChosen as 24.

If you did everything correctly, you will have two DF_TotalPairings files (one csv, the other xlsx) with 25 observations of all the variables (where the meaningful data is on the DIM, MAVG and LACT variables), plus the DF_TotalPairings files with 24 observations. Everything here is done for groups Size 2 -- Which means you will have data for COW1 and COW2 --. 


#ENJOY! Hope this helps!
