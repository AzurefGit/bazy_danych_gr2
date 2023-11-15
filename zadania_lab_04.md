*Zadanie 1*
```sql
SELECT * FROM osoba;
create table postac( id_postaci int auto_increment primary key, nazwa varchar(40), rodzaj enum('wiking','ptak','kobieta'), data_ur date, wiek int unsigned);
```

*Zadanie 2*

```sql
*Zadanie 1*
create table walizka( id_walizki int auto_increment primary key,
pojemnosc int unsigned,
kolor enum('rozowy','czerwony','teczowy','zolty'),
id_wlasciciela int,
foreign key(id_wlasciciela) references postac(id_postaci) on delete cascade);
```
