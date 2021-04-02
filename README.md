# updatemap
project that takes a data export of an activity schedule, transforms data to the activity instance level, and outputs the data for use in an ArcGIS online web app.

## Overview
  This is a small project in which a data export needed to be transformed for day level viewing, from source data that was by the "activity." So, the short version is that each recurring activity is one record in the source data, and upon export the schedule components need to be transformed, then replicated along the index. An example - activity meets on Monday and Wednesday, for 1 month, on the 1st and 3rd weeks of the month. This is one row in the source data, but the required result is 4 records (1st monday, 1st wednesday, 3rd monday, 3rd wednesday). In reality the recurrence expand much more, but that is the premise.
  
  The script supports an ArcGIS online Web App, that is used internally for park programming review. It is in production - I use that term loosely here - as a batch script running on a win64 platform. As such, the environment files are the win64 spec and haven't been tested on linux/macOS. None of the packages used are special, so this should be extensible to other cases.
  
  The entirety of the project is encapsulated with functions - I didn't implement any sort of a udf class structure because at the time I was brute forcing the code out and writing proper code was secondary to accomplishing the task. Open to any and all feedback!

*NOTE: I've omitted one component - dbwrite.py - that, instead of writing to csv, opens a MS-SQL Server connection, truncates a table, and then joins some other info like geospatial attributes based on the location name via a lookup table. All credit to Alex M. - this portion was not of my doing.*

*NOTE 2: The sample input data file is not real, but it is representative of the data that would be read in a production case. Similary, we have data outputting to a csv file (example in the 'output' directory), but in production a MS-SQL table is the target.*
