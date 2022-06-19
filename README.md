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
The default settings will work well for creating credits in a 1920px wide comp, however once you start changing more than colors, you may want to do a couple test runs by limiting the number of CSV rows used just to make sure the credits look how you want them to aesthetically. More on that below in the "CSV Info" section.
<img width="766" alt="Image of the default script window" src="https://user-images.githubusercontent.com/59343247/174394842-366fbbd4-6418-4786-90a4-741a5df807d0.png">

###### General Info Panel
<img width="419" alt="General Info Panel with 1 Column toggled" src="https://user-images.githubusercontent.com/59343247/174502562-0e5df256-c6ee-479d-9c36-12c602313ccc.png">

1. **New Comp Width** - This box is where you specify how wide the new comp will be, the height of the comp will be determined by the number of name/subtitle entries created.
2. **Number of Credits Columns** - This script is capable of creating either one single column of credits or two columns side-by-side. [*You'll notice portions of the General Info Panel change when toggling between 1 and 2 columns*](https://user-images.githubusercontent.com/59343247/174503094-48a3ff47-c95f-4128-94bf-762ed6052218.png)
3. **Center Align Credits Column/Distribute Credits Columns Horizontally** - This checkbox toggles your ability to manually specify where the credits will be placed horizontally in the comp. By default it is checked and the "X Pos" box(es) are uneditable. When unchecked, the "X Pos" box(es) will shift position* and become editable.   * (The position shift is a side effect of me not being the best at ScriptUI... Technically the uneditable and editable boxes are two different objects. If I was manually specifying object location in the UI I could probably make the two boxes on top of one another, but that was a lot of work to figure out at the time.)
4. **1st Column X Pos/2nd Column X Pos** - When "Center Align Credits Columm/Distribute Credits Columns Horizontally" is checked, this box (or boxes if 2 columns is selected) will display the horizontal X position that the centers of the text boxes will be placed. If "Center Align Credits Columm/Distribute Credits Columns Horizontally" is unchecked, these boxes will be editable and you can manually specify where the text boxes will be generated.
5. **Text Box Dimensions** - These boxes are where you can specify the size of text box you want the script to generate for each name and subtitle entry. The first box (width) is most important since it will impact the wrapping of the text. If you have long entries and you do not want them to wrap, you might want to increase this value. The second box (height) is important if you are wrapping text, to make sure the text box is large enough vertically to fit all of the text. Fortunately, this script doesn't rely heavily on this value outside of allowing text to display, so you can just make it MUCH bigger than you need and be safe.
6. **Vertical Space Between Each Name** - This is how vertically separated your entries will be from one another. This number is a value in pixels, but it's not a perfectly exact number as the script also relies on the height of the entry text and position of any subtitles generated to determine where to generate the next entry, so this is more of a ballpark number that you'll want to test and dial in.

###### CSV Info Panel
<img width="419" alt="CSV Info Panel - Defaults" src="https://user-images.githubusercontent.com/59343247/174503548-8e821ead-c64b-4e4a-89e8-cf6a0a4ee71d.png">

1. **Choose CSV File...** - Click this button to open a browser window and navigate to your CSV file. The filepath will be displayed in the box to the right of the button once a file is selected.
2. **Character Used in CSV as List Separator** - Normally CSV data is separated by commas (hence CSV = COMMA Separated Values), because some credits information may need to include commas, you may need to export a CSV with a character other than a comma separating the entries (now CSV = "CHARACTER Separated Values"). This script isn't smart enough to actually read the CSV file as a CSV file so it won't know what to do with the quotations most applications will put around entries that include a comma. If your credits data includes commas, you'll need to change the list separator character (directions on how to do this in Excel on Windows at the bottom of this ReadMe, I don't currently know of any other methods for doing this on MacOS or in other apps). If your CSV uses a character other than a comma as a list separator, you must specify that in this box.
3. **Does the CSV have a Header Row?** - Most spreadsheets will include a header as the first row that specifies what data is in each column. Checking this checkbox tells the script to ignore the first row and not print the header as a credit entry. If your CSV does NOT include a header row, UNCHECK this box, otherwise your first entry will not be generated.
4. **Limit Number of CSV Rows Used?** - Because the script doesn't live preview what the credits will look like, you may need to run a couple tests to ensure your credits look how you want them aesthetically. Since generating the credits does take time (especially with CSVs containing 50+ rows) this checkbox allows you to specify how many rows the script prints so you don't waste time waiting for it to run through all your entries just to realize it looks bad. Toggling this box will pop open a [box](https://user-images.githubusercontent.com/59343247/174504003-77606ee5-ddd5-46ed-826c-ecfc98750800.png) where you can specify how many rows/entries to print. *NOTE: This toggle plays nice with the "Header Row" toggle, regardless of the status of the header row toggle, the script will always print the number of entries you specify in the box.*
