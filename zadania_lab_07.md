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
select k.nazwa, z.nazwa, k.dataUr from kreatura k inner join ekwipunek e on k.idKreatury=e.idKreatury inner join zasob z on z.idZasobu=e.idZasobu having year(k.dataUr) like '167_';
```

*Podpunkt b)*
```sql
select * from kreatura k inner join ekwipunek e on k.idKreatury=e.idKreatury inner join zasob z
on z.idZasobu=e.idZasobu where z.rodzaj = 'jedzenie' order by k.nazwa asc limit 5;
```

*Podpunkt c)*
```sql
#połączenie tabeli samej ze soba
select concat(k1.nazwa,' ',k2.nazwa) from kreatura k1 inner join kreatura k2 where k1.idKreatury - k2.idKreatury = 5;
```

**Zadanie 5**


*Podpunkt a)*
```sql
#1. Gdzie dane?
#2. Które kolumny
#3. Wakunek (1200zł)
#4. (repeta) Koncowe cośki(group by, order by, having, limit, ...)
select k.rodzaj, avg(z.waga * e.ilosc) from kreatura k inner join ekwipunek e on k.idKreatury=e.idKreatury inner join zasob z on e.idZasobu=z.idZasobu where k.rodzaj not in ('waz','malpa') and e.ilosc < 30 group by k.rodzaj; 
```

*Podpunkt b)*
```sql
#1. sposób (podzapytanie):
select a.nazwa, a.rodzaj, a.dataUr from kreatura a, (select min(dataUr) min, max(dataUr) max from kreatura group by rodzaj) b where b.min = a.dataUr or b.max=a.dataUr;
#2. sposób (select ... union select ....)
```
**Ciekawostki/dodatkowe materiały**

```sql
#funkcje agregujące: avg(), sum(), count(), min(), max()
#wartości nie null "count(*)" 
#wyświetlanie wieku:
select year(curdate()) - year(dataUr) as wiek from kreatura;
select year(now()) - year(dataUr) as wiek from kreatura;
#warunki przed selectem
having sum(waga) > 10;
```
