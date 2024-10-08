# Student Test Project Assessment: Data Modeling, Data Cleaning & Transformation

## Project Overview
In this project, you will work with a dataset of student test scores to build a data model, clean the data, and transform it using the concepts of data modeling, DAX, and Power BI functions learned in class.

### Dataset Description:
The dataset contains student test results from multiple classes. It includes the following columns:

- **StudentID**: A unique identifier for each student.
- **StudentName**: The name of the student.
- **Class**: The class or section the student belongs to.
- **Subject**: The subject for which the test was conducted.
- **TestDate**: The date the test was taken.
- **Score**: The score obtained by the student.
- **MaxScore**: The maximum score possible for the test.

### Objective:
You are required to:
1. Clean and transform the data to remove errors and inconsistencies.
2. Create a data model to enable analysis of student performance.
3. Use DAX to perform calculations such as the average score, total score, and pass/fail status.
4. Build visualizations to present key insights from the dataset.

---

## Step 1: Data Cleaning & Transformation

### Tasks:
1. **Handling Missing Values**:
   - Identify missing values in the `StudentName`, `TestDate`, and `Score` columns.
   - Replace missing values in the `StudentName` with "Unknown" and in the `Score` with 0.

   ```dax
   CleanedData = IF(ISBLANK([StudentName]), "Unknown", [StudentName])
   ```
2. **Correcting Data Types**:

- Ensure that the TestDate is recognized as a date, Score and MaxScore are numbers, and StudentID is a whole number.
3. **Outlier Detection**:

- Detect any outliers in the Score column (e.g., scores greater than MaxScore) and correct them by setting the score equal to MaxScore.
4. **Removing Duplicates**:

- Remove any duplicate entries based on the StudentID, TestDate, and Subject
```DAX
  DISTINCT(
    SELECTCOLUMNS(
        Students,
        "StudentID", Students[StudentID],
        "TestDate", Students[TestDate],
        "Subject", Students[Subject]
    )
)
```
## Step 2: Data Modeling
### Tasks:
1. **Creating Relationships**:

- You will create relationships between tables using StudentID to link the student information with the test results.
2. **Calculated Columns**:

- Create a calculated column for the Pass/Fail Status based on the score. Assume that a score of 50 or more is a pass.
3. **Calculated Columns for Percentage Score**:

- Add a calculated column to compute the Percentage Score for each student by dividing the Score by the MaxScore.

4. **Creating Measures**:

- Create a measure for the Total Score obtained by a student across all tests.
- Create a measure for the Average Score across all students.
5. **Creating a "What-If" Parameter**:

- Create a What-If parameter to simulate different passing thresholds (e.g., 40, 50, 60) and observe how the pass/fail status changes.
  
## Step 3: DAX Calculations & Table Functions
### Tasks:
1. **Aggregating Data**:

- Use X Functions to compute the average score for each student, taking into account each subject.
2. **Filtering**:

- Use the FILTER function to filter out students who have failed more than 2 tests.

3. **Table Function**:

- Use ALL to remove filters and calculate the overall class average regardless of the subject or class.


## Step 4: Building Visualizations
### Tasks:
1. **Student Performance Dashboard**:
#### Create a dashboard showing the following:
- The average score by class and subject.
- The total number of students who passed and failed.
- A line graph showing the trend of test scores over time.
- What-If Parameter Visualization:

- Use the What-If parameter to create a slicer in your report, allowing users to adjust the passing threshold and view how the pass/fail distribution changes.
## Step 5: Final Report
1. **Deliverables:
#### A Power BI report containing:
- Cleaned and transformed dataset.
- Data model with calculated columns, measures, and relationships.
- Visualizations that provide insights into student performance.
- A brief write-up summarizing:
- Your approach to data cleaning and transformation.
- Key calculations and insights from your data model.
- Screenshots of the final dashboard.

