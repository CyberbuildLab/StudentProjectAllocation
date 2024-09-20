# Student (Thesis) Project Allocation Data Preparation
This project contains code to:
1. Prepare data for allocating students to projects using the allocation optimiser *pdn_project_allocation* at https://github.com/RudolfCardinal/pdn_project_allocation;
2. Report the final allocations in a format suitable for sharing with students and project supervisors.

## Allocation-Preparation:
This Jupyter Notebook takes the spreadsheet of Topic, Subject Area and Project Type preferences exported from an MS form to produce the student-project matrix required for running the allocation optimiser *pdn_project_allocation* at https://github.com/RudolfCardinal/pdn_project_allocation

<ins>Assumptions and Notes:</ins>
- Topics, Subject Areas and Project Types are also considered to be "projects" according to *pdn_project_allocation*, but Topics are systematially ranked above Subject Areas and Subject Areas above Project Types.
- Project Type is currently discarded (because it has not been needed at all for now), but could be dealt with like the Subject Areas.
- Student selection form asks for top 5 preferred projects, top 3 preferred Subject Areas, and top 3 preferred Project Types.

TODO:
- [ ] Not crticial: Adjust ranking value if students don't give exactly 5 Preferred Topics, 3 Subject Areas and 3 project Types.
- [ ] Add example MS Form 

## Allocation-Reporting:

This Jupyter Notebook takes the result spreadsheet from the allocation optimiser *pdn_project_allocation* and creates the final allocation and summary statistics spreadsheets that are shared with students and project supervisors.

TODO:
- [ ] Check one last time that it's working.
- [X] Currently requires the output file exists. It would be best if it could just be created on demand (using 'open()' function?)
- [X] Add statistics sheet.
