# Student (Thesis) Project Allocation
This project contains:
1. Jupyter Notebook to prepare data for optimising the allocation of students to projects using the optimiser *pdn_project_allocation* (from https://github.com/RudolfCardinal/pdn_project_allocation) to optimally assign projects to students;
2. Jupyter Notebook to report the automatically obtained Student-Project allocations in Excel spreadsheets suitable for sharing with students and project supervisors.
3. Jupyter Notebook to report the final Student-Project allocations alongside summary statistics in Excel spreadsheets for internal use by the Course Organiser.
4. Jupyter Notebook to optimise Reader allocation (supervisor and 2nd reader) and report the results and statistics.
5. Jupyter Notebook to report the results and statistics of the Marking of the projects (in progress).

## 01_Allocation-Preparation:
This Jupyter Notebook takes as input:
- **Student data** spreadsheet containing 3 tabs: 
    - *Students* with the key columns: Full Name and Email Address (which is used to match students to student preferences)
    - *Student_preferences* (exported from an MS Form), 
    - *Student_selfproposals* (only used for the Allocation reporting below) with the following columns: Student, Email, Code, Supervisor, Title, Subject Area, Type
- **Topic data** spreadsheet containing 1 tab:
    - *Topics* with the following columns: Code, Title, Supervisor, Subject Area, Research Type, Level, Max. Students.
- **Supervisor data** spreadsheet containing 2 tabs:
    - *Supervisors* with the following columns: Supervisor, Supervisor_short, Subject_area, Max_number_of_projects, Max_number_of_students, 2nd_reader.
    - *Supervisors_preferences* (see `pdn_project_allocation` for details).
The notebook produces the `01_Output.xlsx` containing the input data required for running the allocation optimiser *pdn_project_allocation*.

The *pdn_project_allocation* optimiser should be rung as follows (assuming it is run from the the folder containing `./O1_Output.xlsx`:

```
pdn_project_allocation.exe --output .\02_Output.xlsx .\01_Output.xls
```

<ins>Assumptions and Notes:</ins>
- *Topics*, *Subject Areas* and *Project Types* in the Student Preferences spreadsheet are all treated as *projects* according to the *pdn_project_allocation* optimiser, but *Topics* are systematially ranked above *Subject Areas* and *Subject Areas* above *Project Types*.
- *Subject Area* for both the projects and supervisors can be list of subject areas. The lists are strings with the subject areas separated by `;#` (this is because this is what MS Lists does when exporting into `xlsx`.
- *Project Type* is currently discarded (because it has not been needed at all for now).
- The Student Preferences selection form asks for top 5 preferred Topics, top 3 preferred Subject Areas, and top 3 preferred Project Types.

## 03_Allocation-Reporting:
This Jupyter Notebook takes the output spreadsheet of step 2 (`./O2_Output_yymmdd-hhmmss.xlsx`) and creates the final project allocation data spreadsheet that is shared with the students and supervisors (`./O3_Output_yymmdd-hhmmss.xlsx`).

## 04_Allocation-Statistics:
This Jupyter Notebook takes the output spreadsheet of step 3 (`./O3_Output_yymmdd-hhmmss.xlsx`)  as well as the list of Topics and the list of Supervisors, and creates the final project allocation data and summary statistics spreadsheet for internal use (`./O4_Output_yymmdd-hhmmss.xlsx`).
**NOTE**: Step 4 is not integrated in Step 3 because the output spreadsheet of step 3 (`./O3_Output_yymmdd-hhmmss.xlsx`) may be adjusted manually by the Course Organiser to reflect some request for reallocation.

## 05_Readers-Allocation:
This Jupyter Notebook takes the list of supervisors and the allocated projects, and then allocate second readers so that the overall load of all supervisors is balanced as much as possible and 2nd readers are allocated topics that fall in their Subject Areas of interest. 
The Jupyter Notebook outputs both the final reader allocations and supervisor+2nd reader statistics for all people.

## 06_Marking-Reporting (in progress):
This Jupyter Notebook takes the marking results of the two markers and the agreed marks and report the results and statistics of the marks. 

## TODO:
- [x] Check one last time that the process for conducting the optimisation and reporting its results works correctly
- [x] Ensure all the files are outputted in one place in a logical naming/order.
- [x] Merge student-related spreadsheet into one spreadsheet (with multiple tabs) and same for supervisor spreadsheet. This way, the input will include just 3 spreadsheets.
- [x] Automate the Reader Allocation process (initiated)
- [x] Merge Readers-Reporting notebook into Readers-Allocation notebook
- [ ] Complete the Marking Reporting notebook
- [ ] Add `Example Data\` folder including all Input spreadsheets.
- [ ] (optional) Adjust ranking value if students don't give exactly 5 Preferred Topics, 3 Subject Areas and 3 project Types (not critical)
- [ ] (optional) Convert Jupyter Notebooks into simple Python scripts
