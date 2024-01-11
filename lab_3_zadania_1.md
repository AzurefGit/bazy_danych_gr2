**Zadanie 1**


```sql
select imie, nazwisko, year(data_urodzenia) from pracownik;
```

**Zadanie 2**


```sql
select imie, nazwisko, (year(now()) - year(data_urodzenia)) as wiek from pracownik;
```

**Zadanie 3**


```sql
select d.nazwa, count(p.id_pracownika) from dzial d 
inner join pracownik p on d.id_dzialu = p.dzial 
group by d.nazwa;
```

**Zadanie 4**


```sql
select k.nazwa_kategori, count(t.nazwa_towaru) as liczba_produktow
from kategoria k inner join towar t on 
k.id_kategori = t.kategoria group by k.nazwa_kategori;
```

**Zadanie 5**


```sql
select k.nazwa_kategori, group_concat(t.nazwa_towaru) 
from kategoria k inner join towar t on 
k.id_kategori = t.kategoria group by k.nazwa_kategori;
```

**Zadanie 6**


```sql
select round(avg(pensja), 1) from pracownik;
```

**Zadanie 7**


```sql
select round(avg(pensja), 2) from pracownik
where data_zatrudnienia <= '2019-01-11';
select data_zatrudnienia, subdate(data_zatrudnienia, interval 5 year)
from pracownik;
```

**Zadanie 8**


```sql
select t.nazwa_towaru, p.towar, sum(p.ilosc) as suma from towar t inner join 
pozycja_zamowienia p on t.id_towaru=p.towar group by p.towar
order by suma desc limit 10;

Reszta na dc
```

**Zadanie 9**


```sql

```

**Zadanie 10**


```sql

```
