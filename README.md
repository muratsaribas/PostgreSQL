# PostgreSQL

### ÖDEV1
- **film** tablosunda bulunan **title** ve **description** sütunlarındaki verileri sıralayınız.
``` sql
	SELECT title, description FROM film 
```
 - **film** tablosunda bulunan tüm sütunlardaki verileri film uzunluğu (length) 60 dan büyük **VE** 75 ten küçük olma koşullarıyla sıralayınız.
``` sql
	SELECT * FROM film 
	WHERE length > 60 AND length < 75 
```
 - **film** tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99 **VE** replacement_cost 12.99 **VEYA** 28.99 olma koşullarıyla sıralayınız.
``` sql
	SELECT * FROM film 
	WHERE rental_rate = 0.99 AND (replacement_cost = 12.99 OR replacement_cost = 28.99) 
```
 - **customer** tablosunda bulunan first_name sütunundaki değeri 'Mary' olan müşterinin last_name sütunundaki değeri nedir?
``` sql
	SELECT last_name from customer
	WHERE first_name = 'Mary' 
```
 - **film** tablosundaki uzunluğu(length) 50 ten büyük OLMAYIP aynı zamanda rental_rate değeri 2.99 veya 4.99 OLMAYAN verileri sıralayınız.
``` sql
	SELECT * FROM film 
	WHERE NOT length > 50 AND NOT (rental_rate = 2.99 OR rental_rate = 4.99) 
```

### ÖDEV2

- **film** tablosunda bulunan tüm sütunlardaki verileri replacement_cost değeri 12.99 dan büyük eşit ve 16.99 küçük olma koşuluyla sıralayınız ( BETWEEN - AND yapısını kullanınız.)
``` sql
	SELECT * FROM film 
	WHERE replacement_cost BETWEEN 12.99 AND 16.98 
```
 - **actor** tablosunda bulunan first_name ve last_name sütunlardaki verileri first_name 'Penelope' veya 'Nick' veya 'Ed' değerleri olması koşuluyla sıralayınız. ( IN operatörünü kullanınız.)
``` sql
	SELECT first_name, last_name FROM actor
	WHERE first_name IN ('Penelope', 'Nick', 'Ed') 
```
 - **film** tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99, 2.99, 4.99 **VE** replacement_cost 12.99, 15.99, 28.99 olma koşullarıyla sıralayınız. ( IN operatörünü kullanınız.)
``` sql
	SELECT * FROM film 
	WHERE rental_rate IN (0.99, 2.99, 4.99) 
	AND replacement_cost IN (12.99, 15.99, 28.99)
```

### ÖDEV3
- **country** tablosunda bulunan **country** sütunundaki ülke isimlerinden 'A' karakteri ile başlayıp 'a' karakteri ile sonlananları sıralayınız.
``` sql
	SELECT * FROM country
	WHERE country LIKE 'A%a'
```
 - **country** tablosunda bulunan **country** sütunundaki ülke isimlerinden en az 6 karakterden oluşan ve sonu 'n' karakteri ile sonlananları sıralayınız.
``` sql
	SELECT * FROM country
	WHERE country LIKE '_____%n'
```
 - **film** tablosunda bulunan **title** sütunundaki film isimlerinden en az 4 adet büyük ya da küçük harf farketmesizin 'T' karakteri içeren film isimlerini sıralayınız.
``` sql
	SELECT title FROM film
	WHERE title ILIKE '%t%t%t%t%'
```
 - **film** tablosunda bulunan tüm sütunlardaki verilerden **title** 'C' karakteri ile başlayan ve uzunluğu (length) 90 dan büyük olan ve rental_rate 2.99 olan verileri sıralayınız.
``` sql
	SELECT * FROM film
	WHERE title LIKE 'C%' AND length > 90 AND rental_rate = 2.99
```
### ÖDEV4
- **film** tablosunda bulunan **replacement_cost** sütununda bulunan birbirinden farklı değerleri sıralayınız.
``` sql
	SELECT DISTINCT replacement_cost FROM film
```
 - **film** tablosunda bulunan **replacement_cost** sütununda birbirinden farklı kaç tane veri vardır?
``` sql
	SELECT * FROM film
	WHERE title LIKE 'C%' AND length > 90 AND rental_rate = 2.99
```
 - **film** tablosunda bulunan film isimlerinde (title) kaç tanesini T karakteri ile başlar ve aynı zamanda rating 'G' ye eşittir?
