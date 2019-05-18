# ETLProject_Team15

World Cup ETL Project

Purpose:
To extract, transform and load FIFA World Cup datasets of countries, matches and players dating back to 1930 along with country participants’ socioeconomic dataset into MySQL relational database


Extract:
We located the FIFA World Cup datasets from Kaggle formatted as three CSV files. The datasets show all related key information about the World Cup matches dating back to the 1930 tournament, results of match winners and the players and countries involved. With this FIFA World Cup datasets, we wanted to merge it with socioeconomic information to analyze if country economic factors have any effect on their match performance. This socioeconomic dataset was also found in Kaggle. For both datasets, to properly read the data into a pandas dataframe, we had to update the encoding for all CSV files to ISO-8859-1.

Transform:
For the FIFA World Cup datasets, we filtered and cleaned up the data using pandas by setting the three CSV files into dataframes to easily read the data and select which column tables to use. We made sure that key column tables: MatchID, Home/Away Team Names and Player Names were included so that the user can perform join queries between the tables loaded in MySQL. Additionally, we cleaned up the data by dropping the null values to avoid loading unnecessary data into MySQL.

For the Socioeconomic dataset, we first had to remove the period from the CSV file name to avoid potential file type confusion. And to properly leverage pandas and to read the data in a dataframe, we changed the encoding to ISO-8859-1 since without it it was generating a ‘UTF-8’ codec can’t decode byte 0xf4 in position 1: invalid continuation byte. Also, like the FIFA World Cup datasets, we removed lines with blank/null values using the dropna and we replaced some country names so that the datasets are consistent.

In order to ensure the dataseTo ensure the country name tables between the FIFA World Cup and Socioeconomic are consistent, we conducted additional cleanup steps to make sure country names between the two match. For example, Czech Republic was previously known as Czechoslovakia - so in the Socioeconomic dataset, the country Czech Republic was updated to Czechoslovakia so that dataset may match the FIFA World Cup dataset. ts between the FIFA World Cup and Socioeconmi

Load:
As shown in the Jupyter Lab notebook, we leveraged MySQL to load our cleaned up datasets. In order to do so, we established connection using pymysql and executed SQL queries to create databases within MySQL. With using to_sql, we were able to load each of the datasets into MySQL. We conducted tests to ensure all the datasets were loaded into MySQL properly by using read_sql_query and also ran the following SQL queries in MySQL so that all of the loaded data can selected, pulled and viewed properly.


