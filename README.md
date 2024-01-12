# Causes-of-Death

This analysis investigates patterns in causes of death across multiple countries over three decades. The dataset contains information solely on death causes, death numbers, countries, and respective years.

---
### Renaming a column

```EXEC sp.rename 'Causes Of Death.Entity', 'Country', 'COLUMN'```

---

### Replacing values
```
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
```

---

### KPIs
```
SELECT COUNT(DISTINCT Year) AS Years, COUNT(DISTINCT Country) AS Countries, 
		COUNT(DISTINCT Causes_name) AS Death_Causes, SUM(Death_Numbers) AS Deaths
FROM [Causes Of Death]
```
![](KPI_C.png)

---

### Year with the highest number of deaths
```
SELECT TOP 1 Year, SUM(Death_Numbers) AS Total_Deaths
FROM [Causes of Death]
GROUP BY Year
ORDER BY Total_Deaths DESC;
```
![](Most_Year.png)

---

### Year with the least number of deaths
```
SELECT TOP 1 Year, SUM(Death_Numbers) AS Total_Deaths 
FROM [Causes Of Death]
GROUP BY Year
ORDER BY Total_Deaths ASC;
```
![](Least_Year.png)

---

### Leading Causes of Death
```
SELECT TOP 5 Causes_name, SUM(Death_Numbers) AS Total_Deaths
FROM [Causes Of Death]
GROUP BY Causes_name
ORDER BY Total_Deaths DESC;
```
![](Leading_Causes.png)

---

### Leading death cause in 2019
```
SELECT TOP 1 Causes_name, SUM(Death_Numbers) AS Total_Deaths
FROM [Causes Of Death]
WHERE Year = 2019
GROUP BY Causes_name
ORDER BY Total_Deaths DESC;
```
![](CVD_19.png)

---

### Leading death cause in 1990
```
SELECT TOP 1 Causes_name, SUM(Death_Numbers) AS Total_Deaths
FROM [Causes Of Death]
WHERE Year = 1990
GROUP BY Causes_name
ORDER BY Total_Deaths ASC;
```
![](CVD_90.png)

---

### Top 5 countries affected by Cardiovascular diseases in 2019
```
SELECT TOP 5 Country, SUM(Death_Numbers) total_deaths
FROM [Causes Of Death]
WHERE Year = 2019 AND Causes_name = 'Cardiovascular diseases'
GROUP BY Country 
ORDER BY total_deaths DESC;
```
![](Countries1.png)

---

### Top 5 countries affected by Cardiovascular diseases in 1990
```SELECT TOP 5 Country, SUM(Death_Numbers) total_deaths
FROM [Causes Of Death]
WHERE Year = 1990 AND Causes_name = 'Cardiovascular diseases'
GROUP BY Country 
ORDER BY total_deaths ASC;
```
![](Countries2.png)




_See Medium article [here](https://medium.com/@prosperherbert2015/analyzing-the-global-leading-cause-of-death-728380fcdf70?source=user_profile---------0----------------------------)_











