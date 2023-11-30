**Zadanie 1**

*Podpunkt a)*
```sql
#dodawanie tabel
create table ekwipunek like wikingowie.ekwipunek;
create table kreatura like wikingowie.kreatura;
create table zasob like wikingowie.zasob;
#dodawanie wartości ------------------------------------
insert into ekwipunek select * from wikingowie.ekwipunek;
insert into kreatura select * from wikingowie.kreatura;
insert into zasob select * from wikingowie.zasob;
```

*Podpunkt b)*
```sql
SELECT * FROM zasob;
```

*Podpunkt c)*
```sql
SELECT * FROM zasob where rodzaj='jedzenie';
```

*Podpunkt d)*
```sql
select idZasobu,ilosc,idKreatury from ekwipunek where idKreatury IN(1,3,5);
```

**Zadanie 2**
*Podpunkt a)*
```sql
SELECT * FROM kreatura where rodzaj<>'wiedzma' and udzwig>=50;
```

*Podpunkt b)*
```sql
SELECT * FROM zasob where waga between 2 and 5;
```

*Podpunkt c)*
```sql
SELECT * FROM kreatura where nazwa like '%or%' and udzwig between 30 and 70;
```

**Zadanie 3**
*Podpunkt a)*
```sql
SELECT * FROM zasob where month(dataPozyskania) between 7 and 8;
```

*Podpunkt b)*
```sql

```


**Zadanie 4**
*Podpunkt a)*
```sql
select distinct rodzaj from kreatura;
```

