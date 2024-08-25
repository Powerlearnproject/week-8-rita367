# Solving an SDG Problem with Data (Choose Your SDG)

## Overview
Select a Sustainable Development Goal (SDG) that resonates with you and develop a data-driven solution to address a specific problem within that SDG. Design a database, perform data analysis, and use Microsoft Excel as the user interface.

## Objectives
- Choose an SDG and identify a specific problem to address.
- Design and implement a relational database relevant to your chosen problem.
- Write SQL queries to retrieve and analyze data.
- Use Microsoft Excel for data visualization and analysis.

## Requirements

### Part 1: SDG Selection and Problem Definition
- **SDG Selection:** Choose an SDG (e.g., SDG 3: Good Health, SDG 7: Affordable and Clean Energy).
- **Problem Definition:** Define a specific problem within your chosen SDG that can be addressed using data.

Part 1: SDG Selection and Problem Definition
SDG Selection:

SDG 3: Good Health and Well-being
Problem Definition:

Problem: High rates of maternal and infant mortality in a specific region.
Data Usage: To address this problem, you can use data related to maternal health services, delivery outcomes, and patient demographics to identify trends, gaps, and areas needing intervention.
Part 2: Database Design
ERD: Design an Entity-Relationship Diagram (ERD) including entities relevant to the problem. For example:

Entities:

Patients: PatientID, Name, Age, Gender, Address
Pregnancies: PregnancyID, PatientID, StartDate, DueDate, Outcome
Deliveries: DeliveryID, PregnancyID, DeliveryDate, Outcome (e.g., live birth, stillbirth)
HealthcareProviders: ProviderID, Name, Specialty
Visits: VisitID, PatientID, ProviderID, VisitDate, TypeOfCare
Relationships:

A Patient can have multiple Pregnancies.
A Pregnancy can have multiple Deliveries.
Patients and HealthcareProviders are linked through Visits
### Part 2: Database Design
- **ERD:** Design an ERD for your project, including entities relevant to your SDG problem.
- **Schema:** Write SQL statements to create the database schema based on your ERD.
- CREATE TABLE Patients (
    PatientID INT PRIMARY KEY,
    Name VARCHAR(100),
    Age INT,
    Gender CHAR(1),
    Address VARCHAR(255)
);

CREATE TABLE Pregnancies (
    PregnancyID INT PRIMARY KEY,
    PatientID INT,
    StartDate DATE,
    DueDate DATE,
    Outcome VARCHAR(50),
    FOREIGN KEY (PatientID) REFERENCES Patients(PatientID)
);

CREATE TABLE Deliveries (
    DeliveryID INT PRIMARY KEY,
    PregnancyID INT,
    DeliveryDate DATE,
    Outcome VARCHAR(50),
    FOREIGN KEY (PregnancyID) REFERENCES Pregnancies(PregnancyID)
);

CREATE TABLE HealthcareProviders (
    ProviderID INT PRIMARY KEY,
    Name VARCHAR(100),
    Specialty VARCHAR(100)
);

CREATE TABLE Visits (
    VisitID INT PRIMARY KEY,
    PatientID INT,
    ProviderID INT,
    VisitDate DATE,
    TypeOfCare VARCHAR(50),
    FOREIGN KEY (PatientID) REFERENCES Patients(PatientID),
    FOREIGN KEY (ProviderID) REFERENCES HealthcareProviders(ProviderID)
);

- **Sample Data:** Populate the database with relevant sample data.
- 
INSERT INTO Patients (PatientID, Name, Age, Gender, Address) VALUES
(1, 'Jane Doe', 28, 'F', '123 Elm St'),
(2, 'Mary Smith', 32, 'F', '456 Oak St');

INSERT INTO Pregnancies (PregnancyID, PatientID, StartDate, DueDate, Outcome) VALUES
(1, 1, '2024-01-10', '2024-10-10', 'Live Birth'),
(2, 2, '2024-03-15', '2024-12-15', 'Stillbirth');

INSERT INTO Deliveries (DeliveryID, PregnancyID, DeliveryDate, Outcome) VALUES
(1, 1, '2024-10-10', 'Live Birth'),
(2, 2, '2024-12-15', 'Stillbirth');

INSERT INTO HealthcareProviders (ProviderID, Name, Specialty) VALUES
(1, 'Dr. Alice Johnson', 'Obstetrics'),
(2, 'Dr. Bob Brown', 'Pediatrics');

INSERT INTO Visits (VisitID, PatientID, ProviderID, VisitDate, TypeOfCare) VALUES
(1, 1, 1, '2024-09-01', 'Routine Checkup'),
(2, 2, 1, '2024-11-01', 'Consultation');

### Part 3: SQL Programming
- **Data Retrieval:** Write SQL queries to retrieve relevant data based on your problem definition.
- -- Retrieve all deliveries with their outcomes
SELECT * FROM Deliveries;

