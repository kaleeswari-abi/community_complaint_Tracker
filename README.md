# Implementation Plan - Community Complaint Tracker

We will build a **Community Complaint Tracker** application using Streamlit and Pandas. The app will allow citizens to report local issues (potholes, garbage, streetlights, etc.), validate input, log complaints to a local file storage (TXT/CSV), and provide a dynamic dashboard with counts, filtering, and charts.

## Design & Architecture

1. **User Interface (Streamlit)**:
   - Modern, clean layout with side-by-side metric cards for quick statistics.
   - Dynamic charts (using Streamlit's native `st.bar_chart` or Plotly/Altair) to visualize complaint categories and status.
   - Interactive, searchable data table using Pandas and `st.dataframe`.
   - **Log Complaint Form**:
     - Fields: Reporter Name, Contact Number (validated), Category (dropdown), Location/Address, Description, Severity (Low, Medium, High).
     - Full validation checks using dictionaries and `try-except` blocks.
     - Files will be stored as structured CSV/TXT files to cover "TXT handling".

2. **Data Model**:
   - Save complaints as CSV (`complaints.csv`) for easy loading into a Pandas DataFrame.
   - Save text logs in a separate text file (`complaints_log.txt`) to satisfy the TXT handling concept.
   - Validate contact numbers, empty fields, and handle errors robustly using `try-except`.

3. **Key Features**:
   - **Basic**: Form validation, saving to file, loading data, basic error handling.
   - **Intermediate**: Categorization, filtering complaints by category/status, counting issues.
   - **Extended**: Rich dashboard showing metrics (Total, Resolved, Pending), bar charts of categories, map visualization (mock coordinates for local areas or simple lists if coordinates are unavailable), and export functionality.

---

## Proposed Changes

### [Community Complaint Tracker App]

We will create the following files in the project workspace:

#### [NEW] [app.py](file:///c:/Users/AnudipCOA/Desktop/community%20complaint%20tracker/app.py)
This is the main entrypoint file. It will contain:
- Streamlit layout (Sidebar for submission, main panel for Dashboard & Data Explorer).
- Input fields with validators (regex or length checks, format constraints).
- Exception handling around file read/write operations.
- Pandas data processing for counting, aggregating, and displaying charts.

#### [NEW] [requirements.txt](file:///c:/Users/AnudipCOA/Desktop/community%20complaint%20tracker/requirements.txt)
Dependencies required:
- `streamlit`
- `pandas`
- `plotly` (for elegant visuals if needed, or we can use Streamlit's built-in charting)

---

## Verification Plan

### Manual Verification
1. **Validation Checks**: Try submitting empty names, invalid phone numbers, and verify error banners appear.
2. **Log Logging**: Check that `complaints.csv` and `complaints_log.txt` are created and correctly appended to.
3. **Data Aggregation**: Verify that numbers on the dashboard match the records in the table.
4. **Filtering**: Select categories/status in the filter sidebar to see the metrics change.
