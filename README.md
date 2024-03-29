# Employee CSV
***a program for converting a .csv of employee data to a mysql database***

## Contents
- [CSV Format](README.md#csv-format)
- [Using the program](README.md#using-the-program)
- [Technologies used](README.md#technologies-used)
- [Scrum Process](README.md#scrum-process)
- [Performance with & without use of lambdas in the CSV read](README>MD#performance-with-&-without-use-of-lambdas-in-the-csv-read)

## CSV Format
The program expects CSV files with records in the following format:

|Emp ID|Name Prefix|First Name|Middle Initial|Last Name|Gender|E-Mail|Date of Birth|Date of Joining|Salary
|---|---|---|---|---|---|---|---|---|---|
|198429|Mrs.|Serafina|I|Bumgarner|F|serafina.bumgarner@exxonmobil.com|9/21/1982|2/1/2008|69294|
|178566|Mrs.|Juliette|M|Rojo|F|juliette.rojo@yahoo.co.uk|5/8/1967|6/4/2011|193912|
|647173|Mr.|Milan|F|Krawczyk|M|milan.krawczyk@hotmail.com|4/4/1980|1/19/2012|123681|
|847634|Mr.|Elmer|R|Jason|M|elmer.jason@yahoo.com|4/9/1996|5/28/2017|93504|
|...|...|...|...|...|...|...|...|...|...|

The file *can* have a header, but only if the first entry in the header row is `Emp ID` exactly.

## Using the program
When the program starts, the user will be prompted to enter a file path of a csv for the program to read from.
> Please enter a file path: 

While reading the file, the program will indicate if any records are invalid and print them to the console.
> The following record is not a valid employee: 

After the file is read, the user will be prompted to enter a number of threads for the program to run on while inserting the read data into the database.
> Please enter the number of threads you would like (1 - 20): 

Each record that can be successfully read will be added to a different table in the output database one table at a time using the specified number of threads:
- Valid records will be added to the main table.
- Valid duplicate records will be added to their own table.
- Records with valid formatting but invalid values will be added to their own table of "questionable" records.

## Technologies used
The following technologies & libraries were used in the creation of this software:
- JetBrains IntelliJ Ultimate
- GitHub
- Oracle's MySQL
- JUnit 5 Jupiter
- Apache Log4j 2

## Scrum Process
Autumn Pelešová was the Scrum Master, and was responsible for organizing scrums and delegating development responsibility among the group for each sprint
Andy Murray created and maintained the Trello board.
For an example of how we used Trello for our scrum development, here is a screenshot from Thursday afternoon:
![Trello board on Thursday afternoon](img/trello-thu-pm.png)
and here is a screenshot from Friday afternoon:
![Trello board on Friday afternoon](img/trello-fri-pm.png)

## Performance with & without use of lambdas in the CSV read
The difference in performance between the readCSV method before and after refactoring it to utilise lambdas was not statistically significant either way and varied between tests. With a large enough sample size, we may have seen more of a trend, but that's just our speculation for now.