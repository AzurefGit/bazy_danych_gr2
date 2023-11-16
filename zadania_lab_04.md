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
adres_budynku varchar(50) not null,
nazwa_izby varchar(50) not null,
metraz mediumint unsigned,
wlasciciel int,
foreign key(wlasciciel) references postac(id_postaci) on delete set null
);
# on delete lub on update -> restrict|set null|cascade

# pkt 2
alter table izba add column kolor varchar(30) default 'czarny' after metraz;
describe izba;

# pkt 3
insert into izba values('Kolejowa 23','spiżarnia',10,default,1);

#dodanie klucza głównego 
alter table izba add primary key(adres_budynku, nazwa_izby);
```


*Zadanie 4*

```sql
create table przetwory (
id_przetworu int auto_increment primary key,
rok_produkcji smallint default 1654,
id_wykonawcy int,
zawartosc varchar(100),
dodatek varchar(60) default 'papryczka chilli',
id_konsumenta int,
foreign key (id_wykonawcy) references postac(id_postaci),
foreign key (id_konsumenta) references postac(id_postaci)
);
# pkt 1
insert into przetwory values(default, default, 3, 'bigos',default,2);

#przydatne polecenie do podejrzenia tabeli |-/-\-|
show create table postac;
```

*Zadanie 5*

```sql
# pkt 1
insert into postac values(default, 'Olaf', 'wiking', '1699-01-05',333),
(default, 'Trynda', 'wiking', '1650-01-23',400),
(default, 'Paweł', 'wiking', '1633-05-30',450),
(default, 'Rolf', 'wiking', '1631-12-21',444),
(default, 'Ralf', 'wiking', '1711-04-19',373);

create table statek (
nazwa_statku varchar(30) primary key,
rodzaj_statku enum('wiosłowy',' żaglowy','mechaniczny','śrubowy'),
data_wodowania date,
max_ladownosc smallint unsigned
);

insert into statek values('MS Sea',4,'2005-09-02',234);

alter table postac add funkcja varchar(50);

#pkt 5
update postac
set funkcja = 'kapitan'
where nazwa = 'Bjorn'

#pkt 6
alter table postac add nazwa_statku varchar(30);

alter table postac
add foreign key (nazwa_statku)
references statek(nazwa_statku);

#pkt 7
update postac
set nazwa_statku = 'SS Stone'
where rodzaj = 'wiking';

update postac
set nazwa_statku = 'MS Sea'
where rodzaj = 'drozd';

#pkt 8
delete from izba
where nazwa_izby = 'spiżarnia';

#pkt 9
drop table izba;
```
