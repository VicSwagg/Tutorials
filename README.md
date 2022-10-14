## Navisworks to BIM360 Workflow

### Intro
This workflow populates a BIM360 Workspace with issues that have pre-assigned parameters pulled directly from  Navisworks Clash Tests. The issues can then be visualized in 3D.
<br>
### Step 1: Revit - NWC Settings:
Hit Export in Revit>File>export NWC

- Open Export Settings
- Modify your NWC settings with the Interface > Display units set to feet or feet & inches

Check your Element settings:
- Do you want rooms to convert?
- Linked files?
- A linked file in Navis will come is as a chunk, but clashes will still happen on individual objects
- CAD formats?

Verify what you're exporting:
- Selection?
- Current View?
- Entire Model?
- Current view is probably the best, especially if in each of your files for Navis you maintain a "Navisworks - - Export" 3D view that is tailored to just what you want to export to use in Navisworks
- Turn off annotation, analytical, and imported objects
<br>
### Step 2: Navisworks:
Edit Quick Properties:

![1](https://user-images.githubusercontent.com/108774367/195907964-8c005ec7-c0c4-4b56-bc5c-e675ee681245.png)


- Find Items Quick find Selection Tree 
- Match your quick properties to Element Category, Element Name, Element Size
- This works well for plumbing, steel, and hvac

![2](https://user-images.githubusercontent.com/108774367/195907995-ed3b4d37-4eea-4806-845f-a2631a51675d.png)


#### Creating Clash Tests:

- Get your selection/search sets the way you want
- Run your clashes with whatever mix of linked NWCs and search sets as you want
- Edit/group your clashes as you see fit
- Any clashes you want to ignore tag as reviewed or resolved

#### Assigning Clashes:

In order to interface with an expedited BIM360 workflow, we need to create special naming conventions, comments, and assignments that will be easily transferred to the BIM360 platform. We need to adjust the following:
##### 1. Clash Name
The clash name should correspond to Locations we will add to our BIM360 project. 

<img src="Location Name.mp4">

In the example above, all of the clashes are located in "LL, North Wing, Foundation".

##### 2. Status
The status in Navisworks offers 5 options to choose from - New, Active, Reviewed, Approved, and Resolved. BIM360 on the other hand offers 4 status options - Open, In Review, Pending, and Closed.
We generally try to adhere to the following rules:
- __"New"__ status is the default, and therefor should not be used during export.
- __"Active"__ status should be used for all active, non-penetration coordination related clashes. The "Active" status in Navisworks will correspond to the "Open" status in BIM360.
- __"Reviewed"__ status in Navisworks corresponds to the "In Review" status in BIM360.
- __"Approved"__ status works well in classifying "Penetrations for Approval". "Approved" in Navisworks corresponds to "Pending" in BIM360.
- __"Resolved"__ status in Navisworks corresponds to the "Closed" status in BIM360.

##### 3. Assigned To
We can use assignments to preemptively assign clashes to members, roles, or companies.  Each of the parties assigned in Navisworks will need to be added to the BIM360 workspace exactly as they appear.

<img src="Assignments.mp4">

__Members__ - Use an email address<br>
__Role__ - Use one of the following BIM360 built-in roles:
- BIM Manager
- Architect
- Construction Manager
- Document Manager
- Engineer
- Estimator
- Executive
- Foreman
- IT
- Project Engineer
- Project Manager
- Superintendent
- VDC Manager

__Company__ - if assignment doesn't contain an email address or one of the pre-assigned roles, the script will default to Company.

##### 4. Comments
Comments can be used to accomplish 3 things: Priority Level, Location Descriptions, and Clash Detail Descriptions.

![Comments and Assignments](https://user-images.githubusercontent.com/108774367/195910300-f49baf83-b6fc-4736-bbde-456dc49a6599.PNG)

__Priority Level__ - Type either "high", "medium", or "low" to distinguish between priority.<br>
__Location Descriptions__ - Add "<" to the beginning of the location description and ">" to the end.<br>
__Clash Detail Descriptions__ - Add "*" to the beginning and end of the clash detail description.

<img src="Comments.mp4">

#### Exporting HTML report:

Export Report as HTML Tabular with the following Items checked:

![Navis Export Settings](https://user-images.githubusercontent.com/108774367/195910433-4486a1fa-635d-4482-82e3-995ab58d70ba.PNG)

- Include the statuses you want to show in your report
- If you are using review/resolved for clashes you want to ignore, uncheck

### Step 3: Excel:
In this step, we format our .html navisworks report to an .xlsx that can be loaded directly into BIM360. Navigate to C:\Egnyte\Shared\Digital Construction Team\02_Digital Assets\00_BIM360 and open file "acc-issues-import-template.xlsx"

Open the "Guide" tab

![Guide Tab](https://user-images.githubusercontent.com/108774367/195910466-3fe381bf-9651-43ff-a4c2-465b0f21d120.PNG)

Here we can find detail about how the file is set up to formulate entries on the "ACS Build" tab.  We can also establish an "Assign Date" which is a date we can use as a reference for the day that clashes are reviewed with the team.  Our due dates represent the dates our assigned party needs to resolve the clash based on the level of priority:

<br>__High Priority__ - Currently set to one week from assignment date
<br>__Medium Priority__ - Currently set to two weeks from assignment date
<br>__Low Priority__ - Currently set to 4 weeks from assignment date.

<br>If the "Assigned To" category is blank, due dates won't be assigned.

<img src="Import Data.mp4">

Browse to Data Tab>existing connections>Browse for more

Navigate to file


Hit highest arrow on upper left (arrow should appear orange/red)

Import

![Import View](https://user-images.githubusercontent.com/108774367/195910574-d2b5dd32-f9cf-4e54-ab73-d30ab786e34f.PNG)

Save somewhere that makes sense to your project, likely in same spot as your HTML report

If your HTML Tabular report changes, but does not change name relative to what you had previously, just hit refresh under Data>Refresh all

### Step 4: BIM360
Navigate to the BIM 360 dashboard. Before we import our .xlsx, we want to make sure our team members and locations have been added, our sub-types are created, and the custom field for "Priority Level" has been created.

##### 1. Adding Team Members
Navigate to Project Admin. From here, we can add individual members with role assignments on the "Members" tab, or more general companies on the "Companies" tab.

![Add Members](https://user-images.githubusercontent.com/108774367/195910631-a5d71e61-1098-4e10-b499-d2f3d119dd54.PNG)

##### 2. Adding Project Locations
Under the "Settings" tab we can navigate to "Locations" and add the locations we input into Navisworks exactly as they appeared.

![Locations](https://user-images.githubusercontent.com/108774367/195910652-37950236-070c-4f2f-b7d8-4d32fd1fc9e7.PNG)

##### 3. Adding Sub-Types
If we navigate to "Docs"

![Docs](https://user-images.githubusercontent.com/108774367/195910681-eb2f1303-4b85-41ee-a4af-3e70d75580e8.PNG)

Under the "Issues" tab we can navigate to "Types" and add a sub-type for Penetrations.

![Sub-Types](https://user-images.githubusercontent.com/108774367/195910701-38335afe-cea7-4ed5-968c-a2165629054d.PNG)

##### 4. Adding Custom Fields
Also within the "Issues" tab we navigate to "Settings" to add a custom field to our project as shown below:

![Priority Level](https://user-images.githubusercontent.com/108774367/195910728-f02010dd-b3ee-450d-baaf-6516287f2730.PNG)


#### Import .xlsx file

<br>Navigate back to the "Issues" tab and select the drop down next to "+ Create Issue"

<img src="Create Issues.mp4">

After we've added our issues in bulk we can navigate through them and assign a marker placement to each issue:

