# sql

Izpiši podatek Name iz tabele Artist z SQL ukazom (za vse vnose v tej tabeli):
```sql
SELECT Artist.Name
FROM Artist
```

Izpiši vse podatke iz tabele Invoice, kjer je BillingCountry Nemčija (Germany):
```sql
SELECT *
FROM Invoice
WHERE Invoice.BillingCountry='Germany'
```

Preštej koliko je vseh albumov v podatkovni bazi:
```sql
SELECT COUNT(*)
FROM Album
```

Koliko strank (Customer) je iz Francije:
```sql
SELECT count(*)
FROM Customer
WHERE customer.Country='France'
```

Kaj je vsota vseh računov (polj Total) v bazi:
```sql
SELECT sum(Invoice.total)
FROM Invoice
```

Kolikšen je povprečen znesek računa:
```sql
SELECT avg(Invoice.total)
FROM Invoice
```

Kateri nakup je bil najdražji?
```sql
SELECT max(Invoice.total), *
FROM Invoice
```

Najcenejsi?
```sql
SELECT min(Invoice.total), *
FROM Invoice
```

V katerem mestu je bilo največ nakupov?
```sql
SELECT Invoice.BillingCity, count(*) as most_city
FROM Invoice
GROUP BY Invoice.BillingCity
ORDER BY most_city DESC
```

Izračunaj oziroma preštej, koliko skladb (Track) je tipa (MediaType) Protected AAC audio file
```sql
SELECT count(*)
FROM Track
INNER JOIN MediaType on Track.MediaTypeId=MediaType.MediaTypeId
WHERE MediaType.Name='Protected AAC audio file'
```

Ugotovi, kateri izvajalec (Artist) ima največ albumov.
```sql
SELECT Artist.Name, count (*) as biggest
FROM Artist
INNER JOIN Album on Album.ArtistId=Artist.ArtistId
GROUP BY Album.ArtistId
ORDER BY biggest DESC
```

Kateri žanr (Genre) ima največ skladb (Track)?
```sql
SELECT Genre.Name, count (*)	
FROM Genre
INNER JOIN Track on Track.GenreId=Genre.GenreId
GROUP BY Track.GenreId
```

Kateri kupec je do sedaj v trgovini zapravil največ?
```sql
SELECT Customer.FirstName, Customer.LastName, sum(Invoice.total) as customer_total
FROM Customer
INNER JOIN Invoice on Invoice.CustomerId=Customer.CustomerId
GROUP BY Invoice.CustomerId
ORDER BY customer_total DESC;
```

Izpiši vse račune in katere pesmi so bile kupljene na posameznem računu (namig: tu narediš many-to-many SQL query in sicer s tremi tabelami, Track, Invoice in InvoiceLine.
```sql
SELECT Invoice.InvoiceId, Track.Name
FROM Invoice
JOIN InvoiceLine ON InvoiceLine.InvoiceId = Invoice.InvoiceId
JOIN Track ON InvoiceLine.TrackId = Track.TrackId;
```

Kateri kupci porabijo več denarja - tisti ki delajo za neko firmo, ali tisti, ki ne
-ki ne delajo

Za vsako izmed teh dveh vrst kupcev naredi svojo SQL poizvedbo ter primerjaj dobljeni vrednosti
```sql
SELECT sum(Invoice.total) as customer_total
FROM Customer
INNER JOIN Invoice on Invoice.CustomerId=Customer.CustomerId
WHERE Customer.Company is NOT NULL
ORDER BY customer_total DESC;
```
```sql
SELECT sum(Invoice.total) as customer_total
FROM Customer
INNER JOIN Invoice on Invoice.CustomerId=Customer.CustomerId
WHERE Customer.Company is NULL
ORDER BY customer_total DESC;
```




