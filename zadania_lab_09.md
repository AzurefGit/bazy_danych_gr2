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

# Funkcja 

alter table kreatura modify waga int default 0;
```



*Ciekawostki*

Nie bedzie na  kol
Bedzie na wej 11.01.2024
