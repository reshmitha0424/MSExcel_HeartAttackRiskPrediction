# 🩺 Heart Attack Prediction Dashboard – Excel Project Summary

## ✅ 1. Column Name Cleaning

Renamed long column names to shorter, readable labels:

| Original Column                        | Renamed To             |
|----------------------------------------|-------------------------|
| Blood Pressure                         | BP                      |
| Alcohol Consumption                    | Alcohol                 |
| Exercise Hours Per Week                | ExerciseHrsInWeek       |
| Previous Heart Problems                | PrevHeartIssue          |
| Medication Use                         | Medication              |
| Stress Level                           | Stress                  |
| Sedentary Hours Per Day                | SedentaryHrsInDay       |
| Physical Activity Days Per Week        | ActiveDaysInWeek        |
| Sleep Hours Per Day                    | SleepHrsInDay           |
| Heart Attack Risk                      | Risk                    |

---

## ✅ 2. Hemisphere Column Cleanup

- Replaced values in **Hemisphere** column:
  - `"Southern Hemisphere"` → `"SH"`
  - `"Northern Hemisphere"` → `"NH"`
- Used **Find and Replace (Ctrl + H)**

---

## ✅ 3. Checked for Merged Cells

- Selected entire sheet
- Verified “Merge & Center” was **not highlighted**
- No merged cells found

---

## ✅ 4. Checked for Blank Rows/Columns

- **Manually scrolled** through the sheet
- No fully blank rows/columns found

---

## ✅ 5. Validated Data Types

| Column Name              | Data Type     |
|--------------------------|---------------|
| Patient ID               | General       |
| Age                      | Number        |
| Sex                      | Text          |
| Cholesterol              | Number        |
| BP                       | General       |
| Heart Rate               | Number        |
| Diabetes                 | Number        |
| Family History           | Number        |
| Smoking                  | Number        |
| Obesity                  | Number        |
| Alcohol                  | Number        |
| ExerciseHrsInWeek        | Number (1 dec)|
| Diet                     | Text          |
| PrevHeartIssue           | Number        |
| Medication               | Number        |
| Stress                   | Number        |
| SedentaryHrsInDay        | Number (1 dec)|
| Income                   | Currency      |
| BMI                      | Number (2 dec)|
| Triglycerides            | Number (2 dec)|
| ActiveDaysInWeek         | Number        |
| SleepHrsInDay            | Number (1 dec)|
| Country / Continent / Hemisphere | Text  |
| Risk                     | Number        |

---

## ✅ 6. Added Helper Columns

Converted raw numeric/binary data into user-friendly labels for analysis and dashboarding.

| Column Name              | Description |
|--------------------------|-------------|
| **Systolic BP**          | `=VALUE(LEFT(E2, FIND("/", E2) - 1))` – Extracts systolic part from BP |
| **Age Group**            | `=IF(B2<30,"Under 30",IF(B2<=49,"30-49",IF(B2<=69,"50-69","70+")))` |
| **Risk Category**        | `=IF(AB2=1, "High", "Low")` |
| **BMI Category**         | `=IF(U2<18.5,"UnderWeight", IF(U2<25,"Normal", IF(U2<30, "Overweight", "Obese")))` |
| **Sleep Quality**        | `=IF(Y2<6, "Poor", IF(Y2<=8, "Average", "Good"))` |
| **Activity Level**       | `=IF(X2=0,"Inactive", IF(X2<3,"Low", IF(X2<6,"Moderate", "High")))` |
| **Stress Category**      | `=IF(R2<4,"Low",IF(R2<7,"Moderate","High"))` |
| **Cholesterol Category** | `=IF(E2<200,"Desirable", IF(E2<240,"Borderline", "High"))` |
| **Heart Rate Category**  | `=IF(I2<60, "Below Normal", IF(I2<=100, "Normal", "Above Normal"))` |
| **Triglycerides Category** | `=IF(Z2<150, "Normal", IF(Z2<200, "Borderline", IF(Z2<500, "High", "Very High")))` |
| **Alcohol Status**       | `=IF(O2=1, "Yes", "No")` |
| **Smoking Status**       | `=IF(M2=1, "Yes", "No")` |
| **Diabetes Status**      | `=IF(K2=1, "Yes", "No")` |
| **Obesity Status**       | `=IF(P2=1, "Yes", "No")` |
| **PrevHeartIssue Status**| `=IF(V2=1, "Yes", "No")` |
| **Medication Status**    | `=IF(X2=1, "Yes", "No")` |
| **Family History Status**| `=IF(M2=1, "Yes", "No")` |

**Note:** Helper columns were added for easier filtering, visualization, and user comprehension in pivot tables and dashboards.

---

## ✅ 7. Pivot Table: Heart Attack Risk by Age Group

### a. Created PivotTable
- **Rows**: Age Group
- **Columns**: Risk Category (High/Low)
- **Values**: Count of Patient ID

### b. Added % of Patients
- Used “Show Values As → % of Row Total”

### c. Renamed Labels
- Row Labels → `Age Group`
- Column Labels → `Risk Category`
- Value Fields → `No. of Patients`, `% of Patients`

### d. Removed Unnecessary Grand Total % Column

### e. Applied Conditional Formatting
- **High Risk %** → Red (high %) to Green (low %)
- **Low Risk %** → Green (high %) to Red (low %)

---

Next steps include:
- Inserting a PivotChart (100% Stacked Column)
- Adding slicers for interactivity
- Creating additional pivot tables by lifestyle and health indicators

