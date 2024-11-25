
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

This script allows users to add data interactively and save it to a new CSV file.

```python
import streamlit as st
import pandas as pd

# Title
st.title("Create and Download a New CSV File")

# Input fields
name = st.text_input("Enter Name")
student_class = st.text_input("Enter Class")
city = st.text_input("Enter City")

# Initialize list for new data
new_data = []

# Add row button
if st.button("Add Row"):
    if name and student_class and city:
        new_data.append({'Name': name, 'Class': student_class, 'City': city})
        st.success("Row added!")
    else:
        st.error("Please fill in all fields.")

# Display added rows
if new_data:
    new_df = pd.DataFrame(new_data)
    st.write("Current Data:")
    st.dataframe(new_df)

    # Save and download the new CSV
    if st.button("Download CSV"):
        st.download_button(
            label="Download CSV",
            data=new_df.to_csv(index=False),
            file_name="new_data.csv",
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
st.header("Create New CSV")

name = st.text_input("Name")
student_class = st.text_input("Class")
city = st.text_input("City")

new_data = []

if st.button("Add New Row"):
    if name and student_class and city:
        new_data.append({'Name': name, 'Class': student_class, 'City': city})
        st.success("Row added!")

if new_data:
    new_df = pd.DataFrame(new_data)
    st.write("Current Data to Save:")
    st.dataframe(new_df)

    if st.button("Download New CSV"):
        st.download_button(
            label="Download CSV",
            data=new_df.to_csv(index=False),
            file_name="created_data.csv",
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

