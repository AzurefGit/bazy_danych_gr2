# nagłówek 1
## nagłówek 2
###### nagłówek 6

Tekst **pogrubiony** lub _kursywa_


**Zadanie 1, pkt. 1**
```sql
SELECT * FROM osoba;
 create table postac( id_postaci int auto_increment primary key, nazwa varchar(40), rodzaj enum('wiking','ptak','kobieta'), data_ur date, wiek int unsigned);


create table walizka( id_walizki int auto_increment primary key,
pojemnosc int unsigned,
kolor enum('rozowy','czerwony','teczowy','zolty'),
id_wlasciciela int,
foreign key(id_wlasciciela) references postac(id_postaci) on delete cascade);
```
```python
def funkcja():
  print('a')
```
Polecenie `SELECT` służy wybieraniu danych z tabeli  
lista ponumerowana
1. Punkt 1.
2. Punkt 2.  
2.1. Punkt 2.1

lista wypunktowana
* punkt 1
* punkt 2  
  * punkt 2.1
