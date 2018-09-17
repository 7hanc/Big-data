# Big-data

# Homework 1

> Goal
* Analyze NYC Taxi Data by using any data analytic tool or package, and deal with the following problems:
>> Dataset
* Taxi data: http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml
> Question
* Q1: What regions have most pickups and drop-offs?
* Q2: When are the peak hours and off-peak hours in taking taxi?
* Q3: What differences exist between short and long distance trips of taking taxi? (Give as many as you can.)
# Homework 2
> Goal
* Use Hadoop Pig Latin to analyze the given dataset and answer the following questions. You can use the Hadoop platform provided by NARLabs or use your own machines.
>> Dataset
* Airline on-time performance dataset
http://stat-computing.org/dataexpo/2009/
> Questeion
* Compute the average delays and find the maximal delays for each month by using data of all years.
`group_month = group Table_csv by Month;
results = FOREACH group_month GENERATE group, AVG(Table_csv.ArrDelay), MAX(Table_csv.ArrDelay);
dump results;
`
* How many plane delays were caused by weather? Please also show the average delays.
* Which is the best month of a year to fly with minimum delays?
* List top 5 airports (using IATA airport code) with largest average delay  and show which type of delay occurs most for each of the top 5 airport.
