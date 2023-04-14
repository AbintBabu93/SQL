# SQL

# Collect necessary data from the table

SELECT emp_no, gender, age, department, education, job_role, business_travel, job_satisfaction
FROM hrdata; 

# Find total numbers of Males and Females in the compnay

SELECT gender, COUNT(gender) as total_gender_count
FROM hrdata
GROUP BY gender; 


# Find total number of Gender In Each Positions


SELECT  job_role, gender, count(gender) as Gender_in_Eachposition
FROM hrdata
GROUP BY job_role, gender
ORDER BY job_role; 


# Find total number of Gender In Each departments

SELECT department,  gender, COUNT(gender) as total_number
FROM hrdata
GROUP BY department, gender
ORDER BY department; 


# Improvement 


SELECT job_role, job_satisfaction, count(job_role),
CASE
    WHEN job_satisfaction = 4 THEN 'Must attending 3 weeks training'
    WHEN job_satisfaction = 3 THEN 'Work together with Team lead for 2 weeks'
    WHEN job_satisfaction = 2 THEN 'Improving your own skills'
    ELSE 'Keep going'
END as Improvement_status
FROM hrdata
GROUP BY job_role, job_satisfaction
ORDER BY job_satisfaction; 


# Find number of employees Business Travel based on the gender


SELECT business_travel, gender, COUNT(business_travel) as business_Travel_count
FROM hrdata
GROUP BY business_travel, gender
ORDER BY business_travel desc; 


# Employees Educations


SELECT education, COUNT(education) as employee_education
FROM hrdata
GROUP BY education
ORDER BY education; 

# Find age between 18 and 28

SELECT age, COUNT(age)
FROM hrdata
WHERE age between 18 and 28
GROUP BY age;


# Classification of employees based on their age


SELECT age, gender, COUNT(gender) Gender_count,
CASE
    WHEN age BETWEEN 18 and 28 THEN 'Young Employees'
    WHEN age BETWEEN 29 and 48 THEN 'Middle age employees'
    WHEN age BETWEEN 49 and 60 THEN 'Old employees'
    ELSE 'EX_Employees'
END as Employees_Type
FROM hrdata
GROUP BY age, gender
ORDER BY age;
