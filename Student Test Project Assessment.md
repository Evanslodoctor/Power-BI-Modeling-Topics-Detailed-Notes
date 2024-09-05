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
