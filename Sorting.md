

### The Data
The data I'm going to use is from FAO (Food and Agriculture Organization) website where I downloaded a CSV file of Crops and livestock products, especially for Africa, then I renamed the file properly as faostat_data_2020. I added 2020 because the data I'm going to use is from that year.
### Analyse Columns
After importing the data into my SQL tool, I'm going to get all the from a specific country, in this case, the one for Republic of Benin.

```sql
SELECT *
FROM faostat_data_2020  --the table name
WHERE Area = 'Benin'; --- the country I'm going to analyse.
```

### Filtering Data
To understand my data and do a proper research, I'll use main columns that contains important data. 
I'm filtering data to show the *product*, *unit* and the *year*
 
```sql
select Item, Value, Unit, Year, Area
from faostat_data_2020
where Area = 'Benin'
Group by Item, Value, Unit, Year, Area;
```

#### Sorting by the Unit
Now let sort by a unique Unit of production, and in this, I'll focus on the tonnes of product harvest in year 2020.

```sql
select Item, Value, Unit, Year, Area 
from faostat_data_2020
where Area = 'Benin'
AND Unit ='t'
Group by Item, Value, Unit, Year, Area;
```

#### Filtering by Value
Since I'm sorting the data with value that must be greater than zero, I'll remove all other Items which value are lower than zero
```sql  
select Item, Value, Unit, Year, Area 
from faostat_data_2020
where Area = 'Benin'
AND Unit ='t'
AND Value > 0
Group by Item, Value, Unit, Year, Area;
```

#### Ordering by Value
 After removing the Items that got less value, It's time to order them by Value.
 I added the DESC keyword in the end because SQL displays the data in Ascend order by default but In my case, I want the opposite.
 ```sql  
 select Item, Value, Unit, Year, Area 
from faostat_data_2020
where Area = 'Benin'
AND Unit ='t'
AND Value > 0
Group by Item, Value, Unit, Year, Area
order by Value DESC;
 ```
