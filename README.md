# ER Dashboard

Dashboard Link - https://app.powerbi.com/links/o-mMGVNA5G?ctid=67cbf827-915c-4f92-841f-f4a5f971fda0&pbi_source=linkShare

Hospital Emergency Room Dashboard — Power BI Project
This interactive Power BI dashboard provides deep insights into the operations and performance of a hospital's Emergency Room (ER). It was designed to help healthcare stakeholders monitor patient volume, admission trends, satisfaction levels, wait times, and resource allocation efficiently.

### Project Overview
Domain: Healthcare

Type: End-to-End Power BI Reporting Solution

Pages:

Monthly View

Consolidated View

Patient Details

### Business Objectives:

Track the number of ER patients across different time periods

Analyze patient satisfaction scores and average wait times

Understand patient flow by gender, age, department, and admission status

Identify patient spikes by hour/day for staffing optimization

Measure timely service delivery (seen within 30 mins)

### Key KPIs: 

KPI	Description
No. of Patients	Total ER visits over time

Avg. Wait Time	Average patient wait duration

Satisfaction Score	Patient-reported satisfaction (1 to 5)

% Seen in 30 Mins	Operational efficiency metric

Patient Referrals	Referrals to departments from ER

### Pages Breakdown

1. Monthly View
Dynamic by Year and Month filters

Line graphs for daily:

Patient count

Wait times

Satisfaction scores

Department referrals, patient age/gender, hourly heat map

 2. Consolidated View
Full date-range analysis

KPIs shown as Cards

Stacked bar & donut charts for:

Age group distribution

Admission status

Gender breakdown

Time-based patient handling


3. Patient Details
Tabular view with:

Patient ID, Name, Gender, Age

Admission Status, Referral Dept.

Wait Time, Admission Date

### Sample DAX Measures

DAX
Copy
Edit
No of Patients = COUNTROWS('Hospital ER_Data')

Patient satisfaction score = AVERAGE('Hospital ER_Data'[Patient Satisfaction Score])

No. of patients Referred = CALCULATE(COUNTROWS('Hospital ER_Data'), 'Hospital ER_Data'[Department Referral] <> "None")

Patients Add Date = DATE
                (YEAR('Hospital ER_Data'[Patient Admission Date]), 
                      MONTH('Hospital ER_Data'[Patient Admission Date]),
                          DAY('Hospital ER_Data'[Patient Admission Date]))

Waittime Interval = 
SWITCH(
    TRUE(),
    'Hospital ER_Data'[Addmission Hour]< 2, "00-02",
    'Hospital ER_Data'[Addmission Hour] < 4, "03-04",
    'Hospital ER_Data'[Addmission Hour] < 6, "05-06",
    'Hospital ER_Data'[Addmission Hour] < 8, "07-08",
    'Hospital ER_Data'[Addmission Hour] < 10, "09-10",
    'Hospital ER_Data'[Addmission Hour] < 12, "11-12",
    'Hospital ER_Data'[Addmission Hour] < 14, "13-14",
    'Hospital ER_Data'[Addmission Hour] < 16, "15-16",
    'Hospital ER_Data'[Addmission Hour] < 18, "17-18",
    'Hospital ER_Data'[Addmission Hour] < 20, "19-20",
    'Hospital ER_Data'[Addmission Hour] < 22, "21-22",
    'Hospital ER_Data'[Addmission Hour]< 24, "23-24",
    "Above 24"
)


### Insights Delivered
Over 9,000 ER visits analyzed

50% of patients admitted; balanced inflow

Majority of patients seen within 30 minutes (~59%)

Peak ER load between 10 AM – 4 PM

Age group 20–49 makes up largest ER visits

Weekends show slight spike in visits

 ### Data Model Highlights
Tables:

Hospital ER_Data — Core patient dataset

Calendar Table — For flexible date slicers

DAX_Table — Calculated measures

Slicers & Filters:

Date range

Month & Year

Age Group, Gender, Referral Dept.



### Outcome
This dashboard can be presented to hospital management to:

Monitor and optimize ER staffing

Improve service delivery time

Highlight areas to enhance patient satisfaction

Allocate departmental resources based on referrals.