``` sql
	SELECT COUNT(DISTINCT replacement_cost) FROM film
```
 - **country** tablosunda bulunan ülke isimlerinden (country) kaç tanesi 5 karakterden oluşmaktadır?
``` sql
	SELECT COUNT(*) FROM country
	WHERE country LIKE '_____'
```
 - **city** tablosundaki şehir isimlerinin kaç tanesi 'R' veya r karakteri ile biter?
``` sql
	SELECT COUNT(*) FROM city
	WHERE city ILIKE '%r'
```
 ### ÖDEV5
- **film** tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en uzun (length) 5 filmi sıralayınız.
``` sql
	SELECT * FROM film
	WHERE title LIKE '%n'
	ORDER BY length DESC
	LIMIT 5
```
 - **film** tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en kısa (length) ikinci 5 filmi sıralayınız.
``` sql
	SELECT * FROM film
	WHERE title LIKE '%n'
	ORDER BY length ASC
	OFFSET 5
	LIMIT 5
```
 - **customer** tablosunda bulunan last_name sütununa göre azalan yapılan sıralamada store_id 1 olmak koşuluyla ilk 4 veriyi sıralayınız.
``` sql
	SELECT * FROM customer
	WHERE store_id = 1
	ORDER BY last_name DESC
	LIMIT 4
```
### ÖDEV6
- **film** tablosunda bulunan **rental_rate** sütunundaki değerlerin ortalaması nedir?
``` sql
	SELECT AVG(rental_rate) FROM film
```
 - **film** tablosunda bulunan filmlerden kaçtanesi 'C' karekteri ile başlar?
``` sql
	SELECT COUNT(*) FROM film
	WHERE title LIKE 'C%'
```
 - **film** tablosunda bulunan filmlerden rental_rate değeri 0.99 a eşit olan en uzun (length) film kaç dakikadır?
``` sql
	SELECT MAX(length) FROM film
	WHERE rental_rate = 0.99
```
 - **film** tablosunda bulunan filmlerin uzunluğu 150 dakikadan büyük olanlarına ait kaç farklı replacement_cost değeri vardır?
``` sql
	SELECT COUNT(DISTINCT replacement_cost) FROM film
	WHERE length > 150
```
 ### ÖDEV7
 - **film** tablosunda bulunan filmleri **rating** değerlerine göre gruplayınız.
``` sql
	SELECT rating, COUNT(*) FROM film
	GROUP BY rating
```
 - **film** tablosunda bulunan filmleri **replacement_cost** sütununa göre grupladığımızda film sayısı 50 den fazla olan replacement_cost değerini ve karşılık gelen film sayısını sıralayınız.
``` sql
	SELECT replacement_cost, COUNT(*) FROM film
	GROUP BY replacement_cost
	HAVING COUNT(*) > 50
```
 - **customer** tablosunda bulunan store_id değerlerine karşılık gelen müşteri sayılarını nelerdir?
``` sql
	SELECT store_id, COUNT(customer_id) FROM customer
	GROUP BY store_id
```
 - **city** tablosunda bulunan şehir verilerini **country_id** sütununa göre gruplandırdıktan sonra en fazla şehir sayısı barındıra country_id bilgisini ve şehir sayısını paylaşınız.
``` sql
	SELECT country_id, COUNT(city) FROM city
	GROUP BY country_id
	ORDER BY COUNT(city) DESC
	LIMIT 1
```
 ### ÖDEV8
 - **test** veritabanınızda **employee** isimli sütun bilgileri id(INTEGER), name VARCHAR(50), birthday DATE, email VARCHAR(100) olan bir tablo oluşturalım.
``` sql
	CREATE TABLE employee (
	id INTEGER,
	name VARCHAR(50),
	birthday DATE,
	email VARCHAR(100)
	);
```
 - Oluşturduğumuz **employee** tablosuna 'Mockaroo' servisini kullanarak 50 adet veri ekleyelim.
``` sql
	insert into employee (id, name, birthday, email) values (1, 'Augustine Blaksley', '1929-03-25', 'ablaksley0@tiny.cc'); 
	insert into employee (id, name, birthday, email) values (2, 'Kelley Tomson', '1938-02-15', 'ktomson1@about.com'); 
	insert into employee (id, name, birthday, email) values (3, 'Ashlie Attwool', '1940-07-28', 'aattwool2@mlb.com'); 
	insert into employee (id, name, birthday, email) values (4, 'Aymer Street', '1952-05-09', 'astreet3@dmoz.org'); 
	insert into employee (id, name, birthday, email) values (5, 'Euphemia Mathes', '1950-08-29', 'emathes4@narod.ru'); 
	... 
```
 - Sütunların her birine göre diğer sütunları güncelleyecek 5 adet UPDATE işlemi yapalım.
