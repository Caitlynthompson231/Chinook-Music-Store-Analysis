<h1>Chinook Music Store Business Analysis 
  </h6>
  
**Author**: Caitlyn Thompson  
**Email**: caitynthompsonsql@gmail.com  
**LinkedIn**: www.linkedin.com/in/caitlynthompsonsql  
**Website**: https://caitlynthompson231.github.io/CaitlynThompson.github.io/  
  
  
<h2>Questions and Answers  
  <h6></h6>  
  
1. _How many tracks are sold in each genre?_  
````sql  
SELECT GEN.name AS Genre, COUNT(*) AS TracksSold
FROM chinook.genres GEN
JOIN chinook.tracks TRA ON GEN.GenreId = TRA.GenreId
JOIN chinook.invoice_items ITM ON TRA.TrackId = ITM.TrackId
GROUP BY Genre
ORDER BY TracksSold DESC;
````  
**Results:**  


| Genre  | TracksSold |
| :----: | :--------: | 
Rock	 |   835
Latin	    |386
Metal	    |264
Alternative & Punk	|244
Jazz	|80
Blues	|61
TV Shows	|47
R&B/Soul	|41
Classical	|41
Reggae	|30
Drama	|29
Pop	|28
Soundtrack	|20
Sci Fi & Fantasy	|20
Hip Hop/Rap	|17
Bossa Nova	|15
Alternative	|14
World	|13
Heavy Metal|	12
Electronica/Dance|	12
Easy Listening	|10
Comedy	|9
Science Fiction|	6
Rock And Roll	|6
  
<h4>What are we looking at?  
  <h6></h6>  
  
  In this query we present an assessment on the volume of tracks sold per genre within the database using a structured JOIN operation to gather data from 3 different tables and we rely on an aggregated function that effectivey quantifies the number of tracks sold and finish with an order by statement to unveil the highest performing genres first 

2. _What is the percentage of tracks sold in the USA?_

````sql
SELECT GEN.name AS Genre,
      ROUND (COUNT(CASE WHEN CUS.Country = 'USA' THEN 1 ELSE NULL END) * 100.0 / COUNT(*)) AS PercentageSoldInUSA
FROM chinook.genres GEN
JOIN chinook.tracks TRA ON GEN.GenreId = TRA.GenreId
JOIN chinook.invoice_items ITM ON TRA.TrackId = ITM.TrackId
JOIN chinook.invoices INV ON ITM.InvoiceId = INV.InvoiceId
JOIN chinook.customers CUS ON INV.CustomerId = CUS.CustomerId
GROUP BY Genre
ORDER BY PercentageSoldInUSA DESC;
````
  
**Results:**
| Genre | PercentageSoldInUSA |
| :---: | :-----------------: |
Comedy|	89
Rock And Roll|	50
Bossa Nova	|47
Alternative	|36
Heavy Metal	|33
TV Shows	|30
Easy Listening	|30
R&B/Soul	|29
Jazz	|28
Sci Fi & Fantasy	|25
Blues	|25
Metal	|24
Latin	|24
Hip Hop/Rap	|24
Drama	|21
Soundtrack	|20
Reggae	|20
Classical	|20
Alternative & Punk	|20
Rock	|19
Pop	|18
Science Fiction	|17
World	|0
Electronica/Dance|	0
  
  
<h4>What are we looking at?  
  <h6></h6>  
  
In this query we present an assesment in the volume of tracks sold per genre from the United States and this time by percent instead of absolute numbers. This can help us get a better understanding of which genre's are the highest selling, which is a starting point to answer which artists should purchased to go in the Chinook Music store. So now we will figure out which artists are the top 3 highest selling so we can make an educated choice.
  
3. _What are the top 3 selling artists based off of their track sales?_ 
  
  
````sql
SELECT
    GEN.name AS Genre,
    ART.Name AS Artist,
    TRK.name AS 'Song Title',
    ALB.Title AS Album,
    COUNT(ITM.TrackId) AS 'Tracks Sold'
FROM
    chinook.genres AS GEN
LEFT JOIN chinook.tracks AS TRK ON GEN.GenreId = TRK.GenreId
LEFT JOIN chinook.albums AS ALB ON TRK.AlbumId = ALB.AlbumId
LEFT JOIN chinook.artists AS ART ON ALB.ArtistId = ART.ArtistId
LEFT JOIN chinook.invoice_items AS ITM ON TRK.TrackId = ITM.TrackId
WHERE
    ITM.TrackId IS NOT NULL
GROUP BY Genre, Artist, 'Song Title', Album
ORDER BY COUNT(ITM.TrackId) DESC;
````
  
**Results:**
  
| Genre | Artist     | Song Title                     |Album| Tracks Sold |
| :---: | :---------:| :----:|  :-----------------------------:| :----------:|
|Latin	|Chico Buarque  |Vai Passar| Minha Historia              |	27         |
|Alternatice & Punk|Titas  	 | Comida|	Acustico| 22          |
|Rock	|Kiss| Black Diamond     |	Greatest Kiss |20          |
  

_What are we looking at?_
  
 This SQL query is designed to compile a comprehensive and organized dataset that showcases the top-selling artists within the Chinook music store based on track sales.This query serves as a valuable tool for making informed decisions regarding potential album acquisitions for the Chinook store, offering a consolidated overview of the top 3 performing artists and their respective track sales data

