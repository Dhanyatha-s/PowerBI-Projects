
# HR DATA DYMANICS
![Connecting you to the future](https://github.com/user-attachments/assets/89de9afc-513d-4228-91b6-167289a52cb1)
### I have taken this dataset from codebasics.io, where i wanted to understand the analysis of this perticular data,   
### So Here is what i did here:  
> YEAH !!! ITS A YOUTUBE PROJECT BUT FOR ME VERY INSIGHTFULL
### Brief Intro to dataset
#### Ii's a dataset consist of employees name, there mode of working, and when they have taken leaves and  3 months of dates corresponding to  each indivduals workng status [are they wroking from office, home, half day WFH or WFO, did tehy taken sick-leaves and holidays and more]:
> Their fiscal year starts @ April.......
## STAKEHOLDER END:
### So as for the stakeholder, they need to know the   
1. How many percentage of employees are doing WFH  
2. What is  percentage of employees presence overall
3. How many percentage of employees are doing WFH

> [!NOTE]
> This may seem simple tasks to know, but when you understand the data given by stakeholder you will know the challenges as 'BIGINNER'.
### Okay!!, WHAT'S TEH CHALLENGE.....  
#### Challenge was to format the date table as it was the excel sheets with 3 different month's date data in 3 differents sheets.  
#### Had to transfrom the data into structured data schema.    
> [!TIP]
> Combine the data from different sheets in PowerBI
### HOW
#### POWERBI ---->  Load the data and transfrom,  
NOW 1. Duplicate it and transfrom it with date sheet, "MAKE SURE YOU DELETE "CHANGE TYPE" In Transformation steps" so it takcles the challenge that we have.   
2. and do transformation.  
3. Always remember if any colums's data is in row : change to UNPIVOT OTHER COLUMN in transfrom by keeping what column you want. here thats what i did.   
4. Lets create Parameters and use the parameter to create Function. So that the transfromation steps we used to change the structure of date sheet to date column. can be applied to across the table contenst --> "REUSABILITY".   
5. After Creating the function invoke it with "INVOKE CUSTOME FUNCTION" by adding the column to the table we Duplicated.  
> Till here i transformaed the data sheets to data table with appropriate EDA.  
> NOW MY DATA SET [Final Data] CONSIST OF  
> 1. Employees Name  
> 2. value [ its the keys to refer the mode of working ]  
> 3. Date [ consist of 3 month's date ]  
> 4. Item [ refers to the months ]  
Additional Colums to support the data analysis
> Create Month Column
```
Month = startofmonth('Final Data' [Date])
```
> Days of Week Column
```
Days of Week = Format('Final Data'[Date], "ddd" )
```


### HERE NOW I WILL CREATE METRICS TO FIND THE INSIGHTS TO STAKEHOLDER PROBLEM STATEMENTS  
In order to find the % of  presence of employees  and others, need to find the ratio of  working days so for from the data table.   
so that we can get no. of Present of Employees VS Total Working Days. 
no. of Absent VS Total Working Days. 
no. of WFH VS Total Working Days. 
no. of HOlidays VS Total Working Days. 
and more...   
#### Lets Calcuate Total Working Days using DAX Formula   
```
Total working days = var total-days = count('Final Data'[values]
                      var non-working-days = calculate(Count('Final Data'[values] in {'WO', 'HO'} )
Return
total-days - non-working-days
```
### Now Calculate the Present days  
Beffore that we'll find need to include WFH HWFH, to the Work from office   
```
WFH Count = Switch(True(), 'Final Data'[Values] = 'WFH' , 1 ,
                            'Final Data'[Values] = 'HWFH' , 0.5 , 0)
```  
Now 
```   
Present days =  count('Final Data'[values],
                      'Final Data'[values] = 'P' )
Return
Present days + [WFH Count]
```  
Like wise will create Percentage of precence  
```
Presence % = Divide(Present days, [total working days] , 0 )
```

Now For WFM %  
```
WFH % = Divide([WFH Count], [total working days] , 0 )
```
NOW FOR SICK Leaves  
```
SL Count = Switch(True(), 'Final Data'[Values] = 'SL' , 1 ,
                            'Final Data'[Values] = 'HSL' , 0.5 , 0)
``` 

Now For SL %  
```
SL % = Divide([SL Count], [total working days] , 0 )
```
### All this to get the insights from the dashboard.   
![HR Data Analytics_page-0001](https://github.com/user-attachments/assets/2b4f34cc-fe62-4f95-9f82-667bf50a88a8)   

![image](https://github.com/user-attachments/assets/96d4663a-5906-4520-8c5d-dcfa002ee514)
### And we can analyze "On What Days most of the employess were present, had taken work from home and sick leaves"   
### We can Check on each Employees and analyze thier working patterns when are they most present and other categories too.  


### This is about the small amount of data where it let me understand the most of power quiery formuals and how to combine different sheets into powerbi, how to create parameter and functons to keep the transfromations to make dynamic changes across the data table, how to create measures and DAX formulas , Most Impoertant formulas [ Calculate functions], and building the Dashboard and formatting it wth styles and it fun to do even if its begInner project...   
# FROM BEGIN ITSELF IS THE 1ST STEP OF SUCCESS
 




