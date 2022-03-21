# 1. Greenest City Project - Vancouver
At the beginning of 2009, Mayor Gregor Robertson assembled the Greenest City Action Team and threw down an audacious and exciting challenge: to develop a plan to make Vancouver the greenest city in the world by 2020. A decade-long effort to make Vancouver a greener place to live, work, and play. The city hit eight of 18 targets, and where it did not cross the finish line, it made significant progress in each of it 10 goals areas.

## 1.1 What this project will show?
With this project I will show where the main focus area was and also the top 5 locations.  What was the main category of projects being developed, the top 5 categories, and their location.

## 1.2 Why use SQL for this project?
Learning purpose only.

## 1.3 Import data file format
I choose CSV as a file format to import to pgAdmin, since this is the most common import and export format for databases. 

# 2. Importing data to pgAdmin

## 2.1 Creating the server
I opened pgAdmin right clicked on PostgreSQL under servers, clicked on create > Server. I gave a name to my server and hit save. 

## 2.2 Creating the table
I decided to create the table by running a code on the Query Tool, just by learning purpose.

``` sql
CREATE TABLE PUBLIC.green_projects(
	MAPID VARCHAR(50),
	NAME VARCHAR(50),
	CATEGORY1 VARCHAR(50),
	CATEGORY2 VARCHAR(50),
	ADDRESS TEXT,
	"Geo Local Area" VARCHAR(50)
	)
```
## 2.3 Importing the data
I decided to import by right click on my table name, select Import/Export. At file name I selected the file .CSV > format CSV > Header 'Yes' > Delimiter ',' > OK. 

# 3. Selecting the data for presentation
## 3.1 Started by Selecting the area with the most number of projects developed 
``` sql
SELECT "Geo Local Area" 
FROM green_projects
GROUP BY "Geo Local Area"
ORDER BY COUNT(*) DESC
LIMIT 1;
```
The result is: **Mount Pleasant**

## 3.2 Which category was the most developed
```sql
SELECT category2
FROM green_projects
GROUP BY category2
ORDER BY COUNT(*) DESC
LIMIT 1;
```
The Result is: **Local-Food**

### Top 5 categories
```sql
SELECT category2
FROM green_projects
GROUP BY category2
ORDER BY COUNT(*) DESC
LIMIT 5;
```
The result is: 
 1. **Local-Food**
 2. **Clean-Air**
 3. **Lighter-Footprint**
 4. **Green-Buildings**
 5. **Access-to-Nature**

## 3.4 Top 5 categories and their most developed location

---

### **1. Local-Food**
```sql
SELECT category2, "Geo Local Area"
FROM green_projects
WHERE category2 = 'Local-Food'
GROUP BY "Geo Local Area", category2
ORDER BY COUNT(*) DESC LIMIT 1
```
The result is: **Strathcona** with a total of 28 projects developed.

```sql
SELECT category2, "Geo Local Area"
FROM green_projects
WHERE category2 = 'Local-Food' AND "Geo Local Area" = 'Strathcona'
```
The result is a list containing **28** Local-Food projects in **Strathcona**

---

### **2. Clean-Air**
```sql
SELECT category2, "Geo Local Area"
FROM green_projects
WHERE category2 = 'Clean-Air'
GROUP BY "Geo Local Area", category2
ORDER BY COUNT(*) DESC LIMIT 1
```
The result is: **Downtown** with a total of 14 projects developed.
```sql
SELECT category2, "Geo Local Area"
FROM green_projects
WHERE category2 = 'Clean-Air' AND "Geo Local Area" = 'Downtown'
```
The result is a list containing **14** Clean-Air projects in **Downtown**

---

### **3. Lighter-Footprint**
```sql
SELECT category2, "Geo Local Area"
FROM green_projects
WHERE category2 = 'Lighter-Footprint'
GROUP BY "Geo Local Area", category2
ORDER BY COUNT(*) DESC LIMIT 1
```
The result is: **Riley Park** with a total of 7 projects developed.
```sql
SELECT category2, "Geo Local Area"
FROM green_projects
WHERE category2 = 'Lighter-Footprint' AND "Geo Local Area" = 'Riley Park'
```
The result is a list containing **7** Lighter-Footprint projects in **Riley Park**

---

### **4. Green-Buildings**
```sql
SELECT category2, "Geo Local Area"
FROM green_projects
WHERE category2 = 'Green-Buildings'
GROUP BY "Geo Local Area", category2
ORDER BY COUNT(*) DESC LIMIT 1
```
The result is: **Mount Pleasant** with a total of 12 projects developed.

```sql
SELECT category2, "Geo Local Area"
FROM green_projects
WHERE category2 = 'Green-Buildings' AND "Geo Local Area" = 'Mount Pleasant'
```
The result is a list containing **12** Green-Buildings projects in **Mount Pleasant**

---

### **5. Access-to-Nature**
```sql
SELECT category2, "Geo Local Area"
FROM green_projects
WHERE category2 = 'Access-to-Nature'
GROUP BY "Geo Local Area", category2
ORDER BY COUNT(*) DESC LIMIT 1
```
The result is: **Fairview** with a total of  projects developed.
```sql
SELECT category2, "Geo Local Area"
FROM green_projects
WHERE category2 = 'Access-to-Nature' AND "Geo Local Area" = 'Fairview'
```
The result is a list containing **4** Access-to-Nature projects in **Fairview**

---