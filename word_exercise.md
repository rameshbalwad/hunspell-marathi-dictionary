# एकाच अक्षराने तयार होणारे शब्द #

```
आपली मराठी भाषा ही अशी भाषा आहे ज्यामध्ये एकाच अक्षरापासून सुद्धा अर्थपूर्ण शब्द तयार होतात.
अशेच एकाच अक्षराने तयार होणारे शब्द सांगा 
जसे - तंतोतंत, बोंबाबोंब ई.
अट - शब्द तीन अक्षारी किंवा जास्त अक्षारी असावा.

http://www.manogat.com/node/20066


drop table if exists manogat;
CREATE TABLE `manogat` (`akshar` varchar(100) NOT NULL default '', 
  PRIMARY KEY  (`akshar`)
) ENGINE=MyISAM DEFAULT CHARSET=utf8;
INSERT INTO `manogat` VALUES ('अ'), ('अ:'), ('अं'), ('आ'), ('इ'), ('ई'), ('उ'), ('ऊ'), ('ए'), ('ऐ'), ('ओ'), ('औ'), ('क'), ('क्ष'), ('ख'), ('ग'), ('घ'), ('च'), ('छ'), ('ज'), ('ज्ञ'), ('झ'), ('ञ'), ('ट'), ('ठ'), ('ड'), ('ढ'), ('ण'), ('त'), ('थ'), ('द'), ('ध'), ('न'), ('प'), ('फ'), ('ब'), ('भ'), ('म'), ('य'), ('र'), ('ल'), ('ळ'), ('व'), ('श'), ('ष'), ('स'), ('ह'); 

drop table if exists manogat1;
create table manogat1 
select word, replace ((replace ((replace ((replace ((replace ((replace ((replace ((replace ((replace ((replace ((replace ((replace ((replace ((replace ((replace ((replace((replace ((replace ((replace( word, 'ा', '' )), 'ि' , '' )), 'ी', '')), 'ु','')), 'ू' , '' )), 'े', '')), 'ै', '')), 'ो', '')) ,'ौ', '')), 'ं', '' )), 'ः', '')), '्', '')), 'ॄ', '')), 'ॢ', '')), 'ॣ', '')), 'ॉ', '')), 'ॅ', '')), 'ृ', '')), 'ँ', '') as myword 
from wordbase where verified > 0;

alter ignore table manogat1 add primary key (myword);

select word, myword, count(*) as cnt from manogat1 inner join manogat where myword like concat('%', akshar, '%') group by myword HAVING cnt = 1
ORDER BY char_length( word ) DESC;

खाली दिलेले शब्द सापडले.
बोंबाबोंब चिंचेचा लालेलाल नानांना तंतोतंत
```