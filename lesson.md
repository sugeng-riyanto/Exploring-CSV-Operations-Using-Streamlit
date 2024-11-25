
# Lesson Plan: Exploring CSV Operations Using Streamlit

## Grade/Target Audience: 
Beginner Python and Streamlit Users  

## Duration:
55 minutes  

---

## Lesson Objectives:
1. Understand the basics of CSV file operations (read, write, and manipulate).
2. Learn how to build an interactive Streamlit app to handle CSV files.
3. Apply Python and Streamlit to perform data operations and download results.

---

## Lesson Structure

### 1. Introduction (5 minutes)
**Objective**: Explain the importance of CSV files and Streamlit for data manipulation.

**Activity**:
- Ask students: "Where have you encountered CSV files in daily life? Examples: Excel exports, datasets."
- Briefly explain what CSV files are and their structure (rows and columns, comma-separated values).
- Introduce Streamlit as a Python-based tool for building interactive web apps.

---

### 2. Explanation of CSV Operations (10 minutes)
**Objective**: Walk through the Python code for reading and writing CSV files.

**Activity**:
- **Reading CSV Files**:
  - Show the example of `csv.reader` to read a file.
  - Highlight how to iterate through rows and extract data.
- **Writing to CSV Files**:
  - Explain how `csv.writer` can be used to create new files.
  - Illustrate appending rows with `writerow`.

**Key Points to Cover**:
1. Reading CSV files using Python.
2. Converting CSV data into lists for manipulation.
3. Writing CSV files by specifying headers and rows.

---

### 3. Building a Streamlit App (15 minutes)
**Objective**: Guide students to implement the CSV operations into a Streamlit app.

**Activity**:
1. **File Upload**:
   - Add a `st.file_uploader` widget to upload CSV files.
   - Use `pandas.read_csv` to read and display the file.
2. **Summing Column Values**:
   - Implement logic to sum integer columns interactively.
   - Use `st.text_input` to get column names.
3. **Writing New Data**:
   - Add `st.text_input` widgets for user inputs.
   - Use a list to store entered data rows.
   - Add a "Download CSV" button to save new data.
4. **Run the App**:
   - Demonstrate running the app using `streamlit run app.py`.

---

### 4. Hands-On Activity (20 minutes)
**Objective**: Students will write their own Streamlit app to practice CSV operations.

**Activity**:
1. Provide students with the following tasks:
   - Upload a sample CSV file (e.g., `players_20.csv`).
   - Extract and display a specific column.
   - Add new rows interactively and download the updated file.
2. Give real-time support as they code.
3. Share a GitHub link with the script if they need a reference.

---

### 5. Wrap-Up and Reflection (5 minutes)
**Objective**: Summarize the lesson and encourage questions.

**Activity**:
- Recap key concepts:
  1. Basics of reading and writing CSV files.
  2. Building interactive apps with Streamlit.
- Ask students to share one thing they found interesting or challenging.
- Assign a small task: "Customize the app by adding a new feature like filtering rows by a condition."

---

## Materials Needed
1. **Software**: Python, Streamlit, Text Editor (VS Code or similar).
2. **Sample Files**:
   - `players_20.csv` with at least one numeric column.
   - A blank CSV template for practice.

---

## Assessment
1. Check if students can upload and process a CSV file successfully.
2. Verify if students can create and download a new CSV file using Streamlit.
3. Observe students’ ability to implement the logic for summing column values.

---

This structured lesson plan ensures a balance of theoretical and practical learning, with hands-on activities to engage students effectively.
