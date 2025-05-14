# Student (Thesis) Project Allocation
This project contains:
1. Jupyter Notebook to prepare data for optimising the allocation of students to projects using the optimiser *pdn_project_allocation*;
2. Submodule (Python code) mirroring the *pdn_project_allocation* project (from https://github.com/RudolfCardinal/pdn_project_allocation) to optimally assign projects to students;
3. Jupyter Notebook to report the final Student-Project allocations in Excel spreadsheets suitable for sharing with students and project supervisors.
4. Jupyter Notebook to report Reader allocation (supervisor and 2nd reader) statistics calculated from the Reader-Student/Project allocation (which is currently done manually).

## Allocation-Preparation:
This Jupyter Notebook takes the spreadsheet of Topic, Subject Area and Project preferences (exported from an MS form) and an Input spreadsheet containing the lists of Students, Supervisors and Project, in order to produce the student-project matrix required for running the allocation optimiser *pdn_project_allocation*. All the data necessary for the optimiser is outputted in a specific output file.

<ins>Assumptions and Notes:</ins>
- Topics, Subject Areas and Project Types are all treated as "projects" according to *pdn_project_allocation*, but Topics are systematially ranked above Subject Areas and Subject Areas above Project Types.
- Project Type is currently discarded (because it has not been needed at all for now), but could be dealt with like the Subject Areas.
- Student preference selection form asks for top 5 preferred projects, top 3 preferred Subject Areas, and top 3 preferred Project Types.

## pdn_project_allocation:
This is a submodule of the GitHub project at https://github.com/RudolfCardinal/pdn_project_allocation. It uses as the spreadsheet outputted in step 1 and conducts the optimisation using the information it contains. The intput and output are concatenated in a single new output file.

## Allocation-Reporting:

This Jupyter Notebook takes the output spreadsheet of step 2 and creates the final allocation and summary statistics spreadsheets that are shared with students and project supervisors.

## Readers-Reporting

This Jupyter Notebook takes the result spreadsheet from the allocation of Readers to each student/project (currently done manually) and outputs statistics about the number of times each supervisor is 1st reader (supervisor) and 2nd Reader. This enables the course organiser to assess whether some readers have been over or under-allocated.

## TODO:
- [ ] Adjust ranking value if students don't give exactly 5 Preferred Topics, 3 Subject Areas and 3 project Types (not critical)
- [ ] Add example MS Form used to obtain student preferences.
- [ ] Check one last time that the process for conducting the optimisation and reporting its results works correctly
- [ ] Ensure all the files are outputted in one place in a logical naming/order.
- [ ] Automate the Reader Allocation process
- [ ] Convert Jupyter Notebooks into simple Python scripts.
