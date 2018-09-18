# Big-data (hw1+hw2)

# Homework 1 (Using pandas, kmeans(scikit-learn))

> Goal
* Analyze NYC Taxi Data by using any data analytic tool or package, and deal with the following problems:
>> Dataset
* Taxi data: http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml
> Question
* Q1: What regions have most pickups and drop-offs?
* Q2: When are the peak hours and off-peak hours in taking taxi?
* Q3: What differences exist between short and long distance trips of taking taxi? (Give as many as you can.)
# Homework 2 (Using Hadoop Pig Latin)
> Goal
* Use Hadoop Pig Latin to analyze the given dataset and answer the following questions. You can use the Hadoop platform provided by NARLabs or use your own machines.
>> Dataset
* Airline on-time performance dataset
http://stat-computing.org/dataexpo/2009/
> Questeion and Answer
* Compute the average delays and find the maximal delays for each month by using data of all years.  
`group_month = group Table_csv by Month;`  
`results = FOREACH group_month GENERATE group, AVG(Table_csv.ArrDelay), MAX(Table_csv.ArrDelay);`  
`dump results;`  
***
Answer: Group/ Average delays/ Maxmimal delays  
![Alt text](https://i.imgur.com/7QaH2sR.jpg)
***
* How many plane delays were caused by weather? Please also show the average delays.  
`group_all = group Table_csv all;`  
`wea = FOREACH group_all GENERATE COUNT(Table_csv.WeatherDelay), AVG(Table_csv.WeatherDelay);`  
`dump wea`  
***
Answer: Total_data/ Average delays  
(1524735, 3.0.90.1044738922)
***
* Which is the best month of a year to fly with minimum delays?   
`group_month = group Table_csv by Month;`   
`min_delay = foreach group_month generate group, MIN(Table_csv.ArrDelay) as min;`   
`min_delay = order min_delay by min ASC; //由小到大`   
`min_delay = limit min_delay 2; //顯示筆數`   
`dump min_delay;`   
* List top 5 airports (using IATA airport code) with largest average delay  and show which type of delay occurs most for each of the top 5 airport.   
`group_ori = group Table_csv by Origin;`      
`ori_avgd = foreach group_ori generate group, 
AVG(Table_csv.ArrDelay) as arr,
AVG(Table_csv.DepDelay) as dep,
AVG(Table_csv.CarrierDelay) as car,
AVG(Table_csv.WeatherDelay) as wea,
AVG(Table_csv.NASDelay) as nas,
AVG(Table_csv.SecurityDelay) as sec,
AVG(Table_csv.LateAircraftDelay) as lat;`   
`ori_avgd = order ori_avgd by arr desc; //由大到小`   
`ori_avgd = limit ori_avgd 5;`   
`dump ori_avgd;`   
***
![Alt text](https://i.imgur.com/GkxNR6s.png)
Answer:
top 5 airports: PUB, ACK, OTH, CEC, PIR (according to ArrDelay)
* In PUB, delay occurs most: ArrDelay
* In ACK, delay occurs most: NASDelay
* In OTH, delay occurs most: LateAircraftDelay
* In CEC, delay occurs most: NASDelay
*	In PIR, delay occurs most: CarrierDelay
***
