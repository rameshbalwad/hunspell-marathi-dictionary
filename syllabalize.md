
```
The contents of the word_list will be given in a .sql dump file.
We can use syllabalize python script available from silpa to break-up each character and return the position in the second table called "syllabalize". 

http://smc.org.in/silpa/Syllabalize

The python source code of this module can be checked here...

https://gist.github.com/950405

The contents of the input table word_list are given below as well as the contents of the expected table syllabalize are also available. 
There can be 1 lakh words in word list with average length of 5, so the expected row count of second table will be around half million. 

Table: word_list
word_id word
1 सभी
2 बच्चे
3 किताब
4 पढते
5 है

Table: syllabalize
word_id char_seq character
1 1 स
1 2 भी
2 1 ब
2 2 च्चे
3 1 कि
3 2 ता
3 3 ब
4 1 प
4 2 ढ
4 3 ते
5 1 है

drop table if exists word_list;
create table word_list (word_id int not null auto_increment, word varchar(255), primary key (word_id)) ENGINE=InnoDB DEFAULT CHARSET=utf8;
insert into word_list (word) values ('सभी'), ('बच्चे'), ('किताब'), ('पढ़ते'), ('हैं');

drop table if exists syllabalize;
create table syllabalize (word_id int, char_seq int, word_char varchar(50), unique key `word_seq` (word_id, char_seq), foreign key (word_id) references word_list(word_id)) ENGINE=InnoDB DEFAULT CHARSET=utf8;
insert into syllabalize values (1, 1, 'स'), (1, 2, 'भी'), (2, 1, 'ब'), (2, 2, 'च्चे'), (3, 1, 'कि'), (3, 2, 'ता'), (3, 3, 'ब'), (4, 1, 'प'), (4, 2, 'ढ़'), (4, 3, 'ते'), (5, 1, 'हैं');
```