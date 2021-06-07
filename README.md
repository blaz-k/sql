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



