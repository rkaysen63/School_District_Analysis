# School_District_Analysis
<p align="center">
  <img src="ScreenShots/Student_Data_Comparison.PNG" width="700">
</p>


## Table of Contents
* [Overview of Project](https://github.com/rkaysen63/School_District_Analysis/blob/master/README.md#overview-of-project)
* [Resources](https://github.com/rkaysen63/School_District_Analysis/blob/master/README.md#resources)
* [Results](https://github.com/rkaysen63/School_District_Analysis/blob/master/README.md#results)
* [Summary](https://github.com/rkaysen63/School_District_Analysis/blob/master/README.md#summary)

## Overview of Project
City School System has requested help with analyzing district and student data to determine the top and bottom performing schools in the district and to see if school spending per capita, school size, or school type have any type of relationship to school performance.  After the initial data was analyzed, it was discovered that math and reading scores from the ninth grade class of Thomas High School (THS) had to be removed from the data set because of evidence of academic dishonesty and the data re-analyzed.  

The opening image compares the original `student_data_df`, lower dataframe, to the revised `student_data_df`, upper dataframe, where the ninth grade math and reading scores for THS were replaced with "NaN".  

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

* ### District Summary 
  <p align="center">
  <img src="ScreenShots/District_Summary_Comparison.png" width="900">
  </p>  
  The image above shows a comparison of the "District Summary" dataframe, after Thomas High School's (THS) ninth grade math and reading scores were removed to the "District Summary" of the original analysis.  The effect is so small as to be considered negligible.  Only a difference of 0.1 points is seen in the Average Math Score for the district.  It is not a surprise that the removal of THS's ninth grade scores had so little impact on the overall district scores because the THS's ninth grade class of 641 students is only 1.6 % of the district's total student population of 39,169.

* ### School Summary 
  <p align="center">
  <img src="ScreenShots/School_Summary_Comparison.png" width="900">
  </p>  
  Since the "School Summary" dataframe displays the results by each school in the district, only the results of THS were affected by removing THS's ninth grade math and reading scores.  Compare the lines that are highlighted in gold.  The lower dataframe is from the original analysis.  The upper dataframe is the revised analysis that excludes THS's ninth graders' math and reading scores. THS's average math score went down < 0.1 points and their average reading score went up < 0.1 points by removing their ninth graders' scores.  The effect is so small as to be considered negligible.
  
* Because the effect of replacing the ninth graders' math and reading scores with "NaN" is negligible, Thomas High School's performance relative to the other schools did not change.

* ### Top Five Performing Schools
  <p align="center">
  <img src="ScreenShots/Top_Schools_Comparison.png" width="900">
  </p> 
  The highest performing schools are shown above.  Since Thomas High School (THS), highlighted in gold in both dataframes, is included in the top 5, the top five schools are shown twice to demonstrate that THS's rank in the top five did not change as a result of removing its ninth grade math and reading scores from the data.
  
* ### Bottom Five Performing Schools
  <p align="center">
  <img src="ScreenShots/Low_Performing_Schools.png" width="900">
  </p>  
  The lowest performing schools are shown above. This dataframe is shown only one time because it did not change after removing THS's ninth graders' math and reading scores.
  
* ### Math and Reading Scores by Grade
  <p align="center">
  <img src="ScreenShots/Math_Read_Grade_Comparison.png" width="800">
  </p>   
  The comparison above of the original "Math Scores by Grade" and "Reading Scores by Grade" dataframes to the "Math Scores by Grade" and "Reading Scores by Grade" dataframes after removing THS's ninth graders' math and reading scores show that the ninth graders' scores appear as "NaN", i.e. a null value, in the revised dataframes.

* ### Scores by School Spending Per Capita
  <p align="center">
  <img src="ScreenShots/Scores_by_Spending_per_Capita_Comparison.png" width="800">
  </p> 
  The comparison above of the original "Scores by Spending Ranges (Per Student)" to the revised "Scores by Spending Ranges (Per Student)" after THS's ninth graders' math and reading scores were removed shows no difference in the results.  Per the results shown in "Scores by Spending Ranges (Per Student)", reading averages are about the same across regardless of the amount spent per student, whereas math scores decrease slightly for schools that spend more money per student.  Apparently there are other factors involved, that may include a more diverse population in larger schools.

* ### Scores by School Size
  <p align="center">
  <img src="ScreenShots/Scores_School_Size_Comparison.png" width="800">
  </p> 
  The comparison above of the original "Scores by School Size" to the revised "Scores by School Size" after THS's ninth graders' math and reading scores were removed show no difference in the results.  Per the results shown in "Scores by School Size", math and reading averages are about the same for small and medium schools, but the math and reading scores decrease for larger schools.
  
* ### Scores by School Type
  <p align="center">
  <img src="ScreenShots/Scores_School_Type_Comparison.png" width="800">
  </p> 
  The comparison above of the original "Scores by School Type" to the revised "Scores by School Type" after THS's ninth graders' math and reading scores were removed show no difference in the results.  Per the results shown in "Scores by School Type", Charter Schools perform slightly better than District Schools in both math and reading.

## Summary
* In order to provide a fair comparison across district schools, Thomas High School's ninth grade math and reading scores were removed from the dataframe, `student_data_df`, and replaced with null, i.e. "NaN".  The numpy dependency was imported to use `np.nan` to quickly substitute "NaN" in place of the ninth graders scores.   
    `import numpy as np`  
    `student_data_df.loc[(student_data_df["school_name"] == "Thomas High School") & (student_data_df["grade"] == "9th"), "reading_score"] = np.nan`   
  The revised `student_data_df` was merged with the `school_data_df` to form a new, "clean" `school_data_complete_df` that includes null ("NaN") values for THS's ninth graders' math and reading scores.

* In creating the District Summary, `district_summary_df`, the average math and reading scores are calculated from the "clean" `school_data_complete_df`, so that the mean of math and reading scores no longer include THS's ninth graders' scores because they are "NaN".  For example:    `average_math_score = school_data_complete_df["math_score"].mean()`<br/>
In order to calculate the passing math, reading and overall percentages, the total student count had to be revised to exclude THS's ninth graders.  The ninth grade count was obtained using the .loc method and subtracting the total student count. \
  `ths_9th_gr_count = school_data_complete_df.loc[(school_data_complete_df["school_name"] == "Thomas High School") & (student_data_df["grade"] == "9th"), "Student ID"].count()`   
  `student_count = school_data_complete_df["Student ID"].count()` \
  `student_count_wo_ths9th = student_count - ths_9th_gr_count` \
  Passing rates were from the "clean" `school_data_complete_df`.  The code included a statement to pull only math, or reading, or both scores from the dataframe that are greater than or equal to 70. Calculation of the overall passing math and reading percentage is shown below to illustrate.  \ 
  `passing_math_reading = school_data_complete_df[(school_data_complete_df["math_score"] >= 70) & (school_data_complete_df["reading_score"] >= 70)]` \
  `overall_passing_math_reading_count = passing_math_reading["student_name"].count()` \ `overall_passing_percentage = overall_passing_math_reading_count/float(student_count_wo_ths9th) * 100`

* The procedure for creating the School Summary, `school_summary_df` without THS's ninth graders' math and reading scores, began exactly the same as before, except after it was created the tenth through twelfth grade passing percentages were calculated separately and inserted into the dataframe to replace the percentages that were calculated using the entire student population to create a "clean" `school_summary_df`.  As before, number of Series were created using the `df.groupby()` functionto calculate the mean for budget, math and reading and filtered dataframes were created for passing math and reading scores using.  Example of calculating the average budget using `groupby()`:  
`per_school_budget = school_data_complete_df.groupby()["school_name"].mean()["budget"]`   
  The average math and reading scores for THS will reflect that the ninth graders' scores are "NaN".  But the percentages will not be correct because the school count was not adjusted to omit the ninth graders from the count.  In order to record the correct passing math, passing reading and passing overall percentages for THS, the correct number of students had to be calculated.  Since the ninth graders were taken out of the equation, the correct student count is the total number of students at THS minus total number of ninth graders.   
  `ths_all_gr_count = school_data_complete_df.loc[(school_data_complete_df["school_name"] == "Thomas High School"), "Student ID"].count()`    
  `ths_9th_gr_count = school_data_complete_df.loc[(school_data_complete_df["school_name"] == "Thomas High School") & (student_data_df["grade"] == "9th"), "Student ID"].count()`    
  `ths_gr10to12_count = ths_all_gr_count - ths_9th_gr_count`   
  Now that the number of tenth through twelfth graders is calculated, new passing perecentages were calculated.  The overall passing math and reading is shown below to illustrate.  
  `ths_passing_math_reading_count = school_data_complete_df.loc[(school_data_complete_df["school_name"] == "Thomas High School") & (school_data_complete_df["math_score"] >= 70) & (school_data_complete_df["reading_score"] >= 70),"Student ID"].count()`  
  `ths_10to12_passing_math_reading_percentage = ths_passing_math_reading_count / ths_gr10to12_count * 100`   
  Finally, these new percentages had to be inserted into `school_summary_df`, replacing the ones that were there.   
  `new_ths_passing_math_reading_percentage = per_school_summary_df.loc["Thomas High School", "% Overall Passing"] = ths_10to12_passing_math_reading_percentage`
  

