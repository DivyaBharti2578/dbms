
mysql> use project1;
Database changed
mysql> create table publisher(Publisher_Name varchar(50) primary key,Publisher_address varchar(50) not null,Publisher_contact int);
Query OK, 0 rows affected (0.07 sec)

mysql> create table book(Book_Id int primary key,Book_Tittle varchar(50) not null,Publisher_name varchar(50),publishing_year int);
Query OK, 0 rows affected (0.05 sec)

mysql> create table branch(Branch_Id int primary key,Branch_Name varchar(50) not null);
Query OK, 0 rows affected (0.04 sec)

mysql> create table borrow(Card_Id int primary key,Borrower_name varchar(50) not null,Borrower_address varchar(60),Borrower_phone_no int);
Query OK, 0 rows affected (0.04 sec)
 create table copies(Copies_ID int primary key,Book_ID int(50) not null,Branch_Id int not null,No_of_copies int not null);
Query OK, 0 rows affected, 1 warning (0.05 sec)
create table author(Author_ID int primary key,Author_name varchar (50) not null,BookId int not null,constraint FK_BOOK_ID foreign key(BookID) referen
ces book(Book_Id));
Query OK, 0 rows affected (0.13 sec)

mysql> describe author;
+-------------+-------------+------+-----+---------+-------+
| Field       | Type        | Null | Key | Default | Extra |
+-------------+-------------+------+-----+---------+-------+
| Author_ID   | int         | NO   | PRI | NULL    |       |
| Author_name | varchar(50) | NO   |     | NULL    |       |
| BookId      | int         | NO   | MUL | NULL    |       |
+-------------+-------------+------+-----+---------+-------+
 create table issue(Issue_id int,constraint fk_issueid foreign key(Issue_Id) references borrow(Card_Id) on update cascade,issue_date int,return_date int,days_remaining int);
Query OK, 0 rows affected (0.09 sec)

mysql> create table staff(Staff_Id int primary key,Staff_name varchar(50),shift varchar(50));
Query OK, 0 rows affected (0.04 sec)
create trigger issue_table before insert on issue for each row set new.days_remaining=new.return_date-new.issue_date;
Query OK, 0 rows affected (0.02 sec)

mysql> insert into publisher values('Harper collin','Old Rajendra Nagar,New Delhi','2136457895');
Query OK, 1 row affected (0.02 sec)
mysql> insert into publisher values('Simon and schuster','Avenue of America,New York',33045008);
Query OK, 1 row affected (0.01 sec)

mysql> insert into publisher values('Houghton Mifflin Harcourt','125 HighSt,Boston',56045008);
Query OK, 1 row affected (0.01 sec)

mysql> insert into publisher values('Allen&Unwin','406 Alebert Street,Melbourne',46595088);
Query OK, 1 row affected (0.01 sec)

mysql> update publisher set publisher_address='25th avenue,New York' where publisher_name='Harper collin';
Query OK, 1 row affected (0.01 sec)
Rows matched: 1  Changed: 1  Warnings: 0

mysql> select * from publisher;
+---------------------------+------------------------------+-------------------+
| Publisher_Name            | Publisher_address            | Publisher_contact |
+---------------------------+------------------------------+-------------------+
| Allen&Unwin               | 406 Alebert Street,Melbourne |          46595088 |
| BloomBurry                | Bedford Avenue,London        |          78945258 |
| Harper collin             | 25th avenue,New York         |        2136457895 |
| Houghton Mifflin Harcourt | 125 HighSt,Boston            |          56045008 |
| Simon and schuster        | Avenue of America,New York   |          33045008 |
+---------------------------+------------------------------+-------------------+
5 rows in set (0.00 sec)

mysql> insert into book values(45,'David Copperfeild','Harper collin',1849);
Query OK, 1 row affected (0.01 sec)

mysql> insert into book values(78,'Sapiens','Harper collin',2011);
Query OK, 1 row affected (0.01 sec)

mysql> insert into book values(89,'Leader','Harper collin',1996);
Query OK, 1 row affected (0.01 sec)

mysql> insert into book values(64,'The Hating game','Harper collin',2016);
Query OK, 1 row affected (0.01 sec)

