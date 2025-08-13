# Student (Thesis) Project Allocation
This project contains:
1. Jupyter Notebook to prepare data for optimising the allocation of students to projects using the optimiser *pdn_project_allocation* (from https://github.com/RudolfCardinal/pdn_project_allocation) to optimally assign projects to students;
2. Jupyter Notebook to report the final Student-Project allocations in Excel spreadsheets suitable for sharing with students and project supervisors.
3. Jupyter Notebook to report Reader allocation (supervisor and 2nd reader) statistics calculated from the Reader-Student/Project allocation (which is currently done manually).

## Allocation-Preparation:
This Jupyter Notebook takes as input:
- **Student data** spreadsheet containing 3 tabs: 
    - *Students*
    - *Student_preferences* (exported from an MS Form,), 
    - *Student_selfproposals* (only used for the Allocation reporting below)
- **Topic data** spreadsheet containing 1 tab:
    - *Topics* with the following columns: Code, Title, Supervisor, Subject Area, Research Type, Level, Max. Students
- **Supervisor data** spreadsheet containing 2 tabs:
    - *Supervisors*
    - *Supervisors_preferences*. 
The notebook produces the `01_Output.xlsx` containing the input data required for running the allocation optimiser *pdn_project_allocation*.

The *pdn_project_allocation* optimiser should be rung as follows (assuming it is run from the the folder containing `./O1_Output.xlsx`:

```
pdn_project_allocation.exe --output .\02_Output.xlsx .\01_Output.xls
```

<ins>Assumptions and Notes:</ins>
- *Topics*, *Subject Areas* and *Project Types* in the Student Preferences spreadsheet are all treated as *projects* according to the *pdn_project_allocation* optimiser, but *Topics* are systematially ranked above *Subject Areas* and *Subject Areas* above *Project Types*.
- *Project Type* is currently discarded (because it has not been needed at all for now).
- The Student Preferences selection form asks for top 5 preferred Topics, top 3 preferred Subject Areas, and top 3 preferred Project Types.

## Allocation-Reporting:
This Jupyter Notebook takes the output spreadsheet of step 2 (`./O2_Output.xlsx`) and creates:
1. The final project allocation data spreadsheet that is shared with the students and supervisors (`./O3_Output.xlsx`).
2. The final project allocation data and summary statistics spreadsheet for internal user (`./O3_Output_Internal.xlsx`).

## Readers-Allocation:
This Jupyter Notebook takes the list of supervisors and the allocated projects, and then allocate second readers so that the overall load of all supervisors is balanced as much as possible and 2nd readers are allocated topics that fall in their Subject Areas of interest. 

## Readers-Reporting (to be merged with previous one):
This Jupyter Notebook takes the result spreadsheet from the allocation of Readers to each student/project (currently done manually) and outputs statistics about the number of times each supervisor is 1st reader (supervisor) and 2nd Reader. This enables the course organiser to assess whether some readers have been over or under-allocated.

## TODO:
- [x] Check one last time that the process for conducting the optimisation and reporting its results works correctly
- [x] Ensure all the files are outputted in one place in a logical naming/order.
- [x] Merge student-related spreadsheet into one spreadsheet (with multiple tabs) and same for supervisor spreadsheet. This way, the input will include just 3 spreadsheets.
- [ ] Add `Example Data\` folder including all Input spreadsheets.
- [ ] Adjust ranking value if students don't give exactly 5 Preferred Topics, 3 Subject Areas and 3 project Types (not critical)
- [ ] Automate the Reader Allocation process (initiated)
- [ ] Merge Readers-Reporting notebook into Readers-Allocation notebook
- [ ] (optional) Convert Jupyter Notebooks into simple Python scripts