``` sql
	UPDATE employee
	SET	name = 'up date1',
		birthday = '2021-08-06',
		email = 'update1@up.date'
	WHERE id = 2;
```
 - Sütunların her birine göre ilgili satırı silecek 5 adet DELETE işlemi yapalım.
``` sql
	DELETE FROM employee
	WHERE id = 0;
```
### ÖDEV9
- **city** tablosu ile **country** tablosunda bulunan şehir (city) ve ülke (country) isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.
``` sql
	SELECT city.city, country.country FROM city
	INNER JOIN country ON city.country_id = country.country_id;
```
 - **customer** tablosu ile **payment** tablosunda bulunan payment_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.
``` sql
	SELECT payment.payment_id, customer.first_name, customer.last_name FROM customer
	INNER JOIN payment ON payment.customer_id = customer.customer_id;
```
 - **customer** tablosu ile **rental** tablosunda bulunan rental_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.
``` sql
	SELECT rental.rental_id, customer.first_name, customer.last_name FROM customer
	INNER JOIN rental ON rental.customer_id = customer.customer_id;
```
 ### ÖDEV10
 - **city** tablosu ile **country** tablosunda bulunan şehir (city) ve ülke (country) isimlerini birlikte görebileceğimiz LEFT JOIN sorgusunu yazınız.
``` sql
	SELECT city.city, country.country FROM city
	LEFT JOIN country ON city.country_id = country.country_id;
```
- **customer** tablosu ile **payment** tablosunda bulunan payment_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz RIGHT JOIN sorgusunu yazınız.
``` sql
	SELECT payment.payment_id, customer.first_name, customer.last_name FROM customer
	RIGHT JOIN payment ON payment.customer_id = customer.customer_id;
```
- **customer** tablosu ile **rental** tablosunda bulunan rental_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz FULL JOIN sorgusunu yazınız.
``` sql
	SELECT rental.rental_id, customer.first_name, customer.last_name FROM customer
	FULL JOIN rental ON rental.customer_id = customer.customer_id;
```
 ### ÖDEV11
- **actor** ve **customer** tablolarında bulunan **first_name** sütunları için tüm verileri sıralayalım.
``` sql
	(SELECT first_name FROM actor)
	UNION
	(SELECT first_name FROM customer)
	ORDER BY first_name;
```
- **actor** ve **customer** tablolarında bulunan **first_name** sütunları için kesişen verileri sıralayalım.
``` sql
	(SELECT first_name FROM actor)
	INTERSECT
	(SELECT first_name FROM customer)
	ORDER BY first_name;
```
- **actor** ve **customer** tablolarında bulunan **first_name** sütunları için ilk tabloda bulunan ancak ikinci tabloda bulunmayan verileri sıralayalım.
``` sql
	(SELECT first_name FROM actor)
	EXCEPT
	(SELECT first_name FROM customer)
	ORDER BY first_name;
```
### ÖDEV12
- **film** tablosunda film uzunluğu **length** sütununda gösterilmektedir. Uzunluğu ortalama film uzunluğundan fazla kaç tane film vardır?
``` sql
	SELECT COUNT(*) FROM film
	WHERE length >
	(SELECT AVG(length) FROM film);
```
- **film** tablosunda en yüksek rental_rate değerine sahip kaç tane film vardır?
``` sql
	SELECT COUNT(*) FROM film
	WHERE rental_rate =
	(SELECT MAX(rental_rate) FROM film);
```
- **film** tablosunda en düşük rental_rate ve en düşük replacement_cost değerlerine sahip filmleri sıralayınız.
``` sql
	SELECT * FROM film
	WHERE 
	rental_rate = (SELECT MIN(rental_rate) FROM film)
	AND 
	replacement_cost = (SELECT MIN(replacement_cost) FROM film)
```
- **payment** tablosunda en fazla sayıda alışveriş yapan müşterileri(customer) sıralayınız.
``` sql
	SELECT * FROM customer
	WHERE customer_id = 
	(
		SELECT customer_id FROM payment
		GROUP BY customer_id
		ORDER BY COUNT(customer_id) DESC
		LIMIT 1
	);
```