mysql> insert into book values(23,'Alchi','Harper collin',2016);
Query OK, 1 row affected (0.01 sec)
mysql> insert into book values(12,'Harry potter the chamber of secrets','BloobBurry',1998);
Query OK, 1 row affected (0.01 sec)

mysql> insert into book values(22,'Harry potter the half blood prince','BloobBurry',2005);
Query OK, 1 row affected (0.01 sec)

mysql> update book set publisher_name='BloomBurry' where Book_Id=22;
Query OK, 1 row affected (0.01 sec)
Rows matched: 1  Changed: 1  Warnings: 0

mysql> insert into book values(56,'Harry potter prisoner of azkaban','BloomBurry',1997);
Query OK, 1 row affected (0.01 sec)

mysql> insert into book values(36,'Harry potter order of pheonix','BloomBurry',2003);
Query OK, 1 row affected (0.01 sec)

mysql> update book set publishing_year=2001 where Book_Id=56;
Query OK, 1 row affected (0.01 sec)
Rows matched: 1  Changed: 1  Warnings: 0

mysql> insert into book values(07,'Harry potter goblet of fire','BloomBurry',2002);
Query OK, 1 row affected (0.01 sec)

mysql> insert into book values(80,'Banned','Simon and schuster',2023);
Query OK, 1 row affected (0.01 sec)
mysql> insert into book values(17,'Monday to Friday','Simon and schuster',2024);
Query OK, 1 row affected (0.01 sec)

mysql> insert into book values(40,'In priase of laziness','Simon and schuster',2024);
Query OK, 1 row affected (0.01 sec)

mysql> insert into book values(96,'Krishna Maha Vishnu Avatar','Simon and schuster',2024);
Query OK, 1 row affected (0.01 sec)

mysql> insert into book values(30,'Someone like her','Simon and schuster',2024);
Query OK, 1 row affected (0.01 sec)

mysql> insert into book values(88,'The song of the tree','Simon and schuster',2024);
Query OK, 1 row affected (0.01 sec)

mysql> insert into book values(34,'A woman burnt','Simon and schuster',2024);
Query OK, 1 row affected (0.01 sec)

mysql> insert into book values(99,'The last trace','Allen&Unwin',2013);
Query OK, 1 row affected (0.01 sec)

mysql> insert into book values(66,'Wolf girl','Allen&Unwin',1998);
Query OK, 1 row affected (0.01 sec)

mysql> insert into book values(55,'Fing your People','Allen&Unwin',1999);
Query OK, 1 row affected (0.01 sec)

mysql> insert into book values(25,'The Honeyeater','Allen&Unwin',2007);
Query OK, 1 row affected (0.01 sec)

mysql> insert into book values(49,'Ben Simmon','Allen&Unwin',2019);
Query OK, 1 row affected (0.05 sec)

mysql> insert into book values(47,'Better life',' Houghton Mifflin Harcourt',1889);
Query OK, 1 row affected (0.01 sec)

mysql> insert into book values(38,'Reading Series',' Houghton Mifflin Harcourt',1990);
Query OK, 1 row affected (0.01 sec)

