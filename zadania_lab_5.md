**Zadanie 1**
*Podpunkt a)*
```sql
delete from postac where rodzaj = 'wiking' and wiek and nazwa != 'Bjorn';
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

```
