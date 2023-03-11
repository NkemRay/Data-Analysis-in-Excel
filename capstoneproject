-----                SESSION A (PROFIT ANALYSIS)
---- What was the profit of the breweries, inclusive of the anglophone and the francophone territories in the last three yaers?
SELECT
 (CASE
   WHEN 'countries' = 'Ghana' THEN 'Anglophone'
    WHEN 'countries' = 'Nigeria' THEN 'Anglophone'
     ELSE 'Francophone'
      END) AS territories, SUM(profit) AS profit_worth
FROM csv_table
 WHERE years IN ('2017', '2018', '2019')
  GROUP BY territories
   ORDER BY SUM(profit) 

----compare the total Profit between these two territories for strategic decision making

SELECT
 (CASE
   WHEN 'countries' = 'Ghana' THEN 'Anglophone'
    WHEN 'countries' = 'Nigeria' THEN 'Anglophone'
     ELSE 'Francophone'
      END) AS territories, SUM(profit) AS profit_worth
FROM csv_table 
 GROUP BY territories
  ORDER BY SUM(profit) 

----what country generated the highest profit in 2019
SELECT countries, MAX(profit) AS highest_profit
 FROM csv_table
  WHERE years = '2019'
   GROUP BY countries
    ORDER  BY MAX(profit) DESC LIMIT 1

----- Help him find the year with the highest profit
SELECT years, MAX(profit) AS highest_profit
 FROM csv_table
  GROUP BY years
   ORDER BY MAX(profit) DESC LIMIT 1

---- which month in the three years was the least profit generated
SELECT months, MIN(profit) AS least_profit
  FROM csv_table
   GROUP BY months
    ORDER BY MIN(profit) ASC LIMIT 1

---- what was the minimum profit in the month of December 2018
SELECT MIN(profit) AS min_profit
 FROM csv_table
  WHERE months = 'December' AND years ='2018'

----compare the profit for each of the months in 2019
SELECT SUM(profit) AS profit, months
 FROM csv_table
  WHERE years= '2019'
   GROUP BY months

----which particular brand generated the highest profit in senegal
SELECT brands, MAX(profit) AS highest_profit
 FROM csv_table 
  WHERE countries ='Senegal' 
   GROUP BY brands
    ORDER BY MAX(profit) DESC LIMIT 1

-----            SESSION B (BRAND ANALYSIS)
----- within the last two years,the brand manager wants to know the top three brands consumed in the francophone countries
SELECT  DISTINCT brands, SUM(quantity) AS consumed_brand
 FROM csv_table
  WHERE years IN ('2018', '2019') 
  AND countries IN('Senegal', 'Togo', 'Benin')
GROUP BY brands
 ORDER BY SUM(quantity) DESC LIMIT 3 
 
 ----find out the top two choice of the consumer brands in Ghana
 SELECT brands
  FROM csv_table
   WHERE countries ='Ghana'
    GROUP BY brands
     ORDER BY SUM(quantity) DESC LIMIT 2
 
-----find out the details of beer consumed in the past three years and in the west region
SELECT years, SUM(quantity) top_choiced
 FROM csv_table
   WHERE brands NOT LIKE '%malt'
   AND region = 'west'
 GROUP BY years
  ORDER BY SUM(quantity)

---- favourite malt brand in the anglophone countires IN 2018 and 2019
SELECT brands, SUM(quantity) favourite
 FROM csv_table
  WHERE countries IN ('Nigeria', 'Ghana')
  AND years IN ('2018', '2019')
  AND brands LIKE '%malt'
 GROUP BY brands
  ORDER BY SUM(quantity) DESC LIMIT 1
 
 ----which brands sold the highest in 2019 in nigeria
 
 SELECT brands, (SUM(quantity)* unit_price) AS sales_revenue 
  FROM  csv_table
   WHERE years = '2019' AND countries = 'Nigeria'
    GROUP BY csv_table.brands, unit_price
     ORDER BY (SUM(quantity)* unit_price) DESC LIMIT 1 
     
 ----favourite brands in south_south region in nigeria
 
SELECT brands, SUM(quantity) AS favourite
 FROM csv_table
  WHERE region = 'southsouth' 
  AND countries = 'Nigeria'
 GROUP BY brands
  ORDER BY SUM(quantity) DESC LIMIT 1
  
---- Beer consumption in nigeria

SELECT SUM(quantity) AS consumed_quantity
 FROM csv_table
  WHERE countries = 'Nigeria' 
  AND brands NOT LIKE '%malt' 

----level of consumption of budweiser in the regions in nigeria
SELECT region, SUM(quantity) AS level_consumed
 FROM csv_table
  WHERE countries = 'Nigeria'
  AND brands= 'budweiser'
 GROUP BY region

---level of consumption of budweiser in the regions in nigeria in 2019

SELECT region, SUM(quantity) AS level_consumed
 FROM csv_table
  WHERE countries = 'Nigeria'
  AND brands= 'budweiser' AND years = '2019'
 GROUP BY region

----        SESSION C (COUNTRIES ANALYSIS)
----- country with the highest consumption of beer

SELECT MAX(quantity) AS highest_consumed, countries
 FROM csv_table
  WHERE brands NOT LIKE '%malt'
   GROUP BY countries
    ORDER BY MAX(quantity) DESC LIMIT 1

---- highest sales personnel of budweiser in senegal

SELECT sales_rep, MAX(quantity) AS quantity_sold
 FROM csv_table
  WHERE brands = 'budweiser'
  AND countries = 'Senegal'
 GROUP BY sales_rep 
  ORDER BY MAX(quantity) DESC LIMIT 1

-----country with the highest profit in the fourth quarter in 2019

SELECT MAX(profit) AS highest_profit, countries
 FROM csv_table
  WHERE months IN ('October', 'November', 'December') 
  AND years = 2019
 GROUP BY countries
  ORDER BY MAX(profit) DESC LIMIT 1 

