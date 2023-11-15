*Zadanie 1*
```sql
SELECT * FROM osoba;
create table postac( id_postaci int auto_increment primary key, nazwa varchar(40), rodzaj enum('wiking','ptak','kobieta'), data_ur date, wiek int unsigned);
```

*Zadanie 2*

```sql
create table walizka( id_walizki int auto_increment primary key,
pojemnosc int unsigned,
kolor enum('rozowy','czerwony','teczowy','zolty'),
id_wlasciciela int,
foreign key(id_wlasciciela) references postac(id_postaci) on delete cascade);
```

*Zadanie 3*

```sql
create table izba (
adres_budynku varchar(130),
nazwa_izby varchar(100),
metraz int unsigned,
wlasciciel int,
primary key(adres_budynku, nazwa_izby),
foreign key(wlasciciel) references postac(id_postaci) on delete set null);
```

*Zadanie 4*

```sql
create table przetwory (
id_przetworu int auto_increment primary key,
rok_produkcji year default 1654,
id_wykonawcy int,
zawartosc varchar(100),
dodatek varchar(100) default 'papryczka chilli',
id_konsumenta INT,
foreign key (id_konsumenta) references postac(id_postaci));
```

*Zadanie 5*

```sql
create table statek (
nazwa_statku varchar(60) primary key,
rodzaj_statku enum('pasazerski', 'towarowy', 'wojenny'),
data_wodowania date,
max_ladownosc int unsigned);
```