mysql> insert into book values(26,'English',' Houghton Mifflin Harcourt',1997);
Query OK, 1 row affected (0.05 sec)
mysql> insert into book values(79,'Pinocchio',' Houghton Mifflin Harcourt',1940);
Query OK, 1 row affected (0.01 sec)
mysql> select * from book;
+---------+-------------------------------------+----------------------------+-----------------+
| Book_Id | Book_Tittle                         | Publisher_name             | publishing_year |
+---------+-------------------------------------+----------------------------+-----------------+
|       5 | charlotte web                       |  Houghton Mifflin Harcourt |            1978 |
|       7 | Harry potter goblet of fire         | BloomBurry                 |            2002 |
|      12 | Harry potter the chamber of secrets | BloomBurry                 |            1998 |
|      17 | Monday to Friday                    | Simon and schuster         |            2024 |
|      22 | Harry potter the half blood prince  | BloomBurry                 |            2005 |
|      23 | Alchemist                           | Harper collin              |            2016 |
|      25 | The Honeyeater                      | Allen&Unwin                |            2007 |
|      26 | English                             |  Houghton Mifflin Harcourt |            1997 |
|      30 | Someone like her                    | Simon and schuster         |            2024 |
|      34 | A woman burnt                       | Simon and schuster         |            2024 |
|      36 | Harry potter order of pheonix       | BloomBurry                 |            2003 |
|      38 | Reading Series                      |  Houghton Mifflin Harcourt |            1990 |
|      40 | In priase of laziness               | Simon and schuster         |            2024 |
|      45 | David Copperfeild                   | Harper collin              |            1849 |
|      47 | Better life                         |  Houghton Mifflin Harcourt |            1889 |
|      49 | Ben Simmon                          | Allen&Unwin                |            2019 |
|      55 | Fing your People                    | Allen&Unwin                |            1999 |
|      56 | Harry potter prisoner of azkaban    | BloomBurry                 |            2001 |
|      64 | The Hating game                     | Harper collin              |            2016 |
|      66 | Wolf girl                           | Allen&Unwin                |            1998 |
|      78 | Sapiens                             | Harper collin              |            2011 |
|      79 | Pinocchio                           |  Houghton Mifflin Harcourt |            1940 |
|      80 | Banned                              | Simon and schuster         |            2023 |
|      88 | The song of the tree                | Simon and schuster         |            2024 |
|      89 | Leader                              | Harper collin              |            1996 |
|      96 | Krishna Maha Vishnu Avatar          | Simon and schuster         |            2024 |
|      99 | The last trace                      | Allen&Unwin                |            2013 |
+---------+-------------------------------------+----------------------------+-----------------+
27 rows in set (0.00 sec)

mysql> insert into branch values(50106,'Delhi');
Query OK, 1 row affected (0.01 sec)

mysql> insert into branch values(40512,'Kolkata');
Query OK, 1 row affected (0.01 sec)

mysql> insert into branch values(78912,'Hyderabad');
Query OK, 1 row affected (0.01 sec)

mysql> insert into branch values(45698,'Mumbai');
Query OK, 1 row affected (0.01 sec)

mysql> insert into branch values(36541,'Pune');
Query OK, 1 row affected (0.05 sec)

mysql> insert into branch values(45678,'Banglore');
Query OK, 1 row affected (0.01 sec)

mysql> select * from branch;
+-----------+-------------+
| Branch_Id | Branch_Name |
+-----------+-------------+
|     36541 | Pune        |
|     40512 | Kolkata     |
|     45678 | Banglore    |
|     45698 | Mumbai      |
|     50106 | Delhi       |
|     78912 | Hyderabad   |
+-----------+-------------+
6 rows in set (0.00 sec)

mysql> insert into borrow values(123,'Divya Bharti','North Banglore',857987945);
Query OK, 1 row affected (0.03 sec)

mysql> insert into borrow values(129,'Ashwini Mukherji','Mahalaxhmi,Banglore',857897945);
Query OK, 1 row affected (0.01 sec)

mysql> insert into borrow values(106,'Rajiv Sharma','Rajinagar,Banglore',987897945);
Query OK, 1 row affected (0.01 sec)

mysql> insert into borrow values(156,'Anjali Mehta','Rajendar Nagar,Delhi',789897945);
Query OK, 1 row affected (0.01 sec)

mysql> insert into borrow values(215,'Mohan Singh','Pimpri,Pune',897897989);
Query OK, 1 row affected (0.01 sec)

mysql> insert into borrow values(012,'Santosh Chatterji','Magarpata,Pune',756897123);
Query OK, 1 row affected (0.01 sec)

mysql> insert into borrow values(032,'Mehvish Kamal','Mukkerji Nagar,Delhi',956897124);
Query OK, 1 row affected (0.01 sec)

mysql> insert into borrow values(184,'Kishna Kumar','South Delhi,Delhi',756897123);
Query OK, 1 row affected (0.01 sec)

mysql> insert into borrow values(298,'Ayan Mishar','Kormangla,Bengaluru',856897145);
Query OK, 1 row affected (0.01 sec)

mysql> insert into borrow values(090,'Arvind Tripathi','Thane,Mumbai',756897145);
Query OK, 1 row affected (0.01 sec)

mysql> insert into borrow values(045,'Anamika Kumari','Near Park street,Kolkata',895897145);
Query OK, 1 row affected (0.01 sec)
mysql> insert into borrow values(255,'Rose Sebastian','Malard,Mumbai',785897145);
Query OK, 1 row affected (0.01 sec)

