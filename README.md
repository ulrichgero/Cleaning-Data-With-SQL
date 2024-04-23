# sort-data-with-sql

This project is to help the local to understand where to invest more and which crops categories sell more so they can improve the harvest time and given area.

## List of task to accomplish
- Get the data in CSV file
- Analyse the columns
- Filter and select main columns
- Sort the data by categories
	+ consolidate the unit production into one.
	+ Put Products into different categories
- Limit by the first 20 Item
- What Element has been product more?
- How many unique products where cultivate by ha?
- 

### The Data
The data I'm going to use is from FAO (Food and Agriculture Organization) website where I downloaded a CSV file of Crops and livestock products, especially for Africa.
### Analyse Columns
After importing the data into my SQL tool, I'm going to get all the from a specific country, in this case, the one for Republic of Benin.

```sql
SELECT *
FROM Product_Crops_E_Africa
WHERE Area = 'Benin';
```

### Filtering Data
To understand my data and do a proper research, I'll use main columns that contains important data. 
I'm filtering data to show the *product*, *unit* and the *year*
 
```sql
select Item AS Product, Unit, Y2019 
from Production_Crops_E_Africa
where Area = 'Benin'
Group by Item, Unit, Y2019;
```

Now let calculate the average of production in year 2019

```sql
select Item AS Product, Unit, AVG(Y2019) 
from Production_Crops_E_Africa
where Area = 'Benin'
Group by Item, Unit, Y2019;
```

#### Sorting by the Unit
Now let sort by a unique Unit of production, and in this, I'll focus on the tonnes of product harvest in year 2019.

```sql
select Item AS Product, Unit, AVG(Y2019) 
from Production_Crops_E_Africa
where Area = 'Benin'
AND Unit ='tonnes'
Group by Item, Unit, Y2019;
```
