# Student (Thesis) Project Allocation Data Preparation
This code takes the spreadsheet of Topic, Subject Area and Project Type preferences exported from an MS form to produce the student-project matrix required for running the allocation optimiser *pdn_project_allocation* at https://github.com/RudolfCardinal/pdn_project_allocation

<ins>Assumptions and Notes:</ins>
- Topics, Subject Areas and Project Types are also considered to be "projects" according to *pdn_project_allocation*, but Topics are systematially ranked above Subject Areas and Subject Areas above Project Types.
- Project Type is currently discarded (because it has not been needed at all for now), but could be dealt with like the Subject Areas.
- Student selection form asks for top 5 preferred projects, top 3 preferred Subject Areas, and top 3 preferred Project Types.

TODO:

- [ ] Adjust ranking value if students don't give exactly 5 Preferred Topics, 3 Subject Areas and 3 project Types.
