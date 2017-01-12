# popularArticle
Sort popular articles with MySQL

### Let's say
Let's say there is simple table which have columns as like below.

    | id | title | crdate | read_cnt | voted_cnt |
    ----------------------------------------------
    | 1  | hello | 2016.. | 34       | 12        |


### Query
    SELECT  id
            ,title
            ,crdate
            ,LOG10(ABS(read_cnt) + 1) / 2 * SIGN(read_cnt)
						  + LOG10(ABS(voted_cnt) + 1) * SIGN(voted_cnt) 
							+ (UNIX_TIMESTAMP(crdate) / 300000) as popular
    FROM  articles
    ORDER BY  popular DESC
