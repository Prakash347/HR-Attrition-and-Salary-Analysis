# HR-Attrition-and-Salary-Analysis
Analyzing employee attrition trends, salary distribution, and performance correlations using SQL
📜 Project Overview
Employee attrition is a critical challenge for organizations. This project explores the relationship between hiring, attrition, salaries, and performance using SQL-based analysis.

🎯 Project Objectives:
Identify hiring and attrition trends from 2015 to 2025.
Analyze salary distribution across departments and job levels.
Examine attrition based on performance, gender, region, and promotions.
Provide actionable insights for HR to improve retention and salary structures.
🔍 Key Insights & Findings

Here’s what the analysis revealed:

📊 1. Hiring Trends (2015–2025):
Peak Hiring: 2023 had the highest hires (120), followed by 2022 (114) and 2018 (113).
Recent Decline: Hiring dropped to 80 in 2024, with only 11 hires in 2025 so far.
SQL Query:


SELECT YEAR(HireDate) AS Hire_Year, COUNT(*) AS Total_Hires
FROM Employees
GROUP BY YEAR(HireDate)
ORDER BY Hire_Year;
Solution:

Conduct targeted recruitment campaigns.
Focus on departments with high attrition.
Impact: Sustained workforce and reduced skill gaps.
🟠 2. Hiring by Department (2015–2025):
Highest Hires: IT and Sales consistently led in hiring.
Stable Hiring: Finance and HR maintained steady recruitment, while Operations and Marketing fluctuated.
SQL Query:

SELECT Department, COUNT(*) AS Total_Hires
FROM Employees
WHERE YEAR(HireDate) BETWEEN 2015 AND 2025
GROUP BY Department
ORDER BY Total_Hires DESC;
Solution:

Prioritize hiring in departments facing attrition.
Conduct skill-based recruitment.
Impact: Balanced workforce across all departments.
🔵 3. Hiring by Job Level (2015–2025):
Top Hires: Job Level 3 had the highest hires, followed by Levels 1, 2, 4, and 5.
Low Hiring: Senior positions had minimal hires.
SQL Query:


SELECT JobLevel, COUNT(*) AS Total_Hires
FROM Employees
WHERE YEAR(HireDate) BETWEEN 2015 AND 2025
GROUP BY JobLevel
ORDER BY Total_Hires DESC;
Solution:
Increase hiring at senior levels.
Promote internally for leadership roles.
Impact: Strong leadership pipeline.

⚫ 4. Attrition by Job Level:
High Attrition: Level 3 (5.14%), Level 4 (4.39%), Level 5 (4.19%).
Low Attrition: Senior roles had 0%, while entry-level (Level 1) had 3.13%.
SQL Query:
SELECT JobLevel, COUNT(*) AS Total_Employees,
SUM(CASE WHEN Attrition = 'Yes' THEN 1 ELSE 0 END) AS Attrition_Count,
ROUND((SUM(CASE WHEN Attrition = 'Yes' THEN 1 ELSE 0 END) * 100.0 / COUNT(*)), 2) AS Attrition_Rate
FROM Employees
GROUP BY JobLevel
ORDER BY Attrition_Rate DESC;
Solution:
Improve retention strategies for mid-level employees.
Offer leadership training and mentorship.

Impact: Reduced turnover and stable workforce.
🟣 5. Attrition by Department:
High Attrition: Sales (6.21%), Marketing (5.20%), HR (4.76%).
Low Attrition: Operations (1.72%).
SQL Query:
SELECT Department, COUNT(*) AS Total_Employees,
SUM(CASE WHEN Attrition = 'Yes' THEN 1 ELSE 0 END) AS Attrition_Count,
ROUND((SUM(CASE WHEN Attrition = 'Yes' THEN 1 ELSE 0 END) * 100.0 / COUNT(*)), 2) AS Attrition_Rate
FROM Employees
GROUP BY Department
ORDER BY Attrition_Rate DESC;
Solution:
Enhance work culture in high-attrition departments.
Conduct exit interviews for root-cause analysis.
Impact: Improved job satisfaction and retention.

🟡 6. Attrition by Age Group:
High Attrition: Employees aged 25–34 had the highest attrition.
SQL Query:
SELECT AgeGroup, COUNT(*) AS Total_Employees,
SUM(CASE WHEN Attrition = 'Yes' THEN 1 ELSE 0 END) AS Attrition_Count,
ROUND((SUM(CASE WHEN Attrition = 'Yes' THEN 1 ELSE 0 END) * 100.0 / COUNT(*)), 2) AS Attrition_Rate
FROM Employees
GROUP BY AgeGroup
ORDER BY Attrition_Rate DESC;
Solution:
Introduce career development programs.
Offer flexible work policies.
Impact: Increased retention among young talent.

