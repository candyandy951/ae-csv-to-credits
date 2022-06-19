# Turning CSVs into Credits made easy!
Have you ever had a client ask you to make a credits reel for their video and hand you a MASSIVE excel document full of names? Nobody has time to re-type or even copy-paste all those names into a text box in Premiere or After Effects and try to clunkily animate it! Fortunately, this script can help take that spreadsheet and quickly turn it into a credits reel that's all ready to animate!

# How to use
## Overview:
**How it Works**
This script is designed to create a new comp at a width that the user specifies, the height of the comp will be determined automatically based on the number of name entries. The script inserts a new text layer for each name and subtitle entry, and pulls the data from the CSV to put in those text boxes. The great part about using this script to insert CSV data into text boxes as opposed to using an expression to read a CSV file is that the text is directly editable in After Effects after the script runs. The downside is if names need to be added or removed, you'll need to run the script again with an updated CSV (or mess with manually trying to move the text layers around).
The comp that the script creates will be one frame in duration. This is because once you start running this script with lists of names 50+ names long you can quickly start bogging AE down with all the layers. The intention of this script is to have you render this single frame comp as a PNG with transparency (use the PNG Sequence render module), then re-import that PNG back into AE to do any scrolling animation needed.

**Additional Details**
- This script is meant to be used to create "walls of names" as opposed to a more basic name & position side-by-side style of credits.
- This script is currently only capable of pulling 3 columns of information from a CSV, a first name, a last name, and a subtitle. Not all 3 need to be used and the script is mildly friendly to mixing and matching these three attributes.
- This script expects you to have a CSV of your names and titles prepared ahead of time, it will not create a CSV from a spreadsheet document for you. Fortunately it's pretty easy to export CSVs from most spreadsheet editors.
- This script is NOT smart enough to read a CSV as a CSV like After Effects can, it relies on you to tell it what character is being used to split entries in the CSV. This poses issues if you have commas in your cell content (for example if you had something like "Firstname, Lastname" in a single cell), normally the CSV export process will just put quotations around the content of that cell and a smart CSV reading program would know what that means. THIS SCRIPT IS NOT THAT SMART! If you have commas within your cell content, you will need to change the character that is used to separate your entries to something other than a comma

## Installation:
- Download the latest .jsx release file.
- Open the script from the After Effects "File>Scripts>Run Script File..." menu
- OR copy the script file into your After Effects plugin folder to quick select it from the File>Scripts menu.

## Setup:
You MUST have "Allow Scripts to Write Files and Access Network" toggled ON in the Preferences>Scripting & Expressions menu for this script to function correctly

<img width="500" alt="Scripting Preferences Window with Top Toggle (Allow Scripts to Write Files and Access Network) highlighted" src="https://user-images.githubusercontent.com/59343247/174502417-517bea39-da28-45c0-a665-d554964c6f8a.png">


## How to Use:
The script will open a new window, in this window you will specify the details of your credits, the CSV format, set fonts, colors, etc.
<img width="766" alt="Image of the default script window" src="https://user-images.githubusercontent.com/59343247/174394842-366fbbd4-6418-4786-90a4-741a5df807d0.png">

###### General Info Panel

- **New Comp Width** - This box is where you specify how wide the new comp will be, the height of the comp will be determined by the number of name/subtitle entries created.
- **Number of Credits Columns** - This script is capable of creating either one single column of credits or two columns side-by-side. *You'll notice portions of the General Info Panel change when toggling between 1 and 2 columns*
- **Center Align Credits Column/Distribute Credits Columns Horizontally** - This checkbox toggles your ability to manually specify where 
