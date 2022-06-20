# Turning CSVs into Credits made easy!
Have you ever had a client ask you to make a credits reel for their video and hand you a MASSIVE excel document full of names? Nobody has time to re-type or even copy-paste all those names into a text box in Premiere or After Effects and try to clunkily animate it! Fortunately, this script can help take that spreadsheet and quickly turn it into a credits reel that's all ready to animate!

# Index:
- [**Overview**](https://github.com/candyandy951/ae-csv-to-credits#overview)
  - [How it Works](https://github.com/candyandy951/ae-csv-to-credits#how-it-works)
  - [Additional Details](https://github.com/candyandy951/ae-csv-to-credits#additional-details)
- [**Installation**](https://github.com/candyandy951/ae-csv-to-credits#installation)
- [**Setup**](https://github.com/candyandy951/ae-csv-to-credits#setup)
- [**How To Use**](https://github.com/candyandy951/ae-csv-to-credits#how-to-use)
  - [General Info Panel](https://github.com/candyandy951/ae-csv-to-credits#general-info-panel)
  - [CSV Info Panel](https://github.com/candyandy951/ae-csv-to-credits#csv-info-panel)
  - [Name/Subtitle Text Options](https://github.com/candyandy951/ae-csv-to-credits#namesubtitle-text-options)
- [**Appendix**](https://github.com/candyandy951/ae-csv-to-credits#appendix)
  - [Changing the Character Used as List Separator in Excel on Windows 10](https://github.com/candyandy951/ae-csv-to-credits#changing-the-character-used-as-list-separator-in-excel-on-windows-10)
  - [**Color Picker Credit**](https://github.com/candyandy951/ae-csv-to-credits#color-picker-credit)

# Overview:
**How it Works**
This script is designed to create a new comp at a width that the user specifies, the height of the comp will be determined automatically based on the number of name entries. The script inserts a new text layer for each name and subtitle entry, and pulls the data from the CSV to put in those text boxes. The great part about using this script to insert CSV data into text boxes as opposed to using an expression to read a CSV file is that the text is directly editable in After Effects after the script runs. The downside is if names need to be added or removed, you'll need to run the script again with an updated CSV (or mess with manually trying to move the text layers around).
The comp that the script creates will be one frame in duration. This is because once you start running this script with lists of names 50+ names long you can quickly start bogging AE down with all the layers. The intention of this script is to have you render this single frame comp as a PNG with transparency (use the PNG Sequence render module), then re-import that PNG back into AE to do any scrolling animation needed.

**Additional Details**
- This script is meant to be used to create "walls of names" as opposed to a more basic name & position side-by-side style of credits.
- This script is currently only capable of pulling 3 columns of information from a CSV, a first name, a last name, and a subtitle. Not all 3 need to be used and the script is mildly friendly to mixing and matching these three attributes.
- This script expects you to have a CSV of your names and titles prepared ahead of time, it will not create a CSV from a spreadsheet document for you. Fortunately it's pretty easy to export CSVs from most spreadsheet editors.
- This script is NOT smart enough to read a CSV as a CSV like After Effects can, it relies on you to tell it what character is being used to split entries in the CSV. This poses issues if you have commas in your cell content (for example if you had something like "Firstname, Lastname" in a single cell), normally the CSV export process will just put quotations around the content of that cell and a smart CSV reading program would know what that means. THIS SCRIPT IS NOT THAT SMART! If you have commas within your cell content, you will need to change the character that is used to separate your entries to something other than a comma

# Installation:
- Download the latest .jsx release file.
- Open the script from the After Effects "File>Scripts>Run Script File..." menu
- OR copy the script file into your After Effects plugin folder to quick select it from the File>Scripts menu.

# Setup:
You MUST have "Allow Scripts to Write Files and Access Network" toggled ON in the Preferences>Scripting & Expressions menu for this script to function correctly

<img width="419" alt="Scripting Preferences Window with Top Toggle (Allow Scripts to Write Files and Access Network) highlighted" src="https://user-images.githubusercontent.com/59343247/174502417-517bea39-da28-45c0-a665-d554964c6f8a.png">


# How to Use:
The script will open a new window, in this window you will specify the details of your credits, the CSV format, set fonts, colors, etc.
The default settings will work well for creating credits in a 1920px wide comp, however once you start changing more than colors, you may want to do a couple test runs by limiting the number of CSV rows used just to make sure the credits look how you want them to aesthetically. More on that below in the "CSV Info" section.

<img width="450" alt="Image of the default script window" src="https://user-images.githubusercontent.com/59343247/174394842-366fbbd4-6418-4786-90a4-741a5df807d0.png">

## General Info Panel
<img width="419" alt="General Info Panel with 1 Column toggled" src="https://user-images.githubusercontent.com/59343247/174502562-0e5df256-c6ee-479d-9c36-12c602313ccc.png">

1. **New Comp Width** - This box is where you specify how wide the new comp will be, the height of the comp will be determined by the number of name/subtitle entries created.
2. **Number of Credits Columns** - This script is capable of creating either one single column of credits or two columns side-by-side. [*You'll notice portions of the General Info Panel change when toggling between 1 and 2 columns*](https://user-images.githubusercontent.com/59343247/174503094-48a3ff47-c95f-4128-94bf-762ed6052218.png)
3. **Center Align Credits Column/Distribute Credits Columns Horizontally** - This checkbox toggles your ability to manually specify where the credits will be placed horizontally in the comp. By default it is checked and the "X Pos" box(es) are uneditable. When unchecked, the "X Pos" box(es) will shift position* and become editable.   * (The position shift is a side effect of me not being the best at ScriptUI... Technically the uneditable and editable boxes are two different objects. If I was manually specifying object location in the UI I could probably make the two boxes on top of one another, but that was a lot of work to figure out at the time.)
4. **1st Column X Pos/2nd Column X Pos** - When "Center Align Credits Columm/Distribute Credits Columns Horizontally" is checked, this box (or boxes if 2 columns is selected) will display the horizontal X position that the centers of the text boxes will be placed. If "Center Align Credits Columm/Distribute Credits Columns Horizontally" is unchecked, these boxes will be editable and you can manually specify where the text boxes will be generated.
5. **Text Box Dimensions** - These boxes are where you can specify the size of text box you want the script to generate for each name and subtitle entry. The first box (width) is most important since it will impact the wrapping of the text. If you have long entries and you do not want them to wrap, you might want to increase this value. The second box (height) is important if you are wrapping text, to make sure the text box is large enough vertically to fit all of the text. Fortunately, this script doesn't rely heavily on this value outside of allowing text to display, so you can just make it MUCH bigger than you need and be safe.
6. **Vertical Space Between Each Name** - This is how vertically separated your entries will be from one another. This number is a value in pixels, but it's not a perfectly exact number as the script also relies on the height of the entry text and position of any subtitles generated to determine where to generate the next entry, so this is more of a ballpark number that you'll want to test and dial in.

## CSV Info Panel
<img width="419" alt="CSV Info Panel - Defaults" src="https://user-images.githubusercontent.com/59343247/174503548-8e821ead-c64b-4e4a-89e8-cf6a0a4ee71d.png">

1. **Choose CSV File...** - Click this button to open a browser window and navigate to your CSV file. The filepath will be displayed in the box to the right of the button once a file is selected.
2. **Character Used in CSV as List Separator** - Normally CSV data is separated by commas (hence CSV = COMMA Separated Values), because some credits information may need to include commas, you may need to export a CSV with a character other than a comma separating the entries (now CSV = "CHARACTER Separated Values"). This script isn't smart enough to actually read the CSV file as a CSV file so it won't know what to do with the quotations most applications will put around entries that include a comma. If your credits data includes commas, you'll need to change the list separator character (directions on how to do this in Excel on Windows at the bottom of this ReadMe, I don't currently know of any other methods for doing this on MacOS or in other apps). If your CSV uses a character other than a comma as a list separator, you must specify that in this box.
3. **Does the CSV have a Header Row?** - Most spreadsheets will include a header as the first row that specifies what data is in each column. Checking this checkbox tells the script to ignore the first row and not print the header as a credit entry. If your CSV does NOT include a header row, UNCHECK this box, otherwise your first entry will not be generated.
4. **Limit Number of CSV Rows Used?** - Because the script doesn't live preview what the credits will look like, you may need to run a couple tests to ensure your credits look how you want them aesthetically. Since generating the credits does take time (especially with CSVs containing 50+ rows) this checkbox allows you to specify how many rows the script prints so you don't waste time waiting for it to run through all your entries just to realize it looks bad. Toggling this box will pop open a [box](https://user-images.githubusercontent.com/59343247/174504003-77606ee5-ddd5-46ed-826c-ecfc98750800.png) where you can specify how many rows/entries to print. *NOTE: This toggle plays nice with the "Header Row" toggle, regardless of the status of the header row toggle, the script will always print the number of entries you specify in the box.*
5. **Column in CSV with Names** - This is where you specify which column in the CSV contains the name entries. If last names are in a separate column (see below) this is where you specify the column with the FIRST names. *NOTE: unlike spreadsheet apps, CSV's count their columns and rows starting at ZERO. If your names are in the FIRST row, then they are actually in row ZERO!*
6. **Last Name in Separate Column?** - If the first and last names are in separate columns, toggling this checkbox will make a new [box](https://user-images.githubusercontent.com/59343247/174631015-6e30240f-e61f-4c11-a0e6-8eb9d556a8dd.png) appear where you can specify which columns contains the last names. If first and last names are in separate columns, the script will automatically combine them into the same text box when generating the credits. *REMEMBER: CSV's count their columns and rows starting at ZERO!*
7. **Is There a Subtitle Column?** - If your credits should have a subtitle generate above or below the name entries, toggle this checkbox. Doing so will make several additional [options](https://user-images.githubusercontent.com/59343247/174631513-e7b83f40-933f-4bd5-a252-8dbd0e27c9c8.png) appear:
   - **Subtitle Column Box** - Where you specify which CSV column the subtitle data is in. *REMEMBER: CSV's count their columns and rows stating at ZERO!
   - **Subtitle Above Name?** - By default, the script will generate the subtitles below the name entries, if you want the subtitle to be above the name, toggle this checkbox.
   - **Space Between Name and Subtitle** - Similar to the "Vertical Space Between Each Name" box from the General Info panel, this value is technically measured in pixels, but is again more of a ballpark number since other factors such as text wrapping, font, font size, etc also play a part in how far the subtitle is from the name entry. Again, it's recommended to limit the number of entries and run a couple tests to dial the aesthetics in before running the script on the full CSV.

## Name/Subtitle Text Options
<img width="419" alt="Name and Subtitle Text Options - Defaults" src="https://user-images.githubusercontent.com/59343247/174634218-ba83989d-59f5-49da-9692-999dae7331c6.png">
*The Subtitle Text Options only appear when "Is There a Subtitle Columns" is checked*

1. **Name/Subtitle Font** - This is a text box where you specify the name of the font you want your Name/Subtitle to be in. However, it is not advised that you manually type the font name in, since After Effects can be touchy about what certain fonts are actually named. Instead, it is recommended that you use the "Choose Font..." button. This button will generate a new comp in your project called "Font Chooser Comp", this new comp will have one text layer on it with instructional text. Alter the font family and font style of the text layer to what you want, then click "Done" in the script window. The script will pull the font family and style information from the text layer and insert the name of the font in the text box so you don't have to. *NOTE: ONLY the font family and font style information is captured from the text layer, if you change the color, font size, leading, or any other attribute of the text layer, the script will NOT retain that information. The Font Chooser Comp is ONLY for choosing a font, nothing else!
2. **Name/Subtitle Font Size** - Set the font size of the name/subtitle entries
3. **Apply Fill?** - By default the text will generate with a fill. To generate with no fill, uncheck this box. Clicking the white box to the right of the checkbox will open a color picker window where you can choose the color of the text fill. *[Color picker](https://github.com/smallpath/adobe-color-picker) is created by [smallpath](https://github.com/smallpath) and [zlovatt](https://github.com/zlovatt), more info below.
4. **Apply Stroke?** - By default the text will generate with no stroke. To generate a stroke, check this box. When you do, a color picker box will appear as well as a [box](https://user-images.githubusercontent.com/59343247/174648444-1c03db9d-ab3c-4203-b702-57937b0d2cd0.png) to specify the stroke width.
5. **Stroke over Fill?** - If you do add a stroke to the text, the script will default to having the stroke over the fill, to have the stroke behind the fill, uncheck this box.
6. **Justification** - This will affect the justification of the text WITHIN the generated text box. The text boxes that get generated will still all be centered on the "Column X Pos" pixel. Because all text boxes will be generated at the same given size, it is possible to justify the text left or right, you will just need to update the "Column X Pos" accordingly.
7. **Text Leading** - This edits the leading of the text in the text box. Since leading is the spacing between lines of text, this is only really important when text wrapping occurs.
8. **Text Tracking** - This edits the tracking of the text in the text box. Tracking is the space between text characters horizontally.

# Appendix
## Changing the Character Used as List Separator in Excel on Windows 10
Below are the steps to take to change what character is used as the list separator when exporting a CSV from Excel on Windows 10. I don't currently know of any other solutions to export a CSV with a list separator other than a comma, if you do know I'm hungry for the knowledge.

Excel uses the settings in Windows to determine what your list separator should be in a CSV, by default (in North America at least) is to use a comma (,). To change this default:
- Open the Windows Control Panel
- Navigate to "Region"
- Click "Additional Settings"
In this Additional Settings window, there should be a box for "List Separator". For use of this script, change this to a character that does NOT appear in your spreadsheet data AT ALL. Click "Apply". Now when you File>Export>CSV from Excel, it should use the list separator you specified in the Windows settings.
![Image showing the windows control panel windows needed to change the list separator character](https://user-images.githubusercontent.com/59343247/174659199-83b05dde-6793-4074-a156-6ef03c0d5c40.png)

## Color Picker Credit
Shoutout to [smallpath](https://github.com/smallpath) and [zlovatt](https://github.com/zlovatt) for the color picker used in this script, it's WAY nicer than the default OS color picker that would pop up otherwise. Check out the github page for the color picker [HERE](https://github.com/smallpath/adobe-color-picker).
