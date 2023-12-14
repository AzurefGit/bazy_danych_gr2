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

```

**Zadanie 2**

*Podpunkt a)*
```sql
-||-
```

*Podpunkt b)*
```sql

```

**Ciekawostki**

#Nie bedzie 5.2 z lab07 na kol
