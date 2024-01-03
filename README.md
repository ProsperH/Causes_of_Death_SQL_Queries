# Causes-of-Death

This analysis investigates patterns in causes of death across multiple countries over three decades. The dataset contains information solely on death causes, death numbers, countries, and respective years.

### Renaming a column

EXEC sp.rename 'Causes Of Death.Entity', 'Country', 'COLUMN'


### Replacing values
UPDATE [Causes Of Death]
SET Country = 
    CASE 
        WHEN Country = 'United States' THEN 'United States of America'
        ELSE Country
    END
WHERE Country = 'United States';

UPDATE [Causes Of Death]
SET Country = 
    CASE 
        WHEN Country = 'America' THEN 'United States of America'
        ELSE Country
    END
WHERE Country = 'America';



### KPIs
![](KPI_C.png)


### Year with the highest number of deaths
![](Most_Year.png)


### Year with the least number of deaths
![](Least_Year.png)


### Leading Causes of Death
![](Leading_Causes.png)


### Leading death cause in 2019
![](CVD_19.png)


### Leading death cause in 1990
![](CVD_90.png)


### Top 5 countries affected by Cardiovascular diseases in 2019
![](Countries1.png)


### Top 5 countries affected by Cardiovascular diseases in 1990
![](Countries2.png)














