Fuel Price, How many KMs can your car go if you buy fuel by $100?

It depends on: 1- Price/Liter where you drive, 2- fuel consumption Liters/100KM.

Back to the automation: getting the data (country | price) as table doesn't work, so how do you get them and calculate the distance:

1- Take the fuel consumption rate per 100KM

2- Use "Build Data Table" activity , build 2 tables as preparation for "TableExtraction" and create only one col call it ID and make it "auto increment".

3- Use "Table Extraction" twice, once for the country and once for the price and save the extracted data tables to the tables you prepared.

4- Now you have 2 cols in each table, the ID and the country or price in a way that makes the ID matches in the 2 tables so:

5- Join the 2 tables on ID

Now you have to calculate the KMs for $100 and put it to excel with the country and price.

6- Use "For Each Row in DataTable" and for each country and price in the joined table: calculate distance and add the 3 of them to a new table:

{currentRow(CountryColIndex), currentRow(PriceColIndex), distance}

distance = math.Round((((100/Convert.ToDouble(CurrentRow(PriceColIndex)))*100)/Convert.ToDouble(FuelConsumption)),2).ToString
