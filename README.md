<b>*Query Trigger</b>
CREATE TRIGGER BEFORE_harga_update  
BEFORE UPDATE ON tiket0007  
FOR EACH ROW  
INSERT INTO log_perubahan (tiket, harga_lama, harga_baru, waktu_perubahan)  
VALUES (OLD.nama_tiket, OLD.harga, NEW.harga, NOW());





<b>*Query view menggunakan join</b>
CREATE VIEW view1 AS
SELECT
    penonton0007.kode_penonton,
    penonton0007.nama,
    penonton0007.tanggal_beli,
    tiket0007.tiket,
    tiket0007.harga
FROM
    penonton0007
JOIN
    tiket0007
ON
    penonton0007.tiket = tiket0007.tiket;







<b>*Query Prosedure</b>
DELIMITER $$

CREATE PROCEDURE hapusDriver()
BEGIN
    START TRANSACTION;
    
    DELETE FROM driver WHERE kd_driver = '3P434';
    
    -- Jika ingin commit perubahan:
    -- COMMIT;
    
    -- Jika ingin membatalkan perubahan:
    ROLLBACK;
END$$

DELIMITER ;

<b>*query Untuk phpmyadmin</b>

BEGIN 
	START TRANSACTION;
    
    DELETE FROM driver WHERE kd_driver = "	3P434";
    
    ROLLBACK;
    
END

