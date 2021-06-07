# sql

Izpiši podatek Name iz tabele Artist z SQL ukazom (za vse vnose v tej tabeli):
SELECT Artist.Name
FROM Artist

Izpiši vse podatke iz tabele Invoice, kjer je BillingCountry Nemčija (Germany):
SELECT *
FROM Invoice
WHERE Invoice.BillingCountry='Germany'

Preštej koliko je vseh albumov v podatkovni bazi:
SELECT COUNT(*)
FROM Album

Koliko strank (Customer) je iz Francije:
SELECT count(*)
FROM Customer
WHERE customer.Country='France'

Kaj je vsota vseh računov (polj Total) v bazi:
SELECT sum(Invoice.total)
FROM Invoice

Kolikšen je povprečen znesek računa:
SELECT avg(Invoice.total)
FROM Invoice



