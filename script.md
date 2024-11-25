

# Python Scripts for CSV Operations Lesson

## 1. Reading a CSV File

This script demonstrates how to read a CSV file and print its rows.

```python
import csv

# Reading a CSV file
with open('players_20.csv', 'r') as file:
    reader = csv.reader(file)
    for row in reader:
        print(row)
```
---

## 2. Writing to a CSV File

This script demonstrates how to create a new CSV file and write rows to it.

```python
import csv

# Writing to a CSV file
with open('new_file.csv', 'w', newline='') as file:
    writer = csv.writer(file)
    header = ['Name', 'Class', 'City']
    rows = [
        ['Akash', '6', 'Delhi'],
        ['Shishir', '9', 'Mumbai'],
        ['Geeta', '11', 'Bangalore']
    ]
    writer.writerow(header)
    writer.writerows(rows)

print("CSV file created successfully!")
```
---

## 3. Building a Basic Streamlit App

This script introduces Streamlit to handle CSV file upload and processing.

```python
import streamlit as st
import pandas as pd

# Title
st.title("CSV File Operations with Streamlit")

# File upload
uploaded_file = st.file_uploader("Upload a CSV file", type=["csv"])

if uploaded_file:
    # Read the file and display the data
    data = pd.read_csv(uploaded_file)
    st.write("Uploaded CSV Data:")
    st.dataframe(data)

    # Summing a specific column
    column_name = st.text_input("Enter the column name to calculate sum:")
    if column_name and column_name in data.columns:
        try:
            total = data[column_name].astype(int).sum()
            st.write(f"The sum of values in '{column_name}' is: {total}")
        except ValueError:
            st.error("The selected column contains non-numeric values.")
    elif column_name:
        st.error("Column not found in the CSV file.")
```
---

## 4. Adding Data and Creating a New CSV

This script allows users to add data interactively and save it to a new CSV file, with the option to add or remove columns dynamically.

```python
import streamlit as st
import pandas as pd

# Title
st.title("Create and Download a Custom CSV File")

# Initialize session state for columns and rows
if "columns" not in st.session_state:
    st.session_state.columns = ["Name", "Class", "City"]
if "data" not in st.session_state:
    st.session_state.data = []

# Section to add/remove columns
st.header("Customize Columns")
new_column = st.text_input("Add a new column:")
if st.button("Add Column"):
    if new_column and new_column not in st.session_state.columns:
        st.session_state.columns.append(new_column)
        st.success(f"Column '{new_column}' added!")
    elif new_column in st.session_state.columns:
        st.warning(f"Column '{new_column}' already exists.")
    else:
        st.error("Column name cannot be empty.")

remove_column = st.selectbox("Select a column to remove:", st.session_state.columns)
if st.button("Remove Column"):
    if remove_column in st.session_state.columns:
        st.session_state.columns.remove(remove_column)
        st.success(f"Column '{remove_column}' removed!")
    else:
        st.error("No such column to remove.")

# Display current columns
st.write("Current Columns:", st.session_state.columns)

# Section to add rows
st.header("Add Data")
row_data = {}
for col in st.session_state.columns:
    row_data[col] = st.text_input(f"Enter value for {col}")

if st.button("Add Row"):
    if all(row_data.values()):  # Ensure all fields are filled
        st.session_state.data.append(row_data)
        st.success("Row added!")
    else:
        st.error("Please fill in all fields.")

# Display current data
if st.session_state.data:
    df = pd.DataFrame(st.session_state.data)
    st.write("Current Data:")
    st.dataframe(df)

    # Download the custom CSV
    csv_data = df.to_csv(index=False).encode("utf-8")
    st.download_button(
        label="Download CSV",
        data=csv_data,
        file_name="custom_data.csv",
        mime="text/csv"
    )
```
---

## 5. Full Streamlit App

This integrates all components into a single app.

```python
import streamlit as st
import pandas as pd

# Title
st.title("CSV Operations App")

# Upload section
uploaded_file = st.file_uploader("Upload a CSV file", type=["csv"])
if uploaded_file:
    data = pd.read_csv(uploaded_file)
    st.write("Uploaded CSV Data:")
    st.dataframe(data)

    # Sum a column
    column_name = st.text_input("Enter column name to calculate sum:")
    if column_name and column_name in data.columns:
        try:
            total = data[column_name].astype(int).sum()
            st.write(f"Sum of '{column_name}': {total}")
        except ValueError:
            st.error("Column contains non-numeric values.")
    elif column_name:
        st.error("Column not found.")

# Create new CSV
st.write("---")
# Title
# Title
st.title("Create and Download a Custom CSV File")

# Initialize session state for columns and rows
if "columns" not in st.session_state:
    st.session_state.columns = ["Name", "Class", "City"]
if "data" not in st.session_state:
    st.session_state.data = []

# Section to add/remove columns
st.header("Customize Columns")
new_column = st.text_input("Add a new column:")
if st.button("Add Column"):
    if new_column and new_column not in st.session_state.columns:
        st.session_state.columns.append(new_column)
        st.success(f"Column '{new_column}' added!")
    elif new_column in st.session_state.columns:
        st.warning(f"Column '{new_column}' already exists.")
    else:
        st.error("Column name cannot be empty.")

remove_column = st.selectbox("Select a column to remove:", st.session_state.columns)
if st.button("Remove Column"):
    if remove_column in st.session_state.columns:
        st.session_state.columns.remove(remove_column)
        st.success(f"Column '{remove_column}' removed!")
    else:
        st.error("No such column to remove.")

# Display current columns
st.write("Current Columns:", st.session_state.columns)

# Section to add rows
st.header("Add Data")
row_data = {}
for col in st.session_state.columns:
    row_data[col] = st.text_input(f"Enter value for {col}")

if st.button("Add Row"):
    if all(row_data.values()):  # Ensure all fields are filled
        st.session_state.data.append(row_data)
        st.success("Row added!")
    else:
        st.error("Please fill in all fields.")

# Display current data
if st.session_state.data:
    df = pd.DataFrame(st.session_state.data)
    st.write("Current Data:")
    st.dataframe(df)

    # Download the custom CSV
    csv_data = df.to_csv(index=False).encode("utf-8")
    st.download_button(
        label="Download CSV",
        data=csv_data,
        file_name="custom_data.csv",
        mime="text/csv"
    )
```
---

## Instructions for Students

1. Save each script in separate `.py` files.
2. Run the Streamlit app scripts using the command:
   ```bash
   streamlit run <script_name>.py
   ```
3. Upload sample CSV files and interact with the app to understand the operations.
4. Customize the columns and rows as needed for creating new CSV files.

