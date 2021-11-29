# BE 434 Project: Lookup Table Containing Potassium Concentration by Food or Drink

## Repo Contents 

- `project.py`: Python script that allows the user to seach or add to the lookup table 

- `create_lookup_table.py`: Python script which creates the lookup table using information from the raw data 

- `lookup_table.txt`: Text file containing different food/drink items and their potassium concentrations (mg/L)

- `potassium.pdf`: PDF obtained from the USDA website containing various foods and drinks along with their corresponding potassium content (mg) for a given amount

- `raw_data_file.txt`: Text file containing the data information as the potassium.pdf file 

---

## Overview

For my senior design project, my team and I have to design a potassium diaganostic system that tracks the users daily potassium intake. The user can directly measure potassium concentration (mg/L) for food or drink using an ion-selective electrode, or they can choose to use the system's built-in lookup table to obtain a 'known' potassium concentration (mg/L) for the item. The system then uses image processing software to estimate the volume (L) of the given item in order to calculate potassium content (mg). Potassium concentraion is never shown to the user becuase the primary purpose of the system is to track potassium intake (mg) throughout the day.

For the purposes of this project, I decided to write a program that has the ability to: 
- Create a lookup table containing item descriptions and their corresponding potassium concentrations
- Seach through the lookup table and obtain the corresponding potassium concentration for the selected item, which is then displayed for the user
- Add new items to lookup table for future use

---

## Creating the Lookup Table 

To create the lookup table, run the following command in your terminal: 

```
$ ./create_look_up_table.py
```
*Please note that raw_data_file.txt will need to be downloaded prior to running the command*

---

## Searching Through the Lookup Table

To search through the lookup table, begin by running the following command to see the selection options: 
```
$ ./project.py             

Please make a selection:
1: Search lookup table
2: Add a new entry
3: Quit
```

Then, select the first option and enter you search term to see the matching results:
```
$ ./project.py             

Please make a selection:
1: Search lookup table
2: Add a new entry
3: Quit
$ 1

Enter a serch term:
$ soda 

Search Results:
1: Bread, irish soda, prepared from recipe
2: Beverages, carbonated, club soda 

Please enter the corresponding number:
```

Lastly, select the desired item to see its corresponding potassium concentration:
```
$ ./project.py             

Please make a selection:
1: Search lookup table
2: Add a new entry
3: Quit
$ 1

Enter a serch term:
$ soda 

Search Results:
1: Bread, irish soda, prepared from recipe
2: Beverages, carbonated, club soda

Please enter the corresponding number:
$ 2

Item Description: Beverages, carbonated, club soda
Potassium Concentration: 33.81 mg/L  
```

To check the search results, you can run the following two commands: 
```
$ grep 'soda' ./lookup_table.txt 
Bread, irish soda, prepared from recipe
Beverages, carbonated, club soda
```
```
$ tail -4 lookup_table.txt      
Beverages, carbonated, club soda
33.81
Beverages, carbonated, low calorie, other than cola or pepper, with aspartame, contains caffeine
33.81
```

---

## Adding to the Lookup Table

To add to the lookup table, begin by running the following command to see the selection options: 
```
$ ./project.py             

Please make a selection:
1: Search lookup table
2: Add a new entry
3: Quit
```

Then, select the second option and enter the desired item description:
```
$ ./project.py             

Please make a selection:
1: Search lookup table
2: Add a new entry
3: Quit
$ 2

Enter a description:
$ peach
```

Lastly, enter the corresponding potassium concentration (mg/L):
```
$ ./project.py             

Please make a selection:
1: Search lookup table
2: Add a new entry
3: Quit
$ 2

Enter a description:
$ peach
Enter the corresponding concentration (mg/L):
$ 20

New concentration has been added.
```

To confirm that the lookup table has been updated, you can run the following command: 
```
$ tail -2 lookup_table.txt 
peach
20.0
```

---

## Methods

Creating the Lookup Table:
1. The raw data file is read line by line 
2. Items with non-numeric volumes (ex. package, bottle) are ignored
3. Volumes for the remaining items are converted to litres 
4. Potassium concentation (mg/L) is calculated using potassium content (mg) and volume (L)
5. The item description and it's corresponding potassium concentration are added to the lookup_table.txt file

Searching Through the Lookup Table:
1. User selects the first option
2. User enters a search term
4. The lookup table file is read line by line, and descriptions containg the search phrase are saved along with their corresponding potassium concentration
4. The saved item descriptions are listed and the user selects the desired item from the matches
5. The selected item and its potassium concentration are obtained from the saved matches and displayed for the user to see

Adding to the Lookup Table:
1. User selects the second option
2. User enters a new item description
3. User enters the corresponding potassium concentration
4. The item description and its potassium concentration are appended to the lookup table file

---
