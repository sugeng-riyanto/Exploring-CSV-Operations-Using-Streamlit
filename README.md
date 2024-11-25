# Exploring-CSV-Operations-Using-Streamlit



# CSV Operations with Streamlit

This project demonstrates how to perform various CSV operations using Python and Streamlit. The project is designed to help students understand how to handle CSV files interactively and apply these concepts in a Streamlit web application.

## Features

1. **Upload and Read CSV Files**:
   - Users can upload a CSV file to view its content.

2. **Column Sum Calculation**:
   - Input a column name to calculate the sum of its integer values.

3. **Create, Customize, and Download New CSV Files**:
   - Users can dynamically add or remove columns.
   - Enter data row-by-row, adjusting to the customized column structure.
   - Download the new dataset as a CSV file.

## Prerequisites

Ensure you have the following installed:

- Python 3.7+
- Streamlit
- Pandas

To install the required Python libraries, run:

```bash
pip install streamlit pandas
```

## How to Run the Project

1. Clone this repository or download the files.

2. Navigate to the directory containing the project files.

3. Run the Streamlit app using the following command:

```bash
streamlit run app.py
```

4. Open the provided URL in your web browser to access the app.

## Usage Instructions

### Upload and View CSV Files

1. Click on "Browse files" to upload a CSV file.
2. The content of the uploaded file will be displayed in a table.

### Calculate Column Sum

1. Enter the column name (case-sensitive) to calculate the sum of its integer values.
2. If the column contains non-numeric data, an error message will be displayed.

### Create, Customize, and Download a New CSV File

1. **Add/Remove Columns**:
   - Enter a column name and click "Add Column" to include it in the structure.
   - Use the dropdown menu to select and remove existing columns.
2. **Add Data Rows**:
   - Input data for each column dynamically based on the current column structure.
   - Ensure all fields are filled before adding a row.
3. **Download CSV**:
   - Once all rows are added, click "Download CSV" to save the customized file locally.

## Example Scenarios

- **Scenario 1**: Upload a dataset like `players_20.csv` to view its content.
- **Scenario 2**: Calculate the sum of a numeric column like "Wage".
- **Scenario 3**: Add custom columns and rows interactively to create a new dataset.

## Project Files

- `app.py`: The main script containing all features of the Streamlit app.
- `README.md`: This file, providing instructions for usage.

## Troubleshooting

- If Streamlit is not recognized as a command, ensure it is installed and added to your PATH.
- Check column names carefully when calculating sums; they are case-sensitive.
- Ensure that Python 3.7+ is installed on your system.

## Author

This project is part of a lesson designed to teach students CSV operations and Streamlit basics interactively.
