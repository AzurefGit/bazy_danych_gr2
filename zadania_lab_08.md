**Zadanie 1**

*Podpunkt a)*
```sql
# Stworzenie tabel
create table uczestnicy like wikingowie.uczestnicy;
create table etapy_wyprawy like wikingowie.etapy_wyprawy;
create table sektor like wikingowie.sektor;
create table wyprawa like wikingowie.wyprawa;
# Dodanie rekordów
insert into uczestnicy select * from wikingowie.uczestnicy;
insert into etapy_wyprawy select * from wikingowie.etapy_wyprawy;
insert into sektor select * from wikingowie.sektor;
insert into wyprawa select * from wikingowie.wyprawa;
```

*Podpunkt b)*
```sql
#Podpowiedź: left join lub podzapytanie
select k.nazwa from kreatura k left join uczestnicy u on u.id_uczestnika=k.idKreatury where id_uczestnika is null
```

*Podpunkt c)*
```sql
#inner join
select w.nazwa, sum(k.udzwig) from uczestnicy u inner join wyprawa w on u.id_wyprawy=w.id_wyprawy inner join kreatura k on u.id_uczestnika=k.idKreatury group by w.nazwa;
```

**Zadanie 2**

*Podpunkt a)*
```sql
select w.nazwa, count(k.idKreatury) as 'liczbaUczestnikow', group_concat(k.nazwa) as 'uczestnicy' from uczestnicy u inner join wyprawa w on u.id_wyprawy=w.id_wyprawy inner join kreatura k on u.id_uczestnika=k.idKreatury group by w.nazwa;
```

*Podpunkt b)*
```sql
select ew.idwyprawy, ew.dziennik, s.nazwa as 'nazwa_sektora', k.nazwa as 'nazwa_kierownika' from etapy_wyprawy ew inner join sektor s on ew.sektor=s.id_sektora inner join wyprawa w on ew.idwyprawy=w.id_wyprawy inner join kreatura k on w.kierownik=k.idKreatury order by w.data_rozpoczecia asc, ew.kolejnosc asc;
```


**Zadanie 3**

*Podpunkt a)*
```sql
select s.nazwa, count(ew.sektor) from sektor s left join etapy_wyprawy ew on s.id_sektora = ew.sektor group by s.id_sektora
```

*Podpunkt b)*
```sql
select k.nazwa, if(count(u.id_uczestnika) > 0, 'brał udział w wyprawie', 'nie brał udział w wyprawie') czy_bral_udzial from kreatura k left join uczestnicy u on u.id_uczestnika = k.idKreatury group by k.idKreatury;
```


**Zadanie 4**

*Podpunkt a)*
```sql
select w.nazwa, sum(length(ew.dziennik)) as suma_znakow from etapy_wyprawy ew inner join wyprawa w on w.id_wyprawy = ew.idWyprawy group by w.nazwa having suma_znakow < 400;
```

*Podpunkt b)*
```sql
select u.id_wyprawy, w.nazwa, sum(e.ilosc*z.waga) / count(distinct u.id_uczestnika) from uczestnicy u inner join ekwipunek e on u.id_uczestnika = e.idKreatury inner join zasob z on z.idZasobu = e.idZasobu inner join wyprawa w on w.id_wyprawy = u.id_wyprawy group by w.id_wyprawy;
```


**Zadanie 5**

*Podpunkt a)*
```sql
select k.nazwa, datediff(w.data_rozpoczecia, k.dataUr) from kreatura k inner join wyprawa w on k.idKreatury = w.kierownik inner join etapy_wyprawy ew on ew.idWyprawy = w.id_wyprawy inner join sektor s on s.id_sektora = ew.sektor where s.nazwa like 'Chatka dziadka';
```

**Ciekawostki**
```sql
#Jeżeli coś zwraca null mozna zmienić wyświetlanie na dowolny cosiek:
-ifnull((ew.sektor), 0) <-- wypisze 0 jeżeli jet null

#Nie bedzie 5.2 z lab07 na kol
```