mysql> insert into borrow values(199,'Anaya Malhotra','Andheri West,Mumbai',657897145);
Query OK, 1 row affected (0.01 sec)

mysql> insert into borrow values(189,'Misha Iyer','Whitefield,Bnaglore',957897145);
Query OK, 1 row affected (0.01 sec)

mysql> select * from borrow;
+---------+-------------------+--------------------------+-------------------+
| Card_Id | Borrower_name     | Borrower_address         | Borrower_phone_no |
+---------+-------------------+--------------------------+-------------------+
|      12 | Santosh Chatterji | Magarpata,Pune           |         756897123 |
|      32 | Mehvish Kamal     | Mukkerji Nagar,Delhi     |         956897124 |
|      45 | Anamika Kumari    | Near Park street,Kolkata |         895897145 |
|      90 | Arvind Tripathi   | Thane,Mumbai             |         756897145 |
|     106 | Rajiv Sharma      | Rajinagar,Banglore       |         987897945 |
|     107 | Kundan Kumar      | Indiranagar,Bengaluru    |         695897145 |
|     123 | Divya Bharti      | North Banglore           |         857987945 |
|     129 | Ashwini Mukherji  | Mahalaxhmi,Banglore      |         857897945 |
|     156 | Anjali Mehta      | Rajendar Nagar,Delhi     |         789897945 |
|     184 | Kishna Kumar      | South Delhi,Delhi        |         756897123 |
|     189 | Misha Iyer        | Whitefield,Bnaglore      |         957897145 |
|     199 | Anaya Malhotra    | Andheri West,Mumbai      |         657897145 |
|     215 | Mohan Singh       | Pimpri,Pune              |         897897989 |
|     255 | Rose Sebastian    | Malard,Mumbai            |         785897145 |
|     298 | Ayan Mishar       | Kormangla,Bengaluru      |         856897145 |
+---------+-------------------+--------------------------+-------------------+
15 rows in set (0.00 sec)
mysql> insert into copies value(111,5,36541,18);
Query OK, 1 row affected (0.01 sec)

mysql> insert into copies value(216,7,36541,23);
Query OK, 1 row affected (0.01 sec)

mysql> insert into copies value(169,7,36541,10);
Query OK, 1 row affected (0.01 sec)

mysql> insert into copies value(189,12,36541,13);
Query OK, 1 row affected (0.01 sec)

mysql> insert into copies value(199,17,36541,11);
Query OK, 1 row affected (0.01 sec)

mysql> insert into copies value(217,22,36541,8);
Query OK, 1 row affected (0.01 sec)

mysql> insert into copies value(167,23,36541,12);
Query OK, 1 row affected (0.01 sec)

mysql> insert into copies value(105,25,36541,08);
Query OK, 1 row affected (0.01 sec)

mysql> insert into copies value(112,34,36541,17);
Query OK, 1 row affected (0.01 sec)

mysql> insert into copies value(158,47,36541,12);
Query OK, 1 row affected (0.05 sec)

mysql> insert into copies value(123,89,36541,10);
Query OK, 1 row affected (0.01 sec)

mysql> insert into copies value(121,45,36541,15);
Query OK, 1 row affected (0.01 sec)

mysql> insert into copies value(119,88,40512,10);
Query OK, 1 row affected (0.01 sec)

mysql> insert into copies value(166,89,40512,9);
Query OK, 1 row affected (0.01 sec)

mysql> insert into copies value(114,49,40512,11);
Query OK, 1 row affected (0.01 sec)

mysql> insert into copies value(181,55,40512,19);
Query OK, 1 row affected (0.01 sec)

mysql> insert into copies value(180,99,40512,11);
Query OK, 1 row affected (0.05 sec)

mysql> insert into copies value(170,98,40512,7);
Query OK, 1 row affected (0.01 sec)

mysql> insert into copies value(144,66,40512,16);
Query OK, 1 row affected (0.01 sec)

mysql> insert into copies value(150,34,40512,8);
Query OK, 1 row affected (0.01 sec)

mysql> insert into copies value(131,29,40512,9);
Query OK, 1 row affected (0.01 sec)

