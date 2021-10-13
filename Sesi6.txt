--A. Buat Database baru dengan nama db_staf
CREATE database db_staff;
use db_staff;

--B. Buat Table data_staff dengan desain spt dibawah ini : 
CREATE table tbl_data_staff(
	id_staff int identity(1,1) primary key,
	nik int,
	nama varchar(50),
	alamat varchar(200),
	handphone varchar(15)
);

--C. asukkan data ke dalam table data_staff sesuai dengan table diatas
--D. Masukkan lebih dari 1 data ke dalam table data masih dalam table diatas.
INSERT INTO tbl_data_staff(nik, nama, alamat, handphone)
VALUES(7201,'BEJO','SURABAYA','082292563365');
INSERT INTO tbl_data_staff(nik, nama, alamat, handphone)
VALUES(4420,'BEAVER','JAKARTA','082292563347');
INSERT INTO tbl_data_staff(nik, nama, alamat, handphone)
VALUES(2236,'DOCKER','BANDUNG','082292563344');
INSERT INTO tbl_data_staff(nik, nama, alamat, handphone)
VALUES(3210,'DOTNET','JOGJA','082292563399');
INSERT INTO tbl_data_staff(nik, nama, alamat, handphone)
VALUES(1159,'ZOOM','BALI','082292563365');

--test
SELECT TDS.* FROM tbl_data_staff tds;

--E. Tambahkan kolom baru pada table data_staff yaitu joindate sekaligus masukan 1 data kedalam table 
--data_staf
ALTER table tbl_data_staff add join_date date;

INSERT INTO tbl_data_staff(nik, nama, alamat, handphone, join_date)
VALUES(2253,'JAVA','BALI','082292563325','10-05-2020');

--F. Tampilkan 2 data SQL kalian sekarang 
SELECT TOP 2 * from tbl_data_staff;

--G. Tampilkan 3 data SQL kalian sekarang 
SELECT TOP 3 * from tbl_data_staff order by id_staff desc;

--H. Buat Table baru staffoutsource dengan isi yang sama seperti data_staff
CREATE table tbl_staff_out_source(
	id_staff_out_source int identity(1,1) primary key,
	nik int,
	nama varchar(50),
	alamat varchar(200),
	handphone varchar(15),
	join_date date
);

--I. Masukkan 10 data baru ke table staffoutsource
INSERT INTO tbl_staff_out_source(nik, nama, alamat, handphone, join_date)
VALUES(1334,'SKAK','SURABAYA','082292503325','10-01-2020');
INSERT INTO tbl_staff_out_source(nik, nama, alamat, handphone, join_date)
VALUES(1234,'SUPARMAN','JOGJA','082292543325','11-05-2020');
INSERT INTO tbl_staff_out_source(nik, nama, alamat, handphone, join_date)
VALUES(5547,'PUTRA','BALI','082292573325','10-05-2021');
INSERT INTO tbl_staff_out_source(nik, nama, alamat, handphone, join_date)
VALUES(6698,'NYOMAN','BALI','082292453325','10-05-2020');
INSERT INTO tbl_staff_out_source(nik, nama, alamat, handphone, join_date)
VALUES(7788,'SUDI','BANDUNG','082292463325','10-05-2019');
INSERT INTO tbl_staff_out_source(nik, nama, alamat, handphone, join_date)
VALUES(4563,'CLARA','KALIMANTAN','082292233325','10-05-2020');
INSERT INTO tbl_staff_out_source(nik, nama, alamat, handphone, join_date)
VALUES(4125,'BRAM','SOLO','082292453325','10-05-2020');
INSERT INTO tbl_staff_out_source(nik, nama, alamat, handphone, join_date)
VALUES(8965,'HADI','NTT','082292143325','10-06-2020');
INSERT INTO tbl_staff_out_source(nik, nama, alamat, handphone, join_date)
VALUES(4123,'ANGGA','JAKARTA','082292483325','10-01-2020');
INSERT INTO tbl_staff_out_source(nik, nama, alamat, handphone, join_date)
VALUES(6985,'HUSOR','MEDAN','082292793325','10-08-2020');
--test
DELETE tbl_data_staff WHERE nik = '1334';

--J. Tampilkan data pada 2 Table yang sudah kalian buat dengan joindate yang sama
SELECT tds.*, tsos.* FROM 
tbl_data_staff tds 
full join
tbl_staff_out_source tsos 
on tds.join_date = tsos.join_date;

--K. Tampilkan seluruh data sebelah kanan yang sama pada table staff_outsource
SELECT tds.*, tsos.* FROM 
tbl_data_staff tds 
right join
tbl_staff_out_source tsos
on tds.join_date = tsos.join_date;

--L. Tampilkan seluruh data staff sebelah kiri yang punya nilai tidak sama akan bernilai null
SELECT tds.*, tsos.* FROM 
tbl_data_staff tds 
left join
tbl_staff_out_source tsos
on tds.join_date = tsos.join_date;

--M. Tampilkan seluruh data antara 2 tabel baik itu tidak punya kesamaan dan bernilai null.
SELECT tds.*, tsos.* FROM 
tbl_data_staff tds 
inner join
tbl_staff_out_source tsos
on tds.join_date = tsos.join_date;

--Test improve
SELECT tds.nik, tds.nama from
tbl_data_staff tds 
union all
select tsos.nik, tsos.nama from
tbl_staff_out_source tsos;

--Test improve
SELECT tds.nik, tds.nama from
tbl_data_staff tds 
union 
select tsos.nik, tsos.nama from
tbl_staff_out_source tsos;