**Zadanie 1**

*Podpunkt a)*
```sql
delete from postac where rodzaj = 'wiking' and nazwa <> 'Bjorn' order by data_ur asc limit 2;
# eventualnie 
delete * from postac
where nazwa <> 'Bjorn'
and rodzaj = 'wiking'
order by data_ur asc limit 2;
```
*Podpunkt b)*
```sql
#krok 1 usunięcie kluczy obcych 

alter table walizka
drop foreign key walizka_ibfk_1;

alter table przetwory
drop foreign key przetwory_ibfk_1;

alter table przetwory
drop foreign key przetwory_ibfk_2;

#krok 2 usunięcie klucza głównego

alter table postac change
id_postaci id_postaci int;
alter table postac modify
id_postaci int;
```

**Zadanie 2**

*Podpunkt a)*
```sql
alter table postac
add column pesel char(11)first;
update postac set pesel='01234567890' + id_postaci;
```
*Podpunkt b)*
```sql
alter table postac modify rodzaj enum('wiking','ptak','kobieta','syrena');
```
*Podpunkt c)*
```sql
insert into postac values(11234567812,10,'Gertruda Nieszczera','syrena','1888-09-21',165,NULL,NULL);
```

**Zadanie 3**

*Podpunkt a)*
```sql
update postac set nazwa_statku = 'SS Stone'
where nazwa like '%a%'; 
```
*Podpunkt b)*
```sql
# mozna between '1901-01-01' and '2000-12-31' lub select year(data_wodowania) from statek z between i zmienic na lata
update statek set max_ladownosc = max_ladownosc * 0.7
where data_wodowania >= '1901-01-01' and data_wodowania <= '2000-12-31';
```
*Podpunkt c)*
```sql
alter table postac add check(wiek < 1000);
```

**Zadanie 4**

*Podpunkt a)*
```sql
#modyfikacja typu
alter table postac modify rodzaj enum('wiking','ptak','kobieta','syrena','wąż');
#dodanie weza
insert into postac values('65482068251',11,'Loko','wąż','2018-03-20',5,NULL,NULL);
```
*Podpunkt b)*
```sql

```

ciekawostki:
```sql
# where nazwa not regexp '^d' 'a$' '^[a-f]' '^[aeiz]' '^[0-9]' '^[^0-9]' kod pocztowy('[0-9]{2}-[0-9]{3})<-ilosc';
# % = dowolny ciag
# _ = jeden znak
# check(warunek) mozna dac przy tworzeniu tab
```
