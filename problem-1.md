# Problem Statement 1
Be careful what you wish for: SQL is a literal genie.

**Requirements:**
- Postgresql 14+

**Problem Goal:** 
- Optimize the SQL query to run faster while providing the same functionality.

**Problem Description:**
![Problem 1](/assets/problem1.png "Problem 1")

The Score table stores scores of players present in the Users table. The score of a player can be the same as that of another player. The following query generates the rank (starting from 1) for a given player.

```
SELECT
	player_score."rank"
FROM
(
	SELECT id, ROW_NUMBER() OVER (ORDER BY score.score DESC, score.user_id) AS "rank"
	FROM
		score
	INNER JOIN 
		"user" ON "user".id = score.user_id
) AS player_score
WHERE 
	player_score.user_id = $1;
```

Optimize this query, while explaining any methods/tools you use.