🔶 7. Performance vs. Attrition:
High Attrition: Low performers had higher attrition.
SQL Query:
SELECT Performance_Rating, COUNT(*) AS Total_Employees,
SUM(CASE WHEN Attrition = 'Yes' THEN 1 ELSE 0 END) AS Attrition_Count,
ROUND((SUM(CASE WHEN Attrition = 'Yes' THEN 1 ELSE 0 END) * 100.0 / COUNT(*)), 2) AS Attrition_Rate
FROM Employees
GROUP BY Performance_Rating
ORDER BY Attrition_Rate DESC;
Solution:
Upskill low performers.
Recognize and reward high performers.
Impact: Improved job satisfaction and retention.

💰 8. Salary vs. Attrition:
High Attrition: Employees with lower salaries had higher attrition.
SQL Query:
SELECT SalaryRange, COUNT(*) AS Total_Employees,
SUM(CASE WHEN Attrition = 'Yes' THEN 1 ELSE 0 END) AS Attrition_Count,
ROUND((SUM(CASE WHEN Attrition = 'Yes' THEN 1 ELSE 0 END) * 100.0 / COUNT(*)), 2) AS Attrition_Rate
FROM Employees
GROUP BY SalaryRange
ORDER BY Attrition_Rate DESC;
Solution:
Conduct salary benchmarking.
Ensure competitive compensation.
Impact: Increased job satisfaction and retention.

👥 9. Gender-wise Attrition:
Findings: Male employees had slightly higher attrition.
SQL Query:
SELECT Gender, COUNT(*) AS Total_Employees,
SUM(CASE WHEN Attrition = 'Yes' THEN 1 ELSE 0 END) AS Attrition_Count,
ROUND((SUM(CASE WHEN Attrition = 'Yes' THEN 1 ELSE 0 END) * 100.0 / COUNT(*)), 2) AS Attrition_Rate
FROM Employees
GROUP BY Gender;
Solution:
Ensure gender equity in workplace policies.
Impact: Improved gender diversity.

🕰️ 10. New Hires vs. Tenured Employees:
Finding: New hires had higher attrition.
SQL Query:
SELECT TenureGroup, COUNT(*) AS Total_Employees,
SUM(CASE WHEN Attrition = 'Yes' THEN 1 ELSE 0 END) AS Attrition_Count,
ROUND((SUM(CASE WHEN Attrition = 'Yes' THEN 1 ELSE 0 END) * 100.0 / COUNT(*)), 2) AS Attrition_Rate
FROM Employees
GROUP BY TenureGroup;
Solution:
Strengthen onboarding programs.
Conduct regular check-ins.
Impact: Improved retention among new hires.

🌍 11. Region-wise Attrition:
Finding: Region C faced the highest attrition.
SQL Query:
SELECT Region, COUNT(*) AS Total_Employees,
SUM(CASE WHEN Attrition = 'Yes' THEN 1 ELSE 0 END) AS Attrition_Count,
ROUND((SUM(CASE WHEN Attrition = 'Yes' THEN 1 ELSE 0 END) * 100.0 / COUNT(*)), 2) AS Attrition_Rate
FROM Employees
GROUP BY Region
ORDER BY Attrition_Rate DESC;
Solution:
Improve work conditions in high-attrition regions.
Impact: Balanced attrition across regions.

📈 12. Promotions vs. Attrition:
Finding: Lack of promotions led to higher attrition.
SQL Query:

SELECT Promotion_Status, COUNT(*) AS Total_Employees,
SUM(CASE WHEN Attrition = 'Yes' THEN 1 ELSE 0 END) AS Attrition_Count,
ROUND((SUM(CASE WHEN Attrition = 'Yes' THEN 1 ELSE 0 END) * 100.0 / COUNT(*)), 2) AS Attrition_Rate
FROM Employees
GROUP BY Promotion_Status;
Solution:
Create clear promotion pathways.
Impact: Increased retention and morale.

💻 13. High Salary Analysis in IT:
Finding: 20% of IT employees earned high salaries.
SQL Query:
SELECT EmployeeID, JobTitle, Department, Salary
FROM Employees
WHERE Department = 'IT' AND Salary > 90000;
Solution:
Benchmark IT salaries with industry standards.
Impact: Fair compensation and retention.

💸 14. Department-wise Salary Comparison:
Finding: IT and Sales had higher average salaries.
SQL Query:
SELECT Department, ROUND(AVG(Salary), 2) AS Avg_Salary
FROM Employees
GROUP BY Department
ORDER BY Avg_Salary DESC;
Solution:
Standardize salaries across departments.
Impact: Increased employee satisfaction.

🏆 15. Performance Rating vs. High Salary:
Finding: Top performers were more likely to earn high salaries.
SQL Query:
SELECT Performance_Rating, ROUND(AVG(Salary), 2) AS Avg_Salary
FROM Employees
GROUP BY Performance_Rating
ORDER BY Performance_Rating DESC;
Solution:

Align salary increments with performance.
Impact: Increased motivation and retention.

⚙️ Technologies Used
SQL: Data querying and analysis
Excel: Data cleaning and preprocessing

🤝 Contributing
Pull requests are welcome! For significant changes, please open an issue first to discuss what you'd like to change.

