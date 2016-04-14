
```
SELECT right( 'क', 1 ) , right( 'का', 1 ) , right( 'कि', 1 ) , right( 'की', 1 ) , right( 'कु', 1 ) , right( 'कू', 1 ) , 
right( 'के', 1 ) , right( 'कै', 1 ) , right( 'को', 1 ) , right( 'कौ', 1 ) , right( 'कं', 1 ) , right( 'कः', 1 ) , 
right( 'कृ', 1 ) , right( 'कॄ', 1 ) , right( 'कॢ', 1 ) , right( 'कॣ', 1 )


क 	ा 	ि 	ी 	ु 	ू 	े 	ै 	ो 	ौ 	ं 	ः 	ृ 	ॄ 	ॢ 	ॣ

drop table if exists swar;

CREATE TABLE `swar` (
   swar_id int not null auto_increment,
  `myswar` varchar(100) NOT NULL default '',
   PRIMARY KEY (swar_id),  
   KEY  (`myswar`)
) ENGINE=MyISAM DEFAULT CHARSET=utf8;

INSERT INTO `swar` (`myswar`) VALUES('');
INSERT INTO `swar` (`myswar`) VALUES('ा');
INSERT INTO `swar` (`myswar`) VALUES('ि');
INSERT INTO `swar` (`myswar`) VALUES('ी');
INSERT INTO `swar` (`myswar`) VALUES('ु');
INSERT INTO `swar` (`myswar`) VALUES('ू');
INSERT INTO `swar` (`myswar`) VALUES('े');
INSERT INTO `swar` (`myswar`) VALUES('ै');
INSERT INTO `swar` (`myswar`) VALUES('ो');
INSERT INTO `swar` (`myswar`) VALUES('ौ');
INSERT INTO `swar` (`myswar`) VALUES('ं');
INSERT INTO `swar` (`myswar`) VALUES('ः');
INSERT INTO `swar` (`myswar`) VALUES('ृ');
INSERT INTO `swar` (`myswar`) VALUES('ॄ');
INSERT INTO `swar` (`myswar`) VALUES('ॢ');
INSERT INTO `swar` (`myswar`) VALUES('ॣ');




drop table if exists vyanjan;

CREATE TABLE `vyanjan` (
   vyanjan_id int not null auto_increment,
  `akshar` varchar(100) default NULL,
   primary key(vyanjan_id),
   key (akshar) 
) ENGINE=MyISAM DEFAULT CHARSET=utf8;

INSERT INTO `vyanjan` (`akshar`) VALUES('क');
INSERT INTO `vyanjan` (`akshar`) VALUES('ख');
INSERT INTO `vyanjan` (`akshar`) VALUES('ग');
INSERT INTO `vyanjan` (`akshar`) VALUES('घ');

INSERT INTO `vyanjan` (`akshar`) VALUES('च');
INSERT INTO `vyanjan` (`akshar`) VALUES('छ');
INSERT INTO `vyanjan` (`akshar`) VALUES('ज');
INSERT INTO `vyanjan` (`akshar`) VALUES('झ');
INSERT INTO `vyanjan` (`akshar`) VALUES('ञ');


INSERT INTO `vyanjan` (`akshar`) VALUES('ट');
INSERT INTO `vyanjan` (`akshar`) VALUES('ठ');
INSERT INTO `vyanjan` (`akshar`) VALUES('ड');
INSERT INTO `vyanjan` (`akshar`) VALUES('ढ');
INSERT INTO `vyanjan` (`akshar`) VALUES('ण');

INSERT INTO `vyanjan` (`akshar`) VALUES('त');
INSERT INTO `vyanjan` (`akshar`) VALUES('थ');
INSERT INTO `vyanjan` (`akshar`) VALUES('द');
INSERT INTO `vyanjan` (`akshar`) VALUES('ध');
INSERT INTO `vyanjan` (`akshar`) VALUES('न');

INSERT INTO `vyanjan` (`akshar`) VALUES('प');
INSERT INTO `vyanjan` (`akshar`) VALUES('फ');
INSERT INTO `vyanjan` (`akshar`) VALUES('ब');
INSERT INTO `vyanjan` (`akshar`) VALUES('भ');
INSERT INTO `vyanjan` (`akshar`) VALUES('म');

INSERT INTO `vyanjan` (`akshar`) VALUES('य');
INSERT INTO `vyanjan` (`akshar`) VALUES('र');
INSERT INTO `vyanjan` (`akshar`) VALUES('ल');
INSERT INTO `vyanjan` (`akshar`) VALUES('व');
INSERT INTO `vyanjan` (`akshar`) VALUES('श');
INSERT INTO `vyanjan` (`akshar`) VALUES('ष');
INSERT INTO `vyanjan` (`akshar`) VALUES('स');
INSERT INTO `vyanjan` (`akshar`) VALUES('ह');
INSERT INTO `vyanjan` (`akshar`) VALUES('ळ');
INSERT INTO `vyanjan` (`akshar`) VALUES('क्ष');
INSERT INTO `vyanjan` (`akshar`) VALUES('ज्ञ');




SELECT b.akshar, a.myswar, concat( b.akshar, a.myswar ) AS mycharacter
FROM vyanjan AS b INNER JOIN swar AS a
ORDER BY vyanjan_id, swar_id


akshar 	myswar 	mycharacter
क 	  	क
क 	ा 	का
क 	ि 	कि
क 	ी 	की
क 	ु 	कु
क 	ू 	कू
क 	े 	के
क 	ै 	कै
क 	ो 	को
क 	ौ 	कौ
क 	ं 	कं
क 	ः 	कः
क 	ृ 	कृ
क 	ॄ 	कॄ
क 	ॢ 	कॢ
क 	ॣ 	कॣ
ख 	  	ख
ख 	ा 	खा
ख 	ि 	खि
ख 	ी 	खी
ख 	ु 	खु
ख 	ू 	खू
ख 	े 	खे
ख 	ै 	खै
ख 	ो 	खो
ख 	ौ 	खौ
ख 	ं 	खं
ख 	ः 	खः
ख 	ृ 	खृ


SELECT b.akshar, group_concat( concat( b.akshar, a.myswar ) ORDER BY swar_id ) AS mycharacter
FROM vyanjan AS b INNER JOIN swar AS a
GROUP BY b.akshar
ORDER BY vyanjan_id, swar_id


akshar 	mycharacter
क 	क,का,कि,की,कु,कू,के,कै,को,कौ,कं,कः,कृ,कॄ,कॢ,कॣ
ख 	ख,खा,खि,खी,खु,खू,खे,खै,खो,खौ,खं,खः,खृ,खॄ,खॢ,खॣ
ग 	ग,गा,गि,गी,गु,गू,गे,गै,गो,गौ,गं,गः,गृ,गॄ,गॢ,गॣ
घ 	घ,घा,घि,घी,घु,घू,घे,घै,घो,घौ,घं,घः,घृ,घॄ,घॢ,घॣ
च 	च,चा,चि,ची,चु,चू,चे,चै,चो,चौ,चं,चः,चृ,चॄ,चॢ,चॣ
छ 	छ,छा,छि,छी,छु,छू,छे,छै,छो,छौ,छं,छः,छृ,छॄ,छॢ,छॣ
ज 	ज,जा,जि,जी,जु,जू,जे,जै,जो,जौ,जं,जः,जृ,जॄ,जॢ,जॣ
झ 	झ,झा,झि,झी,झु,झू,झे,झै,झो,झौ,झं,झः,झृ,झॄ,झॢ,झॣ


No word can start with a swar. So the following words are incorrect.

िगडे 
िविवध 

The query to find such words...
SELECT * FROM wordbase AS a INNER JOIN swar AS b 
ON a.word LIKE concat( b.myswar, '%' ) WHERE b.swar_id !=1

```