# School_District_Analysis
<p align="center">
  <img src="ScreenShots/Student_Data_Comparison.PNG" width="700">
</p>


## Table of Contents
* [Overview of Project](https://github.com/rkaysen63/School_District_Analysis/blob/master/README.md#overview-of-project)
* [Resources](https://github.com/rkaysen63/School_District_Analysis/blob/master/README.md#resourcess)
* [Results](https://github.com/rkaysen63/School_District_Analysis/blob/master/README.md#results)
* [Summary](https://github.com/rkaysen63/School_District_Analysis/blob/master/README.md#summary)

## Overview of Project
City School System has requested help with analyzing district and student data to determine the top and bottom performing schools in the district and to see if school spending per capita, school size, or school type have any type of relationship to school performance.  After the initial data was analyzed, it was discovered that math and reading scores from the ninth grade class of Thomas High School (THS) had to be removed from the data set because of evidence of academic dishonesty and the data re-analyzed.  

The opening image compares the original `student_data_df`, lower dataframe, to the refactored `student_data_df`, upper dataframe, where the ninth grade math and reading scores for THS were replaced with "NaN".  

Python through Jupyter Notebook interface was used to pull in and analyze data from two sources referenced below.

## Resources

* Data Sources:
  * students_complete.csv
  * schools_complete.csv
* Software: Python 3.7.9 in Jupyter Notebook interface
* Lesson Plan: UTA-VIRT-DATA-PT-02-2021-U-B-TTH, Module 4 Challenge
* Readme Markdown Help:
  * Reference resizing images: https://gist.github.com/DavidWells/7d2e0e1bc78f4ac59a123ddf8b74932d

## Results
Results: Using bulleted lists and images of DataFrames as support, address the following questions.

* ### District Summary 
  <p align="center">
  <img src="ScreenShots/District_Summary_Comparison.png" width="900">
  </p>
  The image above shows a comparison of the *District Summary*, i.e `district_summary_df` dataframe, after Thomas High School's (THS) ninth grade math and reading scores were removed to the `district_summary_df` of the original analysis.  The effect is so small as to be considered negligible.  Only a difference of 0.1 points is seen in the Average Math Score for the district.  It is not a surprise that the removal of THS's ninth grade scores had so little impact on the overall district scores because the THS's ninth grade class of 641 students is only 1.6 % of the district's total student population of 39169.

* ### School Summary 
  <p align="center">
  <img src="ScreenShots/School_Summary_Comparison.png" width="900">
  </p>
  Since the *School Summary*, i.e. `per_school_summary_df`, displays the results by each school in the district, only the results of THS were affected by removing THS's ninth grade math and reading scores.  Compare the lines that are highlighted in gold.  The lower dataframe is from the original analysis.  The upper dataframe is the refactored analysis that excludes THS's ninth graders' math and reading scores. THS's average math score went down < 0.1 points and their average reading score went up < 0.1 points by removing their ninth graders' scores.  The effect is so small as to be considered negligible.
  
* Because the effect of replacing the ninth graders' math and reading scores with NaN is negligible, Thomas High School's performance relative to the other schools did not change.

* ### Top Five Performing Schools
  <p align="center">
  <img src="ScreenShots/Top_Schools_Comparison.png" width="900">
  </p> 
  The highest performing schools are shown above.  Since Thomas High School (THS), highlighted in gold in both dataframes, is included in the top 5, the top five schools was shown twice to demonstrate that THS's rank in the top five did not change as a result of removing its ninth grade math and reading scores from the data.
  
* ### Bottom Five Performing Schools
  <p align="center">
  <img src="ScreenShots/Low_Performing_Schools.png" width="900">
  </p> 
  The lowest performing schools are shown above. This dataframe is shown only one time because Thomas High School does not fall in this category before or after removing the ninth graders' math and reading scores.
  
* ### Math and Reading Scores by Grade
  <p align="center">
  <img src="ScreenShots/Math_Read_Grade_Comparison.png" width="800">
  </p> 
  The comparison above of the original *Math and Reading Scores by Grade* to the *Math and Reading Scores by Grade* after the THS ninth graders' math and reading scores were removed show that the ninth graders' grades appear as NaN, i.e. a null value, in the subsequent dataframe.

* ### Scores by School Spending Per Capita
* <p align="center">
  <img src="ScreenShots/Scores_by_Spending_per_Capita_Comparison.png" width="800">
  </p> 
  The comparison above of the original *Scores by Spending Ranges (Per Student)* to the revised *Scores by Spending Ranges (Per Student)* after THS ninth graders' math and reading scores were removed shows no difference in the results.  The dataframe, `scores_by_school_spending_df`, shows that regardless of the amount spent on each student, reading averages are about the same across the spending ranges, but the math scores actually decreased slightly for schools that spent more money per student.

* ### Scores by School Size
  <p align="center">
  <img src="ScreenShots/Scores_School_Size_Comparison.png" width="800">
  </p> 
  The comparison above of the original *Scores by School Size* to the revised *Scores by School Size* after THS ninth grader's math and reading scores were removed show no difference in the results.  The dataframe, `scores_by_size_df`, shows that math and reading averages are about the same for small and medium schools, but the math and reading scores decreased for larger schools.
  
* ### Scores by School Type
  <p align="center">
  <img src="ScreenShots/Scores_School_Type_Comparison.png" width="800">
  </p> 
  The comparison above of the original *Scores by School Type* to the revised *Scores by School Type* after THS ninth grader's math and reading scores were removed show no difference in the results.  The dataframe, `scores_by_type_df`, shows that Charter Schools perform slightly better than District Schools in both math and reading.

## Summary
Summarize four major changes in the updated school district analysis after reading and math scores for the ninth grade at Thomas High School have been replaced with NaNs.
1. Replace student grades for ths ninth graders with nan
2. Recalculate passing % w clean data, i.e. ths ninth gr removed.
3. Create a dataframe of all students from ths passing math, again passing reading, again passing both
4. Using dataframes above get % from ths 10-12. replace math, reading, overall % in school summary for ths
5. Calculate the number of THS students 10-12th
