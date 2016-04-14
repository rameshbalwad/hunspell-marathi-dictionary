#Finding count of each character

# Introduction #
In order to find the incorrect word, we also need to find if certain characters does appear anywhere in the wordlist. The list of characters (मूळाक्षर) and it's count is listed on the following page.

http://spreadsheets.google.com/pub?key=tBJjzbcQB5i7tmfdO5Hk2DQ&output=html

As per the page above, the most popular character is र that appears 64926 times and least popular is ऐ that appears 361 times. I can also see that ङ is mentioned in 18 words. In order to find where does the ङ is used, I will query the table...

# Example #

`SELECT group_concat( word ) FROM wordbase WHERE word LIKE '%ङ%' AND verified > 0`

पराङ‌मुख,पराङ्मुख,वाङ्मय,वाङ्मयीन,वाङमय,वाङमयाकडे,वाङमयाच्या,दिङ्मूढ,वाङ्मयात,विचारवाङ्मय,
वाङ्मयउत्सव,वाङ्मयपरिषद,वाङ्मयपरिषदेच्या,वाङ्मयामध्ये,पंतवाङ्मयाचा,वाङ्‌मय,वाङ्मयाच्या,वाङ्मयावरुन

`SELECT group_concat(word) FROM wordbase WHERE word LIKE '%ॄ%' AND verified > 0 `

अभिवॄद्धी,अभिवॄद्ध्यर्थ,उपकॄत,घॄणा,पॄथ्वीचे,त्यादॄष्ट्या,दॄष्टीने,घॄष्णेश्वर,दॄष्टी,संस्कॄतीचे,
कॄती,त्यादॄष्टीने,निवॄत्त,वॄत्ती,वॄत्तीचा,वॄत्तीमुळे,गॄहपाठाच्या,चित्रपटसॄष्टीतील


# The query #
The following query was used to find the count of each character across all words.

```
DROP TABLE IF EXISTS int_table;

CREATE TABLE int_table(int_col int( 11 ) NOT NULL , PRIMARY KEY ( int_col )) ENGINE = MYISAM ;

INSERT INTO int_table VALUES ( 0 ) , ( 1 ) , ( 2 ) , ( 3 ) , ( 4 ) , ( 5 ) , ( 6 ) , ( 7 ) , ( 8 ) , ( 9 ) , ( 10 ) , 
( 11 ) , ( 12 ) , ( 13 ) , ( 14 ) , ( 15 ) , ( 16 ) , ( 17 ) , ( 18 ) , ( 19 ) , ( 20 ) , 
( 21 ) , ( 22 ) , ( 23 ) , ( 24 ) , ( 25 ) , ( 26 ) , ( 27 ) , ( 28 ) , ( 29 ) , ( 30 ) ;

DROP TABLE IF EXISTS akshar;

CREATE TABLE akshar SELECT int_col, SUBSTRING( s, int_col +1, 1 ) AS c 
FROM int_table, (SELECT word AS s FROM wordbase WHERE verified > 0) sel1
WHERE int_col < char_length( s ) ;

SELECT c AS mulakshar, count( * ) AS cnt FROM akshar GROUP BY c LIMIT 100

```


# Finding count of words

```
अं या अक्षराने सुरू होणारे सात अक्षरी शब्द
अंधारकारमय अंमलबजावणी अंशराशीकरण

खाली दिलेली क्वेरी वापरून ३ शब्द मिळवले.

SELECT word
FROM wordbase AS a
LEFT JOIN pratya AS b ON a.word LIKE concat( '%', myprat )
LEFT JOIN yogi AS c ON a.word LIKE concat( '%', myword )
WHERE verified >0
AND myprat IS NULL
AND myword IS NULL
AND 
char_length(
replace((replace ((replace ((replace ((replace ((replace ((replace ((replace ((replace ((replace ((replace ((replace((replace ((replace ((replace( word, 'ा', '' )), 'ि' , '' )), 'ी', '')), 'ु','')), 'ू' , '' )), 'े', '')), 'ै', '')), 'ो', '')) ,'ौ', '')), 'ं', '' )), 'ः', '')), '्', '')), 'ॄ', '')), 'ॢ', '')), 'ॣ', '')
) - (char_length(word) - char_length(replace( word, '्', '' ))) = 7 and word like 'अं%' 
limit 2000

```