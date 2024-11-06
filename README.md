# MEESSI-AHF Automated Risk Calculator

## Overview

This project provides an **automated script** to interact with the MEESSI-AHF Risk Model web calculator, aiming to streamline the process of calculating 30-day mortality risk for patients with Acute Heart Failure (AHF) in the Emergency Department (ED). Please note that this repository only automates data entry and result extraction from the MEESSI-AHF calculator, as hosted on their official website. **This project does not modify or interpret the MEESSI-AHF score** and should only be used with a clear understanding of the disclaimer below.

The MEESSI-AHF score itself was developed based on data from Spanish ED patients, and details on the model, patient cohort, and validation can be found in the publication:

> Miro O et al. *Predicting 30-day Mortality for Patients with Acute Heart Failure Who Are in the Emergency Department: A Cohort Study*. Ann Intern Med 2017.

For full information on the MEESSI-AHF Risk Model and the score, visit the official website: [MEESSI-AHF Risk Calculator](https://meessi-ahf.risk.score-calculator-ica-semes.portalsemes.org/).

## Disclaimer

The **MEESSI-AHF Risk Model** is intended solely for use by qualified healthcare professionals. This automated script is only a tool to interact with the MEESSI-AHF web calculator, and **it should not replace clinical judgment or medical decision-making**. By using this automation, you agree to assume all responsibility for its outcomes.

### Legal Disclaimer (as per MEESSI-AHF website)
- The MEESSI-AHF risk model tool is intended for use by physicians.
- The information provided by this tool is **not a substitute for clinical judgment** and is **not sufficient for making medical decisions**.
- I disclaim any responsibility for how you interpret the MEESSI-AHF risk score.
- Please refer to the full disclaimer on the MEESSI-AHF website.

## Features

- **Automates Data Entry**: Inputs patient data into the MEESSI-AHF online form to streamline the calculation process.
- **Extracts Results**: Retrieves the calculated 30-day mortality risk and risk category for each patient.
- **Image-Based Risk Mapping**: Extracts and maps diagnostic images used in the MEESSI-AHF calculator to risk categories based on predefined mappings (e.g., "Low risk", "High risk").
- **Interactive Notebook**: An interactive Jupyter notebook file, `AutomatedMEESSI.ipynb`, is provided to allow for easy interaction and testing within a notebook environment.

## Prerequisites

This script requires **Python 3.x**, **Selenium**, and **ChromeDriver**.

### Selenium and ChromeDriver

The script uses **Selenium** to automate interactions with the MEESSI-AHF website. Selenium is a tool for automating web browsers, and it requires a compatible **web driver**. This project uses **ChromeDriver** specifically for Google Chrome. Here’s how to set it up:

1. **Install Selenium**:
   ```bash
   pip install selenium

2.	**Download ChromeDriver**:
- Visit [ChromeDriver download page](https://developer.chrome.com/docs/chromedriver/downloads) to download the ChromeDriver version that matches your installed version of Google Chrome.
- After downloading, place the ChromeDriver executable in a known location and specify its path in the script (e.g., chromedriver_path = '/path/to/chromedriver').
3. **Specify ChromeDriver Path**:
- Update the chromedriver_path variable in the script with the path to your ChromeDriver executable:
    ```py
    chromedriver_path = '/path/to/chromedriver'

---

## Sample Data

A sample Excel file, `MEESSI_AHF_Test_Data.xlsx`, is provided in this repository to help you get started. This file contains example patient data formatted for input into the automated script.

### Sample Data Structure

The following table shows the data fields expected in the Excel file. Ensure your data aligns with this structure:

| Patient ID | Barthel index | SBP | Age | NTprobnp | K  | NYHA_class_IV | Troponin | RR | Low output | Spo2RA | ACS | LVH | Cr |
|------------|---------------|-----|-----|----------|----|---------------|----------|----|------------|--------|-----|-----|----|
| 001        | Unknown       | 160 | 78  |          | 3.2| Yes           | Positive | 28 | 1          | 96     | 1   | 1   | 1.2|
| 002        | 60            | 130 | 82  | 7000     | 4.0| No            | Normal   | 24 | 0          | 89     | 0   | 0   | 2.0|
| 003        | 80            | 120 | 85  | 15000    | 5.0| No            | Unknown  | 30 | 0          | 85     | 1   | 1   | 1.8|
| 004        | Unknown       | 150 | 76  |          | 3.8| Yes           | Positive | 22 | 1          | 92     | 0   | 1   | 1.1|
| 005        | 90            | 100 | 90  | 25000    | 5.6| Yes           | Normal   | 26 | 1          | 83     | 1   | 0   | 2.5|

Place your data file in the same directory as the script, or provide the path to it when running the script.

## Data Description
### Data Table

| Variable              | Description                                           | Example Value |
|-----------------------|-------------------------------------------------------|---------------|
| Barthel Index         | Score indicating the independence of the patient      | Unknown       |
| Systolic BP (SBP)     | Systolic blood pressure                               | 140           |
| Age                   | Patient's age                                         | 75            |
| NT-proBNP             | NT-proBNP level (biomarker for heart failure)         | 8000          |
| Potassium (K)         | Potassium level                                       | 4.5           |
| NYHA class IV         | NYHA classification for heart failure severity        | Yes, No       |
| Troponin level        | Troponin level indicator                              | Positive      |
| Respiratory rate (RR) | Respiratory rate                                      | 25            |
| Low output symptoms   | Symptoms indicating low cardiac output; 1=Yes, 0=No   | 1, 0          |
| Oxygen saturation (Spo2RA) | Oxygen saturation on room air                    | 95            |
| Episode with ACS      | Association with Acute Coronary Syndrome; 1=Yes, 0=No | 1, 0          |
| Hypertrophy at ECG (LVH) | Left ventricular hypertrophy on ECG; 1=Yes, 0=No   | 1, 0          |
| Creatinine (Cr)       | Creatinine level                                      | 1.2           |

### Result

| Variable              | Description                                        | Example Value |
|-----------------------|----------------------------------------------------|---------------|
| MEESSI                | Calculated MEESSI score                            | 28.5%         |
| Risk Group            | Calculated risk group                              | Very High     |
| Quintile/Decile       | Risk quintile or decile based on MEESSI            | 10th decile   |


## License

This project is licensed under the MIT License. See the LICENSE file for details.

## Acknowledgments

The MEESSI-AHF score and model were developed by SEMES and ICASEMES.

This automation tool is inspired by the MEESSI-AHF web calculator. The authors of this project are not affiliated with the creators of the MEESSI-AHF risk model.

For further queries about the MEESSI-AHF score, please contact omiro@clinic.cat.

For report about this code, please leave a comment in **Issues**.

**Note**: Use this tool at your own risk. This is a third-party automation tool and is not endorsed by the creators of the MEESSI-AHF Risk Model. Always validate and interpret results with clinical judgment and caution.