mysql> insert into copies value(136,47,78912,12);
Query OK, 1 row affected (0.01 sec)
mysql> insert into copies value(0792,89,78912,12);
Query OK, 1 row affected (0.02 sec)

mysql> insert into copies value(079,55,78912,11);
Query OK, 1 row affected (0.01 sec)

mysql> insert into copies value(019,44,78912,12);
Query OK, 1 row affected (0.01 sec)
mysql> insert into copies value(009,26,78912,3);
Query OK, 1 row affected (0.01 sec)

mysql> insert into copies value(060,36,78912,12);
Query OK, 1 row affected (0.01 sec)

mysql> insert into copies value(070,34,78912,14);
Query OK, 1 row affected (0.04 sec)

mysql> insert into copies value(075,34,45678,11);
Query OK, 1 row affected (0.05 sec)

mysql> insert into copies value(215,5,45678,10);
Query OK, 1 row affected (0.01 sec)

mysql> insert into copies value(163,7,45678,12);
Query OK, 1 row affected (0.01 sec)

mysql> insert into copies value(143,88,45678,16);
Query OK, 1 row affected (0.01 sec)
mysql> insert into copies value(142,45,45678,13);
Query OK, 1 row affected (0.05 sec)

mysql> insert into copies value(140,40,45678,6);
Query OK, 1 row affected (0.01 sec)

mysql> insert into copies value(110,38,45678,7);
Query OK, 1 row affected (0.01 sec)

mysql> insert into copies value(100,25,45678,16);
Query OK, 1 row affected (0.01 sec)

mysql> insert into copies value(101,29,45678,10);
Query OK, 1 row affected (0.01 sec)

mysql> insert into copies value(109,34,45678,11);
Query OK, 1 row affected (0.01 sec)

mysql> insert into copies value(114,99,45678,10);
ERROR 1062 (23000): Duplicate entry '114' for key 'copies.PRIMARY'
mysql> insert into copies value(113,99,45678,10);
Query OK, 1 row affected (0.04 sec)

mysql> insert into copies value(118,98,45678,9);
Query OK, 1 row affected (0.01 sec)

mysql> insert into copies value(117,98,45678,12);
Query OK, 1 row affected (0.03 sec)
mysql> insert into copies value(179,80,40512,15);
Query OK, 1 row affected (0.01 sec)

mysql> select * from copies;
+-----------+---------+-----------+--------------+
| Copies_ID | Book_ID | Branch_Id | No_of_copies |
+-----------+---------+-----------+--------------+
|         9 |      26 |     78912 |            3 |
|        12 |      40 |     78912 |           10 |
|        19 |      44 |     78912 |           12 |
|        60 |      36 |     78912 |           12 |
|        70 |      34 |     78912 |           14 |
|        75 |      34 |     45678 |           11 |
|        79 |      55 |     78912 |           11 |
|       100 |      25 |     45678 |           16 |
|       101 |      29 |     45678 |           10 |
|       105 |      25 |     36541 |            8 |
|       109 |      34 |     45678 |           11 |
|       110 |      38 |     45678 |            7 |
|       111 |       5 |     36541 |           18 |
|       112 |      34 |     36541 |           17 |
|       113 |      99 |     45678 |           10 |
|       114 |      49 |     40512 |           11 |
|       117 |      98 |     45678 |           12 |
|       118 |      98 |     45678 |            9 |
|       119 |      88 |     40512 |           10 |
|       121 |      45 |     36541 |           15 |
|       123 |      89 |     36541 |           10 |
|       131 |      29 |     40512 |            9 |
|       136 |      47 |     78912 |           12 |
|       140 |      40 |     45678 |            6 |
|       142 |      45 |     45678 |           13 |
|       143 |      88 |     45678 |           16 |
|       144 |      66 |     40512 |           16 |
|       150 |      34 |     40512 |            8 |
|       158 |      47 |     36541 |           12 |
|       163 |       7 |     45678 |           12 |
|       166 |      89 |     40512 |            9 |
|       167 |      23 |     36541 |           12 |
|       169 |       7 |     36541 |           10 |
|       170 |      98 |     40512 |            7 |
|       173 |      30 |     40512 |           10 |
|       179 |      80 |     40512 |           15 |
|       180 |      99 |     40512 |           11 |
|       181 |      55 |     40512 |           19 |
|       189 |      12 |     36541 |           13 |
|       199 |      17 |     36541 |           11 |
|       215 |       5 |     45678 |           10 |
|       216 |       7 |     36541 |           23 |
|       217 |      22 |     36541 |            8 |
|       792 |      89 |     78912 |           12 |
+-----------+---------+-----------+--------------+
44 rows in set (0.00 sec)

