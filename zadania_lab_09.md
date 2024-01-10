**Zadanie 1**

*Podpunkt a)*
```sql
DELIMITER //
create trigger kreatura_before_insert
before insert ON kreatura
for each row
BEGIN
	IF NEW.waga <= 0
    THEN
		SET NEW.waga = 1;
	END IF;
END
//

DELIMITER //
create trigger kreatura_before_update
before update ON kreatura
for each row
BEGIN
	IF NEW.waga <= 0
    THEN
		SET NEW.waga = 1;
	END IF;
END
//


alter table kreatura modify waga int default 0; #zmiana na signed, by błędów nie było
show create trigger nazwa; #wyświetlanie

```

**Zadanie 2**

*Podpunkt a)*
```sql
create ... like ...
... modify ... varchar(50)

DELIMITER //
create trigger wyprawa_before_delete
before delete ON wyprawa 
for each row
BEGIN
	insert into archiwum_wypraw 
	select w.id_wyprawy, w.nazwa, w.data_rozpoczecia, w.data_zakonczenia, k.nazwa from wyprawa w
	inner join kreatura k on w.kierownik=k.idKreatury where id.wyprawy = old.id_wyprawy;
END
//
DELIMITER ;
```

**Zadanie 3**

*Podpunkt a)*
```sql
DELIMITER $$
CREATE PROCEDURE eliksir_sily(IN id int)
BEGIN
Update kreatura set udzwig = 1.2 * udzwig where id_kreatury = id;
END
$$
DELIMITER ;
```

*Podpunkt b)*
```sql

```

**Zadanie 4**

*Podpunkt a)*
```sql
create table system_alarmowy(id_alarmu int, wiadomosc varchar(50));
```

*Podpunkt b)*
```sql
DELIMITER $$

CREATE TRIGGER uczestnicy_after_insert
AFTER INSERT ON uczestnicy
FOR EACH ROW
BEGIN
	DECLARE tesciowa varchar(100);
	DECLARE sektor_id integer;
	DECLARE czy_tesciowa bool;
	DECLARE czy_chata_dziadka bool;
	SET tesciowa = 'Tesciowa';
	SET sektor_id = 7;



IF tesciowa in (
	SELECT nazwa from kreatura WHERE idKreatury in 
	( SELECT id_uczestnika from uczestnicy where id_wyprawy=NEW.id_wyprawy)) 
	
THEN 
    
	SET czy_tesciowa = true;
	END IF;
    
IF sektor_id in (
	SELECT sektor FROM etapy_wyprawy WHERE idWyprawy=NEW.id_wyprawy
	) 
THEN 
	SET czy_chata_dziadka = true;
END IF;
    
IF czy_tesciowa AND czy_chata_dziadka
    
THEN  
	INSERT INTO system_alarmowy VALUES(default,'Tesciowa nadchodzi !!!');
END IF;

END
$$

DELIMITER ;

insert into uczestnicy values(2,14); #sprawdzenie
```

*Ciekawostki*

Nie bedzie na  kol

Bedzie na wej 11.01.2024