-- Get all visits for a specific patient
SELECT * FROM Visits WHERE PatientID = 1;

- **Data Analysis:** Write SQL queries to analyze data and generate insights related to your SDG problem.
-- Count the number of live births and stillbirths
SELECT Outcome, COUNT(*) AS Count
FROM Deliveries
GROUP BY Outcome;

-- Average age of patients by delivery outcome
SELECT d.Outcome, AVG(p.Age) AS AverageAge
FROM Deliveries d
JOIN Pregnancies preg ON d.PregnancyID = preg.PregnancyID
JOIN Patients p ON preg.PatientID = p.PatientID
GROUP BY d.Outcome;

### Part 4: Data Analysis Using Excel
- **Import Data:** Import data from your database into Excel.
- **Analysis:** Analyze the data using pivot tables, charts, and other Excel tools.
- **Dashboard:** Create an interactive Excel dashboard to visualize key insights.
The current infant mortality rate for Kenya in 2024 is 29.720 deaths per 1000 live births, a 2.97% decline from 2023.
The infant mortality rate for Kenya in 2023 was 30.629 deaths per 1000 live births, a 3.59% decline from 2022.
The infant mortality rate for Kenya in 2022 was 31.771 deaths per 1000 live births, a 3.47% decline from 2021.
The infant mortality rate for Kenya in 2021 was 32.913 deaths per 1000 live births, a 3.36% decline from 2020.
### Part 5: Integration and Testing
- **Integration:** Document the process of importing data into Excel and ensuring consistency.
- **Testing:** Test the integration and functionality of your Excel dashboard.

### Part 6: Presentation
- **Pitch Deck:** Develop a 10-slide PowerPoint presentation as taught in the entrepreneurship module covering:
  - Project overview and SDG alignment.
  - Problem definition and significance.
  - Database design and schema.
  - Data analysis insights.
  - Excel dashboard demonstration.
- **Delivery:** Present your pitch deck, demonstrating how your project addresses the SDG problem.
lide 1: Title Slide
Title: Addressing Maternal and Infant Mortality: A Data-Driven Approach
Subtitle: Alignment with SDG 3 - Good Health and Well-being
Your Name
Date
Slide 2: Project Overview and SDG Alignment
SDG 3 Overview: Brief introduction to Sustainable Development Goal 3 (Good Health and Well-being).
Selected Problem: Focus on maternal and infant mortality rates.
Relevance: Explain how addressing this issue aligns with SDG 3.
Slide 3: Problem Definition and Significance
Problem Statement: Define the specific issue of maternal and infant mortality.
Significance: Highlight the impact on health and well-being.
Contextual Data: Provide statistics or real-world examples to illustrate the problem's magnitude.
Slide 4: Database Design and Schema
ERD Overview: Present the Entity-Relationship Diagram (ERD) showing key entities (Patients, Pregnancies, Deliveries, HealthcareProviders, Visits).
Schema Details: Briefly describe the tables and their relationships.
Purpose: Explain how the database design helps in addressing the problem.
Slide 5: Data Retrieval and Analysis
Key SQL Queries: Include examples of SQL queries used to retrieve and analyze data.
Insights: Summarize key findings from the queries, such as delivery outcomes and average patient age.
Visualization: Include any relevant data snapshots or charts from the SQL analysis.
Slide 6: Excel Data Import and Analysis
Import Process: Describe how data was imported from the database into Excel.
Analysis Tools: Mention the tools and techniques used for analysis (pivot tables, charts).
Findings: Present any initial insights from the Excel analysis.
Slide 7: Excel Dashboard Demonstration
Dashboard Overview: Provide screenshots or visuals of the interactive Excel dashboard.
Key Visuals: Highlight key charts, graphs, and pivot tables.
Insights: Explain how the dashboard helps in understanding and addressing the problem.
Slide 8: Conclusion and Recommendations
Summary of Findings: Recap the main insights and conclusions from the data analysis.
Recommendations: Suggest actions or interventions based on the findings.
Impact: Discuss potential improvements in maternal and infant health.
Slide 9: Next Steps
Further Analysis: Outline any additional analyses or research needed.
Implementation: Discuss potential steps for implementing recommendations.
Monitoring: Suggest how progress can be monitored and evaluated.
Slide 10: Q&A and Contact Information
Questions: Invite questions from the audience.
Contact Information: Provide your email or other contact details for follow-up.
## Deliverables (upload onto this repo)
- SDG problem definition document
- ERD
- SQL scripts
- Excel workbook with data analysis and dashboard
- Integration documentation
- Pitch deck presentation (Provide the link e.g Canva or Gamma in your documentation)
https://gamma.app/docs/Managing-Your-Spending-Insights-Tips-for-Better-Financial-Control-y755x5pon0fn7hr
