# Optimizing spell check query #

Here are 3 steps to optimize the spell check process.

1) Only the verified words are kept to keep the number of words as low as possible.

2) The table type can be changed to memory.

3) The verified column and indexes can be removed to keep the table size small.

http://saraswaticlasses.net/shabdasampada/

In order to make the spell options load faster on the above page, the following changes where made to the DB.

```
// after taking the backup of original wordbase table...
drop table if exists wordbase;
set max_heap_table_size = 4194304*20;

CREATE TABLE `wordbase` (
 `word` varchar(50) NOT NULL,
 PRIMARY KEY  (word)
) ENGINE=MEMORY;
insert into wordbase select word from wordbase1 where verified > 0  
```

The shabdasampada.inc file has references to the verified column. Therefore this file from /inc/ folder was updated and 4 references in the where clause were removed.