# Data Sets
| StudentID | FirstName   | LastName    | TestDate   | Subject      | Score | MaxScore |
|-----------|-------------|-------------|------------|--------------|-------|----------|
| 1         | Emily       | Johnson     | 3/15/2024  | Mathematics  | 85    | 100      |
| 1         | Emily       | Johnson     | 3/15/2024  | English      | 75    | 100      |
| 1         | Emily       | Johnson     | 3/15/2024  | Science      | 90    | 100      |
| 1         | Emily       | Johnson     | 3/15/2024  | History      | 88    | 100      |
| 1         | Emily       | Johnson     | 3/15/2024  | Geography    | 80    | 100      |
| 2         | Noah        | Smith       | 3/15/2024  | Mathematics  | 78    | 100      |
| 2         | Noah        | Smith       | 3/15/2024  | English      | 85    | 100      |
| 2         | Noah        | Smith       | 3/15/2024  | Science      | 75    | 100      |
| 2         | Noah        | Smith       | 3/15/2024  | History      |       | 100      |
| 2         | Noah        | Smith       | 3/15/2024  | Geography    | 70    | 100      |
| 3         | Olivia      | Brown       | 3/15/2024  | Mathematics  | 82    | 100      |
| 3         | Olivia      | Brown       | 3/15/2024  | English      | 78    | 100      |
| 3         | Olivia      | Brown       | 3/15/2024  | Science      | 88    | 100      |
| 3         | Olivia      | Brown       | 3/15/2024  | History      | 84    | 100      |
| 3         | Olivia      | Brown       | 3/15/2024  | Geography    | 79    | 100      |
| 4         | William     | Davis       | 3/15/2024  | Mathematics  | 89    | 100      |
| 4         | William     | Davis       | 3/15/2024  | English      | 80    | 100      |
| 4         | William     | Davis       | 3/15/2024  | Science      | 84    | 100      |
| 4         | William     | Davis       | 3/15/2024  | History      | 90    | 100      |
| 4         | William     | Davis       | 3/15/2024  | Geography    | 76    | 100      |
| 5         | Sophia      | Wilson      | 3/15/2024  | Mathematics  | 87    | 100      |
| 5         | Sophia      | Wilson      | 3/15/2024  | English      | 90    | 100      |
| 5         | Sophia      | Wilson      | 3/15/2024  | Science      | 92    | 100      |
| 5         | Sophia      | Wilson      | 3/15/2024  | History      | 89    | 100      |
| 5         | Sophia      | Wilson      | 3/15/2024  | Geography    | 85    | 100      |
| 6         |             | Martinez    | 3/15/2024  | Mathematics  | 75    | 100      |
| 6         | Liam        | Martinez    | 3/15/2024  | English      | 80    | 100      |
| 6         | Liam        | Martinez    | 3/15/2024  | Science      | 85    | 100      |
| 6         | Liam        | Martinez    | 3/15/2024  | History      | 78    | 100      |
| 6         | Liam        | Martinez    | 3/15/2024  | Geography    | 80    | 100      |
| 7         | Mia         | Miller      | 3/15/2024  | Mathematics  | 83    | 100      |
| 7         | Mia         | Miller      | 3/15/2024  | English      | 85    | 100      |
| 7         | Mia         | Miller      | 3/15/2024  | Science      | 88    | 100      |
| 7         | Mia         | Miller      | 3/15/2024  | History      | 84    | 100      |
| 7         | Mia         | Miller      | 3/15/2024  | Geography    | 77    | 100      |
| 8         | James       | Garcia      | 3/15/2024  | Mathematics  | 80    | 100      |
| 8         | James       | Garcia      | 3/15/2024  | English      |       | 100      |
| 8         | James       | Garcia      | 3/15/2024  | Science      | 86    | 100      |
| 8         | James       |             | 3/15/2024  | History      | 82    | 100      |
| 8         | James       | Garcia      | 3/15/2024  | Geography    | 78    | 100      |
| 9         | Isabella    | Rodriguez   | 3/15/2024  | Mathematics  | 85    | 100      |
| 9         | Isabella    | Rodriguez   | 3/15/2024  | English      | 89    | 100      |
| 9         | Isabella    | Rodriguez   | 3/15/2024  | Science      | 91    | 100      |
| 9         | Isabella    | Rodriguez   | 3/15/2024  | History      | 87    | 100      |
| 9         | Isabella    | Rodriguez   | 3/15/2024  | Geography    | 83    | 100      |
| 10        | Lucas       | Martinez    | 3/15/2024  | Mathematics  | 81    | 100      |
| 10        | Lucas       | Martinez    | 3/15/2024  | English      | 87    | 100      |
| 10        | Lucas       | Martinez    | 3/15/2024  | Science      | 84    | 100      |
| 10        | Lucas       | Martinez    | 3/15/2024  | History      | 79    | 100      |
| 10        | Lucas       | Martinez    | 3/15/2024  | Geography    | 82    | 100      |
| 11        | Charlotte   | Wilson      | 3/15/2024  | Mathematics  | 90    | 100      |
| 11        | Charlotte   | Wilson      | 3/15/2024  | English      | 93    | 100      |
| 11        | Charlotte   | Wilson      | 3/15/2024  |              | 89    | 100      |
| 11        | Charlotte   | Wilson      | 3/15/2024  | History      | 91    | 100      |
| 11        | Charlotte   | Wilson      | 3/15/2024  | Geography    | 88    | 100      |
| 12        | Elijah      | Anderson    | 3/15/2024  | Mathematics  | 82    | 100      |
| 12        | Elijah      | Anderson    | 3/15/2024  | English      | 85    | 100      |
| 12        | Elijah      | Anderson    | 3/15/2024  | Science      | 87    | 100      |
| 12        | Elijah      | Anderson    | 3/15/2024  | History      | 80    | 100      |
| 12        | Elijah      | Anderson    | 3/15/2024  | Geography    | 83    | 100      |
| 13        | Amelia      | Taylor      | 3/15/2024  | Mathematics  | 88    | 100      |
| 13        | Amelia      | Taylor      | 3/15/2024  | English      | 91    | 100      |
| 13        | Amelia      | Taylor      | 3/15/2024  | Science      | 89    | 100      |
| 13        | Amelia      | Taylor      | 3/15/2024  | History      | 86    | 100      |
| 13        | Amelia      | Taylor      | 3/15/2024  | Geography    | 84    | 100      |
| 14        | Benjamin    | Thomas      | 3/15/2024  | Mathematics  | 76    | 100      |
| 14        | Benjamin    | Thomas      | 3/15/2024  | English      |       | 100      |
| 14        | Benjamin    | Thomas      | 3/15/2024  | Science      | 83    | 100      |
| 14        | Benjamin    | Thomas      | 3/15/2024  | History      | 77    | 100      |
| 14        | Benjamin    | Thomas      | 3/15/2024  | Geography    | 79    | 100      |
| 15        | Harper      | Jackson     | 3/15/2024  | Mathematics  | 85    | 100      |
| 15        | Harper      | Jackson     | 3/15/2024  | English      | 87    |          |
| 15        | Harper      | Jackson     | 3/15/2024  | Science      | 92    | 100      |
| 15        | Harper      | Jackson     | 3/15/2024  | History      | 84    | 100      |
| 15        | Harper      | Jackson     | 3/15/2024  | Geography    | 81    | 100      |
| 16        | Ethan       | White       | 3/15/2024  | Mathematics  | 78    | 100      |
| 16        | Ethan       | White       | 3/15/2024  | English      | 85    | 100      |
| 16        | Ethan       | White       | 3/15/2024  | Science      | 83    | 100      |
| 16        | Ethan       | White       | 3/15/2024  | History      | 80    | 100      |
| 16        | Ethan       | White       | 3/15/2024  | Geography    | 75    | 100      |
| 17        | Abigail     | Harris      | 3/15/2024  | Mathematics  | 84    | 100      |
| 17        | Abigail     | Harris      | 3/15/2024  | English      | 87    | 100      |
| 17        | Abigail     | Harris      | 3/15/2024  | Science      | 88    | 100      |
| 17        | Abigail     | Harris      | 3/15/2024  | History      | 83    | 100      |
| 17        | Abigail     | Harris      | 3/15/2024  | Geography    | 81    | 100      |
| 18        | Oliver      | King        | 3/15/2024  | Mathematics  | 82    | 100      |
| 18        |             | King        | 3/15/2024  | English      | 85    | 100      |
| 18        | Oliver      | King        | 3/15/2024  | Science      | 89    | 100      |
| 18        | Oliver      | King        | 3/15/2024  | History      | 86    | 100      |
| 18        | Oliver      | King        | 3/15/2024  | Geography    | 84    | 100      |
| 19        | Evelyn      | Lewis       | 3/15/2024  | Mathematics  | 80    | 100      |
| 19        | Evelyn      | Lewis       | 3/15/2024  | English      | 88    | 100      |
| 19        | Evelyn      | Lewis       | 3/15/2024  | Science      | 90    | 100      |
| 19        | Evelyn      | Lewis       | 3/15/2024  | History      | 85    | 100      |
| 19        | Evelyn      | Lewis       | 3/15/2024  | Geography    | 82    | 100      |
| 20        | Henry       | Scott       | 3/15/2024  | Mathematics  | 87    | 100      |
| 20        | Henry       | Scott       | 3/15/2024  | English      | 89    | 100      |
| 20        | Henry       | Scott       | 3/15/2024  | Science      | 92    | 100      |
| 20        | Henry       | Scott       | 3/15/2024  | History      | 86    | 100      |
| 20        | Henry       | Scott       | 3/15/2024  | Geography    | 90    | 100      |
| 21        | Isabella    | Clark       | 3/15/2024  | Mathematics  | 86    | 100      |
| 21        | Isabella    | Clark       | 3/15/2024  | English      | 88    | 100      |
| 21        | Isabella    | Clark       | 3/15/2024  | Science      | 91    | 100      |
| 21        | Isabella    | Clark       | 3/15/2024  | History      | 85    | 100      |
| 21        | Isabella    | Clark       | 3/15/2024  | Geography    | 82    | 100      |
| 22        | Lucas       | Rodriguez   | 3/15/2024  | Mathematics  | 89    | 100      |
| 22        | Lucas       | Rodriguez   | 3/15/2024  | English      | 90    | 100      |
| 22        | Lucas       | Rodriguez   | 3/15/2024  | Science      | 93    | 100      |
| 22        | Lucas       | Rodriguez   | 3/15/2024  | History      | 88    | 100      |
| 22        | Lucas       | Rodriguez   | 3/15/2024  | Geography    | 84    | 100      |
| 23        | Mia         | Ramirez     | 3/15/2024  | Mathematics  | 77    | 100      |
| 23        | Mia         | Ramirez     | 3/15/2024  | English      | 83    | 100      |
| 23        | Mia         | Ramirez     | 3/15/2024  | Science      | 79    | 100      |
| 23        | Mia         | Ramirez     | 3/15/2024  | History      | 81    | 100      |
| 23        | Mia         | Ramirez     | 3/15/2024  | Geography    | 78    | 100      |
| 24        | James       | Wright      | 3/15/2024  | Mathematics  | 84    | 100      |
| 24        | James       | Wright      | 3/15/2024  | English      | 87    | 100      |
| 24        | James       | Wright      | 3/15/2024  | Science      | 90    | 100      |
| 24        | James       | Wright      | 3/15/2024  | History      | 86    | 100      |
| 24        | James       | Wright      | 3/15/2024  | Geography    | 82    | 100      |
| 25        | Emma        | Lopez       | 3/15/2024  | Mathematics  | 82    | 100      |
| 25        | Emma        | Lopez       | 3/15/2024  | English      | 84    | 100      |
| 25        | Emma        | Lopez       | 3/15/2024  | Science      | 85    | 100      |
| 25        | Emma        | Lopez       | 3/15/2024  | History      | 87    | 100      |
| 25        | Emma        | Lopez       | 3/15/2024  | Geography    | 83    | 100      |
| 26        | Jack        | Green       | 3/15/2024  | Mathematics  | 80    | 100      |
| 26        | Jack        | Green       | 3/15/2024  | English      | 83    | 100      |
| 26        | Jack        | Green       | 3/15/2024  | Science      | 86    | 100      |
| 26        | Jack        | Green       | 3/15/2024  | History      | 79    | 100      |
| 26        | Jack        | Green       | 3/15/2024  | Geography    | 81    | 100      |
| 27        | Noah        | Hill        | 3/15/2024  | Mathematics  | 91    | 100      |
| 27        | Noah        | Hill        | 3/15/2024  | English      | 92    | 100      |
| 27        | Noah        | Hill        | 3/15/2024  | Science      | 94    | 100      |
| 27        | Noah        | Hill        | 3/15/2024  | History      | 89    | 100      |
| 27        | Noah        | Hill        | 3/15/2024  | Geography    | 87    | 100      |
| 28        | Aiden       | Baker       | 3/15/2024  | Mathematics  | 82    | 100      |
| 28        | Aiden       | Baker       | 3/15/2024  | English      | 85    | 100      |
| 28        | Aiden       | Baker       | 3/15/2024  | Science      | 88    | 100      |
| 28        | Aiden       | Baker       | 3/15/2024  | History      | 84    | 100      |
| 28        | Aiden       | Baker       | 3/15/2024  | Geography    | 80    | 100      |
| 29        | Grace       | Adams       | 3/15/2024  | Mathematics  | 78    | 100      |
| 29        | Grace       | Adams       | 3/15/2024  | English      | 81    | 100      |
| 29        | Grace       | Adams       | 3/15/2024  | Science      | 84    | 100      |
| 29        | Grace       | Adams       | 3/15/2024  | History      | 79    | 100      |
| 29        | Grace       | Adams       | 3/15/2024  | Geography    | 76    | 100      |
| 30        | Chloe       | Nelson      | 3/15/2024  | Mathematics  | 85    | 100      |
| 30        | Chloe       | Nelson      | 3/15/2024  | English      | 87    | 100      |
| 30        | Chloe       | Nelson      | 3/15/2024  | Science      | 90    | 100      |
| 30        | Chloe       | Nelson      | 3/15/2024  | History      | 83    | 100      |
| 30        | Chloe       | Nelson      | 3/15/2024  | Geography    | 88    | 100      |