mysql> insert into author value(45,'Jk Rowling',7);
Query OK, 1 row affected (0.01 sec)
ERROR 1062 (23000): Duplicate entry '45' for key 'author.PRIMARY'
mysql> insert into author value(44,'Jk Rowling',12);
Query OK, 1 row affected (0.01 sec)

mysql> insert into author value(47,'Jk Rowling',56);
Query OK, 1 row affected (0.01 sec)

mysql> insert into author value(78,'Jk Rowling',36);
Query OK, 1 row affected (0.01 sec)

mysql> insert into author value(17,'DevDutt Patnaik',89);
Query OK, 1 row affected (0.01 sec)

mysql> insert into author value(56,'Paul',23);
Query OK, 1 row affected (0.01 sec)
mysql> insert into author value(38,'Hinari',78);
Query OK, 1 row affected (0.01 sec)

mysql> insert into author value(33,'Charles',45);
Query OK, 1 row affected (0.01 sec)

mysql> select * from author;
+-----------+-----------------+--------+
| Author_ID | Author_name     | BookId |
+-----------+-----------------+--------+
|        17 | DevDutt Patnaik |     89 |
|        33 | Charles         |     45 |
|        38 | Hinari          |     78 |
|        44 | Jk Rowling      |     12 |
|        45 | Jk Rowling      |      7 |
|        47 | Jk Rowling      |     56 |
|        56 | Paul            |     23 |
|        78 | Jk Rowling      |     36 |
+-----------+-----------------+--------+
8 rows in set (0.00 sec)
mysql> insert into issue(issue_id,Issue_date,Return_date) value(12,12,30);
Query OK, 1 row affected (0.02 sec)

mysql> insert into issue(issue_id,Issue_date,Return_date) value(32,1,30);
Query OK, 1 row affected (0.01 sec)

mysql> insert into issue(issue_id,Issue_date,Return_date) value(45,9,29);
Query OK, 1 row affected (0.01 sec)

mysql> insert into issue(issue_id,Issue_date,Return_date) value(123,7,31);
Query OK, 1 row affected (0.01 sec)

mysql> insert into issue(issue_id,Issue_date,Return_date) value(189,11,31);
Query OK, 1 row affected (0.05 sec)

mysql> insert into issue(issue_id,Issue_date,Return_date) value(215,10,31);
Query OK, 1 row affected (0.04 sec)

mysql> insert into issue(issue_id,Issue_date,Return_date) value(255,15,30);
Query OK, 1 row affected (0.01 sec)

mysql> insert into issue(issue_id,Issue_date,Return_date) value(90,4,24);
Query OK, 1 row affected (0.01 sec)

mysql> select * from issue;
+----------+------------+-------------+----------------+
| Issue_id | issue_date | return_date | days_remaining |
+----------+------------+-------------+----------------+
|       12 |         12 |          30 |             18 |
|       32 |          1 |          30 |             29 |
|       45 |          9 |          29 |             20 |
|      123 |          7 |          31 |             24 |
|      189 |         11 |          31 |             20 |
|      215 |         10 |          31 |             21 |
|      255 |         15 |          30 |             15 |
|       90 |          4 |          24 |             20 |
+----------+------------+-------------+----------------+
mysql> insert into staff value(123789456,'Maria','Morning');
Query OK, 1 row affected (0.01 sec)

mysql> insert into staff value(456789123,'Palak','Evening');
Query OK, 1 row affected (0.05 sec)

mysql> insert into staff value(789456123,'Anant','Night');
Query OK, 1 row affected (0.01 sec)

mysql> select * from staff;
+-----------+------------+---------+
| Staff_Id  | Staff_name | shift   |
+-----------+------------+---------+
| 123789456 | Maria      | Morning |
| 456789123 | Palak      | Evening |
| 789456123 | Anant      | Night   |
+-----------+------------+---------+
3 rows in set (0.00 sec)
