There are cases when the word can be written by adding a zero-width space anywhere in it.
For e.g.

select char\_length('फटाक्यांची'), char\_length('फटाक्‍यांची');

10     11

As you can see the first one has only 10 characters in it while the second word has 11 and both look the same and google indexes both the words as same.

But since there is an extra character in it the second word is treated differently in the database. I found that both the words were in the database and both were marked as correct. Let's find out where exactly the zero-width space is hidden in the second word.

```
SELECT substring( 'फटाक्यांची', -10, 1 ) AS one, substring( 'फटाक्यांची', -9, 1 ) AS two, substring( 'फटाक्यांची', -8, 1 ) AS three, 
substring( 'फटाक्यांची', -7, 1 ) AS four, substring( 'फटाक्यांची', -6, 1 ) AS five, substring( 'फटाक्यांची', -5, 1 ) AS six, 
substring( 'फटाक्यांची', -4, 1 ) AS seven, substring( 'फटाक्यांची', -3, 1 ) AS eight, substring( 'फटाक्यांची', -2, 1 ) AS nine, 
substring( 'फटाक्यांची', -1, 1 ) AS ten
 									
फ 	ट 	ा 	क 	् 	य 	ा 	ं 	च 	ी

SELECT substring( 'फटाक्‍यांची', -11, 1 ) AS one, substring( 'फटाक्‍यांची', -10, 1 ) AS two, substring( 'फटाक्‍यांची', -9, 1 ) AS three, 
substring( 'फटाक्‍यांची', -8, 1 ) AS four, substring( 'फटाक्‍यांची', -7, 1 ) AS five, substring( 'फटाक्‍यांची', -6, 1 ) AS six, 
substring( 'फटाक्‍यांची', -5, 1 ) AS seven, substring( 'फटाक्‍यांची', -4, 1 ) AS eight, substring( 'फटाक्‍यांची', -3, 1 ) AS nine, 
substring( 'फटाक्‍यांची', -2, 1 ) AS ten, substring( 'फटाक्‍यांची', -1, 1 ) AS elevan


फ  	ट  	ा  	क  	्  	‍  	य  	ा  	ं  	च  	ी
```

So, obviously the word with extra blank character at the sixth place is wrong and should be removed. The following query was used to find out how many such words are there.

SELECT word FROM wordbase where word like concat('%', substring( 'फटाक्‍यांची', -6, 1 ), '%')

Around 1024 words found. The following query was used to remove them.

delete FROM wordbase where word like concat('%', substring( 'फटाक्‍यांची', -6, 1 ), '%') limit 1100