# Comprehensive Student Information Dataset

| StudentID | FirstName | LastName | Gender | DateOfBirth | Class | EnrollmentDate | Address              | ParentContact |
|-----------|-----------|----------|--------|-------------|-------|----------------|----------------------|---------------|
| 1         | Alice     | Johnson  | Female | 2006-03-12  | 10A   | 2021-01-15     | 123 Elm St, Citytown | +254712345678 |
| 2         | Bob       | Smith    | Male   | 2006-06-25  | 10A   | 2021-01-15     | 456 Oak St, Citytown | +254722345679 |
| 3         | Charlie   | Davis    | Male   | 2006-09-10  | 10B   | 2021-01-15     | 789 Pine St, Citytown| +254732345670 |
| 4         | Diana     | Brown    | Female | 2005-11-30  | 11A   | 2020-02-10     | 321 Maple St, Citytown| +254742345671 |
| 5         | Ethan     | Wilson   | Male   | 2005-04-22  | 11B   | 2020-02-10     | 654 Birch St, Citytown| +254752345672 |
| 6         | Fiona     | Taylor   | Female | 2007-01-18  | 9A    | 2022-01-20     | 987 Cedar St, Citytown| +254762345673 |
| 7         | George    | Clark    | Male   | 2006-08-05  | 10A   | 2021-01-15     | 159 Elm St, Citytown | +254772345674 |
| 8         | Hannah    | Adams    | Female | 2005-02-19  | 11A   | 2020-02-10     | 852 Oak St, Citytown | +254782345675 |
| 9         | Ian       | Thompson | Male   | 2006-10-07  | 10B   | 2021-01-15     | 741 Pine St, Citytown| +254792345676 |
| 10        | Jane      | Evans    | Female | 2006-05-29  | 10A   | 2021-01-15     | 963 Maple St, Citytown| +254702345677 |
| 11        | Kyle      | Baker    | Male   | 2007-02-21  | 9B    | 2022-01-20     | 234 Birch St, Citytown| +254712345678 |
| 12        | Laura     | Carter   | Female | 2005-12-12  | 11B   | 2020-02-10     | 432 Cedar St, Citytown| +254722345679 |
| 13        | Mike      | Collins  | Male   | 2006-07-14  | 10A   | 2021-01-15     | 678 Oak St, Citytown | +254732345680 |
| 14        | Nancy     | Cooper   | Female | 2006-04-30  | 10B   | 2021-01-15     | 543 Pine St, Citytown| +254742345681 |
| 15        | Oliver    | Davis    | Male   | 2005-11-01  | 11A   | 2020-02-10     | 234 Maple St, Citytown| +254752345682 |
| 16        | Patricia  | Evans    | Female | 2006-08-15  | 10B   | 2021-01-15     | 789 Cedar St, Citytown| +254762345683 |
| 17        | Quentin   | Foster   | Male   | 2007-03-25  | 9A    | 2022-01-20     | 654 Elm St, Citytown | +254772345684 |
| 18        | Rachel    | Green    | Female | 2006-01-10  | 10A   | 2021-01-15     | 321 Birch St, Citytown| +254782345685 |
| 19        | Samuel    | Harris   | Male   | 2005-12-24  | 11B   | 2020-02-10     | 987 Pine St, Citytown| +254792345686 |
| 20        | Tina      | Jackson  | Female | 2006-09-05  | 10B   | 2021-01-15     | 159 Maple St, Citytown| +254702345687 |
| 21        | Uma       | King     | Female | 2005-06-17  | 11A   | 2020-02-10     | 456 Cedar St, Citytown| +254712345688 |
| 22        | Victor    | Lewis    | Male   | 2006-05-10  | 10A   | 2021-01-15     | 741 Oak St, Citytown | +254722345689 |
| 23        | Wendy     | Martinez | Female | 2007-01-30  | 9B    | 2022-01-20     | 852 Pine St, Citytown| +254732345690 |
| 24        | Xavier    | Nelson   | Male   | 2005-10-25  | 11B   | 2020-02-10     | 963 Birch St, Citytown| +254742345691 |
| 25        | Yvonne    | Ortiz    | Female | 2006-03-21  | 10B   | 2021-01-15     | 234 Oak St, Citytown | +254752345692 |
| 26        | Zachary   | Price    | Male   | 2007-08-16  | 9A    | 2022-01-20     | 678 Maple St, Citytown| +254762345693 |
| 27        | Alice     | Robinson | Female | 2006-12-02  | 10A   | 2021-01-15     | 543 Cedar St, Citytown| +254772345694 |
| 28        | Ben       | Scott    | Male   | 2005-07-09  | 11A   | 2020-02-10     | 789 Elm St, Citytown | +254782345695 |
| 29        | Claire    | Taylor   | Female | 2006-04-13  | 10B   | 2021-01-15     | 321 Oak St, Citytown | +254792345696 |
| 30        | Derek     | Upton    | Male   | 2005-11-22  | 11B   | 2020-02-10     | 456 Pine St, Citytown| +254702345697 |
| 31        | Ella      | Vargas   | Female | 2006-06-30  | 10A   | 2021-01-15     | 987 Birch St, Citytown| +254712345698 |
| 32        | Frank     | Wallace  | Male   | 2007-02-14  | 9B    | 2022-01-20     | 852 Maple St, Citytown| +254722345699 |
| 33        | Grace     | Watson   | Female | 2005-10-03  | 11A   | 2020-02-10     | 741 Cedar St, Citytown| +254732345700 |
| 34        | Henry     | Young    | Male   | 2006-08-23  | 10B   | 2021-01-15     | 963 Oak St, Citytown | +254742345701 |
| 35        | Iris      | Adams    | Female | 2005-05-27  | 11B   | 2020-02-10     | 234 Maple St, Citytown| +254752345702 |
| 36        | Jack      | Bell     | Male   | 2006-03-14  | 10A   | 2021-01-15     | 678 Cedar St, Citytown| +254762345703 |
| 37        | Kim       | Cooper   | Female | 2007-11-08  | 9A    | 2022-01-20     | 543 Birch St, Citytown| +254772345704 |
| 38        | Liam      | Daniels  | Male   | 2005-06-05  | 11A   | 2020-02-10     | 852 Elm St, Citytown | +254782345705 |
| 39        | Mia       | Edwards  | Female | 2006-02-28  | 10B   | 2021-01-15     | 963 Pine St, Citytown| +254792345706 |
| 40        | Noah      | Foster   | Male   | 2005-12-15  | 11B   | 2020-02-10     | 789 Oak St, Citytown | +254702345707 |
| 41        | Olivia    | Gray     | Female | 2006-09-18  | 10A   | 2021-01-15     | 321 Maple St, Citytown| +254712345708 |
| 42        | Paul      | Harris   | Male   | 2007-04-07  | 9B    | 2022-01-20     | 654 Oak St, Citytown | +254722345709 |
| 43        | Quinn     | Jones    | Female | 2005-10-12  | 11A   | 2020-02-10     | 987 Cedar St, Citytown| +254732345710 |
| 44        | Ryan      | King     | Male   | 2006-05-02  | 10B   | 2021-01-15     | 543 Pine St, Citytown| +254742345711 |
| 45        | Sophia    | Lewis    | Female | 2005-07-19  | 11B   | 2020-02-10     | 852 Maple St, Citytown| +254752345712 |
| 46        | Tom       | Martin   | Male   | 2006-11-14  | 10A   | 2021-01-15     | 678 Birch St, Citytown| +254762345713 |
| 47        | Uma       | Nelson   | Female | 2007-06-20  | 9A    | 2022-01-20     | 789 Elm St, Citytown | +254772345714 |
| 48        | Victor    | Oliver   | Male   | 2005-03-11  | 11A   | 2020-02-10     | 963 Oak St, Citytown | +254782345715 |
| 49        | Wanda     | Parker   | Female | 2006-08-10  | 10B   | 2021-01-15     | 321 Cedar St, Citytown| +254792345716 |
| 50        | Xander    | Quinn    | Male   | 2005-12-05  | 11B   | 2020-02-10     | 654 Maple St, Citytown| +254702345717 |
| 51        | Yara      | Reed     | Female | 2006-01-15  | 10A   | 2021-01-15     | 987 Oak St, Citytown | +254712345718 |
| 52        | Zachary   | Scott    | Male   | 2007-07-12  | 9B    | 2022-01-20     | 852 Cedar St, Citytown| +254722345719 |
| 53        | Ava       | Turner   | Female | 2005-05-23  | 11A   | 2020-02-10     | 741 Maple St, Citytown| +254732345720 |
| 54        | Ben       | Underwood| Male   | 2006-03-08  | 10B   | 2021-01-15     | 963 Pine St, Citytown| +254742345721 |
| 55        | Clara     | Vega     | Female | 2005-11-17  | 11B   | 2020-02-10     | 234 Elm St, Citytown | +254752345722 |
| 56        | Derek     | Walker   | Male   | 2006-07-21  | 10A   | 2021-01-15     | 678 Pine St, Citytown| +254762345723 |
| 57        | Ella      | Xander   | Female | 2007-12-04  | 9A    | 2022-01-20     | 543 Maple St, Citytown| +254772345724 |
| 58        | Frank     | Young    | Male   | 2005-06-10  | 11A   | 2020-02-10     | 852 Birch St, Citytown| +254782345725 |
| 59        | Grace     | Zane     | Female | 2006-09-25  | 10B   | 2021-01-15     | 963 Cedar St, Citytown| +254792345726 |
| 60        | Henry     | Adams    | Male   | 2005-10-04  | 11B   | 2020-02-10     | 234 Pine St, Citytown| +254702345727 |
| 61        | Iris      | Barnes   | Female | 2006-07-05  | 10A   | 2021-01-15     | 678 Maple St, Citytown| +254712345728 |
| 62        | Jack      | Carter   | Male   | 2007-05-30  | 9B    | 2022-01-20     | 543 Oak St, Citytown | +254722345729 |
| 63        | Kim       | Dixon    | Female | 2005-12-14  | 11A   | 2020-02-10     | 852 Pine St, Citytown| +254732345730 |
| 64        | Liam      | Evans    | Male   | 2006-02-22  | 10B   | 2021-01-15     | 963 Birch St, Citytown| +254742345731 |
| 65        | Mia       | Fisher   | Female | 2005-08-13  | 11B   | 2020-02-10     | 234 Cedar St, Citytown| +254752345732 |
| 66        | Noah      | Gray     | Male   | 2006-06-11  | 10A   | 2021-01-15     | 678 Elm St, Citytown | +254762345733 |
| 67        | Olivia    | Hayes    | Female | 2007-04-17  | 9A    | 2022-01-20     | 543 Pine St, Citytown| +254772345734 |
| 68        | Paul      | Jordan   | Male   | 2005-09-29  | 11A   | 2020-02-10     | 852 Maple St, Citytown| +254782345735 |
| 69        | Quinn     | Kelly    | Female | 2006-01-22  | 10B   | 2021-01-15     | 963 Oak St, Citytown | +254792345736 |
| 70        | Ryan      | Lee      | Male   | 2005-07-23  | 11B   | 2020-02-10     | 234 Birch St, Citytown| +254702345737 |
| 71        | Sophia    | Martinez | Female | 2006-10-05  | 10A   | 2021-01-15     | 678 Cedar St, Citytown| +254712345738 |
| 72        | Tom       | Nguyen   | Male   | 2007-03-10  | 9B    | 2022-01-20     | 543 Oak St, Citytown | +254722345739 |
| 73        | Uma       | Owens    | Female | 2005-11-21  | 11A   | 2020-02-10     | 852 Elm St, Citytown | +254732345740 |
| 74        | Victor    | Patel    | Male   | 2006-12-14  | 10B   | 2021-01-15     | 963 Pine St, Citytown| +254742345741 |
| 75        | Wanda     | Quinn    | Female | 2005-04-06  | 11B   | 2020-02-10     | 234 Maple St, Citytown| +254752345742 |
| 76        | Xavier    | Rivera   | Male   | 2006-08-09  | 10A   | 2021-01-15     | 678 Birch St, Citytown| +254762345743 |
| 77        | Yara      | Sanders  | Female | 2007-10-23  | 9A    | 2022-01-20     | 543 Maple St, Citytown| +254772345744 |
| 78        | Zachary   | Taylor   | Male   | 2005-07-04  | 11A   | 2020-02-10     | 852 Cedar St, Citytown| +254782345745 |
| 79        | Alice     | Upton    | Female | 2006-05-21  | 10B   | 2021-01-15     | 963 Elm St, Citytown | +254792345746 |
| 80        | Ben       | Vega     | Male   | 2005-03-17  | 11B   | 2020-02-10     | 678 Maple St, Citytown| +254702345747 |
| 81        | Clara     | Walker   | Female | 2006-11-08  | 10A   | 2021-01-15     | 543 Cedar St, Citytown| +254712345748 |
| 82        | Derek     | Xander   | Male   | 2007-04-16  | 9B    | 2022-01-20     | 852 Pine St, Citytown| +254722345749 |
| 83        | Ella      | Young    | Female | 2005-02-11  | 11A   | 2020-02-10     | 963 Oak St, Citytown | +254732345750 |
| 84        | Frank     | Zane     | Male   | 2006-10-20  | 10B   | 2021-01-15     | 234 Birch St, Citytown| +254742345751 |
| 85        | Grace     | Adams    | Female | 2005-09-05  | 11B   | 2020-02-10     | 678 Cedar St, Citytown| +254752345752 |
| 86        | Henry     | Barnes   | Male   | 2006-01-12  | 10A   | 2021-01-15     | 543 Maple St, Citytown| +254762345753 |
| 87        | Iris      | Cooper   | Female | 2007-06-21  | 9A    | 2022-01-20     | 852 Oak St, Citytown | +254772345754 |
| 88        | Jack      | Daniels  | Male   | 2005-11-29  | 11A   | 2020-02-10     | 963 Pine St, Citytown| +254782345755 |
| 89        | Kim       | Edwards  | Female | 2006-02-17  | 10B   | 2021-01-15     | 234 Maple St, Citytown| +254792345756 |
| 90        | Liam      | Fisher   | Male   | 2005-08-04  | 11B   | 2020-02-10     | 678 Birch St, Citytown| +254702345757 |
| 91        | Mia       | Green    | Female | 2006-12-01  | 10A   | 2021-01-15     | 543 Oak St, Citytown | +254712345758 |
| 92        | Noah      | Harris   | Male   | 2007-07-30  | 9B    | 2022-01-20     | 852 Cedar St, Citytown| +254722345759 |
| 93        | Olivia    | Johnson  | Female | 2005-05-14  | 11A   | 2020-02-10     | 963 Maple St, Citytown| +254732345760 |
| 94        | Paul      | King     | Male   | 2006-08-08  | 10B   | 2021-01-15     | 234 Elm St, Citytown | +254742345761 |
| 95        | Quinn     | Lewis    | Female | 2005-03-18  | 11B   | 2020-02-10     | 678 Pine St, Citytown| +254752345762 |
| 96        | Ryan      | Martinez | Male   | 2006-10-27  | 10A   | 2021-01-15     | 543 Maple St, Citytown| +254762345763 |
| 97        | Sophia    | Nelson   | Female | 2005-06-12  | 11A   | 2020-02-10     | 852 Cedar St, Citytown| +254772345764 |
| 98        | Tom       | Oliver   | Male   | 2006-11-20  | 10B   | 2021-01-15     | 963 Oak St, Citytown | +254782345765 |
| 99        | Uma       | Price    | Female | 2007-04-30  | 9A    | 2022-01-20     | 234 Pine St, Citytown| +254792345766 |
| 100       | Victor    | Quinn    | Male   | 2005-12-01  | 11A   | 2020-02-10     | 678 Maple St, Citytown| +254702345767 |
| 101       | Wanda     | Reed     | Female | 2006-02-05  | 10A   | 2021-01-15     | 543 Cedar St, Citytown| +254712345768 |
| 102       | Xavier    | Scott    | Male   | 2007-03-28  | 9B    | 2022-01-20     | 852 Oak St, Citytown | +254722345769 |
| 103       | Yara      | Taylor   | Female | 2005-11-12  | 11A   | 2020-02-10     | 963 Birch St, Citytown| +254732345770 |
| 104       | Zachary   | Upton    | Male   | 2006-09-09  | 10B   | 2021-01-15     | 234 Maple St, Citytown| +254742345771 |
| 105       | Alice     | Vega     | Female | 2005-01-16  | 11B   | 2020-02-10     | 678 Oak St, Citytown | +254752345772 |
| 106       | Ben       | Walker   | Male   | 2006-06-25  | 10A   | 2021-01-15     | 543 Pine St, Citytown| +254762345773 |
| 107       | Clara     | Xander   | Female | 2007-08-17  | 9A    | 2022-01-20     | 852 Maple St, Citytown| +254772345774 |
| 108       | Derek     | Young    | Male   | 2005-02-28  | 11A   | 2020-02-10     | 963 Cedar St, Citytown| +254782345775 |
| 109       | Ella      | Zane     | Female | 2006-07-19  | 10B   | 2021-01-15     | 234 Birch St, Citytown| +254792345776 |
| 110       | Frank     | Adams    | Male   | 2005-10-08  | 11B   | 2020-02-10     | 678 Maple St, Citytown| +254702345777 |
| 111       | Grace     | Barnes   | Female | 2006-01-22  | 10A   | 2021-01-15     | 543 Cedar St, Citytown| +254712345778 |
| 112       | Henry     | Cooper   | Male   | 2007-04-01  | 9B    | 2022-01-20     | 852 Oak St, Citytown | +254722345779 |
| 113       | Iris      | Daniels  | Female | 2005-12-18  | 11A   | 2020-02-10     | 963 Pine St, Citytown| +254732345780 |
| 114       | Jack      | Edwards  | Male   | 2006-07-10  | 10B   | 2021-01-15     | 234 Maple St, Citytown| +254742345781 |
| 115       | Kim       | Fisher   | Female | 2005-11-25  | 11B   | 2020-02-10     | 678 Cedar St, Citytown| +254752345782 |
| 116       | Liam      | Green    | Male   | 2006-04-07  | 10A   | 2021-01-15     | 543 Oak St, Citytown | +254762345783 |
| 117       | Mia       | Harris   | Female | 2007-03-29  | 9A    | 2022-01-20     | 852 Birch St, Citytown| +254772345784 |
| 118       | Noah      | Johnson  | Male   | 2005-08-15  | 11A   | 2020-02-10     | 963 Cedar St, Citytown| +254782345785 |
| 119       | Olivia    | King     | Female | 2006-12-06  | 10B   | 2021-01-15     | 234 Pine St, Citytown| +254792345786 |
| 120       | Paul      | Lewis    | Male   | 2005-05-11  | 11B   | 2020-02-10     | 678 Maple St, Citytown| +254702345787 |

Would you like to generate any specific insights from this data, or is there anything else you'd like to do with it?
