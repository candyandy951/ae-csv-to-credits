# Turning CSVs into Credits made easy!
Have you ever had a client ask you to make a credits reel for their video and hand you a MASSIVE excel document full of names? Nobody has time to re-type or even copy-paste all those names into a text box in Premiere or After Effects and try to clunkily animate it! Fortunately, this script can help take that spreadsheet and quickly turn it into a credits reel that's all ready to animate!

# How to use
## Setup:
- This script is currently only capable of pulling 3 columns of information from a CSV, a first name, a last name, and a subtitle. The script is mildly friendly to mixing and matching these three attributes.
- This script expects you to have a CSV of your names and titles prepared ahead of time, it will not create a CSV from a spreadsheet document for you. Fortunately it's pretty easy to export CSVs from most spreadsheet editors.
- This script is NOT smart enough to read a CSV as a CSV like After Effects can, it relies on you to tell it what character is being used to split entries in the CSV. This poses issues if you have commas in your cell content (for example if you had something like "Firstname, Lastname" in a single cell), normally the CSV export process will just put quotations around the content of that cell and a smart CSV reading program would know what that means. THIS SCRIPT IS NOT THAT SMART! If you have commas within your cell content, you will need to change the character that is used to separate your entries to something other than a comma





After Effects script to convert a character separated values (CSV) document to a credits crawl. The script will generate a comp of specified width and variable height based on number of credits entries. The comp will be 1 frame long with the intention of the user rendering a PNG sequence from it (resulting in a single PNG) to then re-import into the project and animate as needed.

(This ReadMe could use some work... That's a later issue)
