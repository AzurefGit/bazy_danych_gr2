**Zadanie 1**


*Podpunkt a)*
```sql
  select avg(waga) from kreatura where rodzaj = 'wiking';
```

*Podpunkt b)*
```sql
  select rodzaj, avg(waga), count(waga) from kreatura group by rodzaj;
```

*Podpunkt c)*
```sql
  select avg(year(now()) - year(dataUr)) as wiek from kreatura;
```

**Zadanie 2**


*Podpunkt a)*
```sql
  select rodzaj, sum(waga*ilosc) as suma_wag from zasob group by rodzaj;
```

*Podpunkt b)*
```sql
  select nazwa, avg(waga)  from zasob where ilosc>=4 group by nazwa having sum(waga) > 10;
```

*Podpunkt c)*
```sql
  select rodzaj, count(distinct nazwa) as liczba from zasob where ilosc > 1 group by rodzaj having liczba > 1;
```

**Zadanie 3**


*Podpunkt a)*
```sql
select nazwa,ilosc from kreatura, ekwipunek where kreatura.idKreatury=ekwipunek.idKreatury;
#lub inner join
select k.nazwa,e.ilosc from kreatura k inner join ekwipunek e on k.idKreatury=e.idKreatury;
```

*Podpunkt b)*
```sql
select k.nazwa, e.idZasobu, z.nazwa, e.ilosc from kreatura k inner join ekwipunek e on k.idKreatury=e.idKreatury inner join zasob z on z.idZasobu=e.idZasobu;
```

*Podpunkt c)*
```sql
select * from kreatura k left join ekwipunek e on k.idKreatury=e.idKreatury where e.idEkwipunku
is  null;
# podzapytanie
select idKreatury from kreatura where idKreatury not in (select distinct idKreatury from ekwipunek where idKreatury is not null)
```

**Zadanie 4**


*Podpunkt a)*
```sql
select k.nazwa, z.nazwa, k.dataUr from kreatura k inner join ekwipunek e on k.idKreatury=e.idKreatury inner join zasob z on z.idZasobu=e.idZasobu having year(k.dataUr) = 1670 ;
```

*Podpunkt b)*
```sql
select k.nazwa, z.nazwa, k.dataUr from kreatura k inner join ekwipunek e on k.idKreatury=e.idKreatury inner join zasob z on z.idZasobu=e.idZasobu having year(k.dataUr) = 1670 ;
```

*Podpunkt c)*
```sql

```

**Ciekawostki/dodatkowe materiały**

```sql
#funkcje agregujące: avg(), sum(), count(), min(), max()
#wartości nie null "count(*)" 
#wyświetlanie wieku 
select year(curdate()) - year(dataUr) as wiek from kreatura;
select year(now()) - year(dataUr) as wiek from kreatura;
#warunki przed selectem
having sum(waga) > 10;
```
