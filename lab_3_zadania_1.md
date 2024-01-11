**Zadanie 1**


```sql
select imie, nazwisko, year(data_urodzenia) from pracownik
```

**Zadanie 2**


```sql
select imie, nazwisko, (year(now()) - year(data_urodzenia)) as wiek from pracownik
```

**Zadanie 3**


```sql
select d.nazwa, count(p.id_pracownika) from dzial d 
inner join pracownik p on d.id_dzialu = p.dzial 
group by d.nazw
```

**Zadanie 4**


```sql
select k.nazwa_kategori, count(t.nazwa_towaru) as liczba_produktow
from kategoria k inner join towar t on 
k.id_kategori = t.kategoria group by k.nazwa_kategori;
```

**Zadanie 5**


```sql

```
