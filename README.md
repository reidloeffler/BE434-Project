# BE 434 Project: Lookup Table Containing Potassium Concentration by Food or Drink

## Repo Contents 

- `project.py`: Python script that allows the user to seach or add to the lookup table 

- `create_lookup_table.py`: Python script which creates the lookup table using information from the raw data 

- `lookup_table.txt`: Text file containing different food/drink items and their potassium concentrations (mg/L)

- `potassium.pdf`: PDF obtained from the USDA website containing various foods and drinks along with their corresponding potassium content (mg) for a given amount

- `raw_data_file.txt`: Text file containing the data information as the potassium.pdf file 

---

## Creating the Lookup Table 

To create the lookup table, run the following command in your terminal: 

```
$ ./create_look_up_table.py
```
*Please note that raw_data_file.txt will need to be downloaded prior to running the command*

Method:
1. Items with non-numeric volumes (ex. package, bottle) are ignored
2. Volumes for the remaining items are converted to litres 
3. Potassium concentation (mg/L) is calculated using potassium content (mg) and volume (L)
4. The item description and it's corresponding potassium concentration are added to the lookup_table.txt file

---

## Searching Through the Lookup Table

To search through the lookup table, begin by running the following command to see the selection options: 
```
$ ./project.py             

Please make a selection:
1: Search look up table
2: Add a new entry
3: Quit
```

Then, select the first option and enter you search term to see the matching results:
```
$ ./project.py             

Please make a selection:
1: Search look up table
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
1: Search look up table
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
1: Search look up table
2: Add a new entry
3: Quit
```

Then, select the second option and enter the desired item description:
```
$ ./project.py             

Please make a selection:
1: Search look up table
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
1: Search look up table
2: Add a new entry
3: Quit
$ 2

Enter a description:
$ peach
Enter the corresponding concentration (mg/L):
20

New concentration has been added.
```

To confirm that the lookup table has been updated, you can run the following command: 
```
$ tail -2 lookup_table.txt 
peach
20.0
```
---