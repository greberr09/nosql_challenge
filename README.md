# Module 12 nosql_challenge

This challenge is for the food editors of a magazine, "Eat Safe, Love," and is based on data that the UK Food Standards Agency creates after it evaluates establishments across the United Kingdom, and gives them, among other ratings, a food hygiene rating.   

For this challenge, the challenge author has been contracted by the editors of the magazine to evaluate some of the ratings data in order to help the magazine's journalists and food critics decide where they should focus future articles. 

The challenge involves the nosql database mongo_db, jupyter notebooks, and the Python database connection pymongo.  It uses Pandas to analyze data extracted from the database.

There are two jupyter notebooks for this challenge.  Both should be launched from the location where the notebooks are stored.  The first notebook, "NoSQL_setup_starter.ipynb", loads a jsoon file, "establishments.json," from the "Resources" subfolder, and makes various additions, deletions, and updates to the data.

The second jupyter notebook, "NoSQl_analysis_starter.ipynb", runs a series of queries on the establishments data to examine a number of hygiene and other ratings data, both in specific locations and throughout the United Kingdom.  

CODE EXECUTION NOTES:
=====================

Before either jupyter notebook is run, the mongo database server must be running on the localhost, pointing at the directory where the data is stored.

After mongod and the mongo utility tools are installed, the database server can be run from a terminal, after activating the proper conda environment, with the command: 

mongod -dbpath 'name_of_db_folder'

After the server is running, the json data for the establishmenents collection must be imported.  That can be done from a separate terminal or shell, in the proper conda environment, with the command:  

mongoimport --type json -d uk_food -c establishments --drop --jsonArray establishments.json   

The import command is also contained at the beginning of the NoSQL_setup notebook.   The import should be run in the Resources sub-folder containing the json file.

Json file upload:  

The json file does not show a different timestamp or size after the number of updates that were processed.  Therefore, adding it to GitHub with git add -f did not work, after the initial establishments.json had been added to the repository at the beginning of the project, nor did adding it with -no-assume-unchanged.  Git still saw it as nothing changed.  So, the original file was deleted from the repository and the updated file was added after all of the work was complete.   This was a final suggestion by our instructor if the "no assumed unchanged" did not work.

Notes on the code:

Both jupyter notebooks are based on starter code provided, which was mostly detailed comments, with almost no code being included.   Those comments are included in the delivered code.   Many additional comments were added, both in markdown cells and in code blocks.  The one exception, other than opening database boilerplate, where code for updating a field was provided, is noted in comments in the cell.

The challenge requirements include some specific methods for how certain operations, such as converting strings to integers and floats, should be done.   There are several markdown cells in each notebook commenting on these methods, and the use of other possile methods in a production environment for better error handling and information retention.

Part of the requirements is to add a new restaurant to the collection.  The latitude and longitude were provided by the challenge authors.  In the NoSQL_analysis notebook, there are two queries involving that location, to find both all restaurants and all entities within a specified distance of that location.  There are also several additional queries involving that entity, if it had been situated in a more restaurant-friendly part of Greenwich (Greenwich is a part of the London metropolitan area).  These additional queries were not part of the challenge requirements.

The method of string to number conversion in mongodb that is ultimately used was a combination of quite a bit of research in stack overflow and chatGPT, even though it is only one update statement using a specified method.  The alternative data checking and updating methods that are discussed in the markdown cells are also a combination of similiar research.  Initially, those methods were used succesfully to do the conversions, before the code was switched to the required "update_many()".  The updating of those three fields, and the research about it, were by far the most complicated and time-intensive parts of this challenge, at least for this coder, even though many other parts would appear to be more complex.