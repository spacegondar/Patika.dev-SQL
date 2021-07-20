# Patika.dev.sql

## Ödev 1

#### 1.Film tablosunda bulunan title ve description sütunlarındaki verileri sıralayınız.
```
--1.1 Soru
SELECT title, description
FROM film;
```

#### 2.Film tablosunda bulunan tüm sütunlardaki verileri film uzunluğu (length) 60 dan büyük VE 75 ten küçük olma koşullarıyla sıralayınız.
```
--1.2 Soru
SELECT *
FROM film
WHERE length > 60 AND length < 75;
```

#### 3.Film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99 VE replacement_cost 12.99 VEYA 28.99 olma koşullarıyla sıralayınız.
```
--1.3 Soru
SELECT *
FROM film
WHERE rental_rate = 0.99 AND (replacement_cost = 12.99 OR replacement_cost = 28.99);
```

#### 4.Customer tablosunda bulunan first_name sütunundaki değeri 'Mary' olan müşterinin last_name sütunundaki değeri nedir?
```
--1.4 Soru(Smith)
SELECT last_name
FROM customer
WHERE first_name = 'Mary'
```

#### 5.Film tablosundaki uzunluğu(length) 50 ten büyük OLMAYIP aynı zamanda rental_rate değeri 2.99 veya 4.99 OLMAYAN verileri sıralayınız.
```
--1.5 Soru
SELECT *
FROM film
WHERE NOT (length > 50 OR rental_rate = 2.99 OR rental_rate = 4.99 );
```

## Ödev 2

#### 1.Film tablosunda bulunan tüm sütunlardaki verileri replacement cost değeri 12.99 dan büyük eşit ve 16.99 küçük olma koşuluyla
```
--2.1 Soru
SELECT * 
FROM film 
WHERE replacement_cost Between 12.99 AND 16.99;
```

#### 2. Actor tablosunda bulunan first_name ve last_name sütunlardaki verileri first_name 'Penelope' veya 'Nick' veya 'Ed' değerleri olması
```
--2.2 Soru
SELECT first_name, last_name
FROM actor 
WHERE first_name IN('Penelope', 'Ed', 'Nick');
```

#### 3. film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99, 2.99, 4.99 VE replacement_cost 12.99, 15.99, 28.99 olma koşullarıyla sıralayınız.
```
--2.3 Soru
SELECT *
FROM film
WHERE (rental_rate IN(0.99,2.99,4.99)) AND (replacement_cost IN(12.99,15.99,28.99))
```

## Ödev 3

#### 1.Country tablosunda bulunan country sütunundaki ülke isimlerinden 'A' karakteri ile başlayıp 'a' karakteri ile sonlananları sıralayınız.
```
--3.1 Soru
SELECT country
FROM country
WHERE country LIKE 'A%a';
```

#### 2.Country tablosunda bulunan country sütunundaki ülke isimlerinden en az 6 karakterden oluşan ve sonu 'n' karakteri ile sonlananları sıralayınız.
```
--3.2 Soru
SELECT country
FROM country
WHERE country LIKE '%_____n';
```

#### 3.Film tablosunda bulunan title sütunundaki film isimlerinden en az 4 adet büyük ya da küçük harf farketmesizin 'T' karakteri içeren
```
--3.3 Soru
SELECT  title
FROM film
WHERE title ILIKE '%T%T%T%T%';
```

#### 4.Film tablosunda bulunan tüm sütunlardaki verilerden title 'C' karakteri ile başlayan ve uzunluğu (length) 90 dan büyük olan ve rental_rate 2.99 olan verileri sıralayınız.
```
--3.4 Soru
SELECT *
FROM film
WHERE title ILIKE 'C%' AND length > 90 AND rental_rate = 2.99;
```

## Ödev 4

#### 1.Film tablosunda bulunan replacement_cost sütununda bulunan birbirinden farklı değerleri sıralayınız.
```
--4.1 Soru
SELECT DISTINCT(replacement_cost)
FROM film
ORDER BY replacement_cost ASC;
```

#### 2.Film tablosunda bulunan replacement_cost sütununda birbirinden farklı kaç tane veri vardır?
```
--4.2 Soru
SELECT COUNT(DISTINCT(replacement_cost))
FROM film;
```

#### 3.Film tablosunda bulunan film isimlerinde (title) kaç tanesini T karakteri ile başlar ve aynı zamanda rating 'G' ye eşittir?
```
--4.3 Soru
SELECT COUNT(title)
FROM film
WHERE title ILIKE 'T%' AND rating = 'G';
```

#### 4.Country tablosunda bulunan ülke isimlerinden (country) kaç tanesi 5 karakterden oluşmaktadır?
```
--4.4 Soru
SELECT COUNT(*)
FROM country 
WHERE country ILIKE '_____';
```

#### 5.City tablosundaki şehir isimlerinin kaçtanesi 'R' veya r karakteri ile biter?
```
--4.5 Soru
SELECT COUNT(*)
FROM city
WHERE city ILIKE '%r';
```

## Ödev 5

#### 1.Film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en uzun (length) 5 filmi sıralayınız.
```
--5.1 Soru
SELECT title, length
FROM film
WHERE title LIKE '%n'
ORDER BY length DESC, title ASC
LIMIT 5;
```

#### 2.Film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en kısa (length) ikinci 5 filmi sıralayınız.
```
--5.2 Soru
SELECT title, length
FROM film
WHERE title LIKE '%n'
ORDER BY length ASC, title ASC
OFFSET 5
LIMIT 5;
```

#### 3.Customer tablosunda bulunan last_name sütununa göre azalan yapılan sıralamada store_id 1 olmak koşuluyla ilk 4 veriyi sıralayınız.
```
--5.3 Soru
SELECT *
FROM customer
WHERE store_id = 1
ORDER BY last_name DESC
LIMIT 4;
```

## Ödev 6

#### 1.Film tablosunda bulunan rental_rate sütunundaki değerlerin ortalaması nedir?
```
--6.1 Soru
SELECT ROUND(AVG(length),4) AS Ortalama
FROM film;
```

#### 2.Film tablosunda bulunan filmlerden kaçtanesi 'C' karekteri ile başlar?
```
--6.2 Soru
SELECT COUNT(*)
FROM film
WHERE title LIKE 'C%'
```

#### 3.Film tablosunda bulunan filmlerden rental_rate değeri 0.99 a eşit olan en uzun (length) film kaç dakikadır?
```
--6.3 Soru(184)
SELECT MAX(length)
FROM film
WHERE rental_rate = 0.99
```

#### 4.Film tablosunda bulunan filmlerin uzunluğu 150 dakikadan büyük olanlarına ait kaç farklı replacement_cost değeri vardır?
```
--6.4 Soru(21)
SELECT COUNT(DISTINCT replacement_cost)
FROM film
WHERE length > 150
```


