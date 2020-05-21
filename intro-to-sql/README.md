# QUESTIONS??????

# Thoughts on Databases, why do we need???

# Intro to SQL
1. Install the SQLite Browser if you haven't already [here](http://sqlitebrowser.org/)
2. Open the SQLite Browser and click 'File -> Open DataBase'
3. Choose the `chinook.db` file from this repo. This database is open source and maintained by Microsoft (SQL is no fun if you don't have any data).
4. Click the tab that says 'Execute SQL'. Type SQL queries in the box above. Press the play button. See the results of that query in the box below
5. Introduce CRUD

##Question :

## Challenges
1. Write the SQL to return all of the rows in the tists table?
```sql
```

2. Write the SQL to select the artist with the name "Black Sabbath"
```sql
SELECT * FROM artists WHERE name = 'Black Sabbath'
```

3. Write the SQL to create a table named 'fans' with an auto-incrementing ID that's a primary key and a name field of type text
```sql
CREATE TABLE fans (
  id INTEGER PRIMARY KEY,
  name TEXT
);
```

4. Write the SQL to alter the fans table to have a artist_id column type integer?
```sql
ALTER TABLE fans ADD COLUMN artist_id INTEGER;
```

5. Write the SQL to add yourself as a fan of the Black Eyed Peas? ArtistId **169**
```sql
INSERT INTO fans (name, artist_id) VALUES ('Bryce', 169)
```

6. Write the SQL to return fans that are not fans of (artist_id : 169).
```sql
SELECT * FROM fans WHERE artist_id != 196;
```

7. remove fans from our DB
```sql
DROP TABLE fans;
```

8. Write the SQL to display an artists name next to their album title
```sql
SELECT artists.name, albums.title
FROM artists INNER JOIN albums
ON artists.id = albums.artist_id
```

9. Write the SQL to display artist name, album title and number of tracks on that album
```sql
SELECT albums.title, artists.name, COUNT(tracks.album_id)
FROM albums JOIN artists, tracks
ON artists.id = albums.artist_id AND albums.id = tracks.album_id
GROUP BY (albums.title);
```

10. Write the SQL to return the name of all of the artists in the 'Pop' Genre
```sql
SELECT artists.name
FROM artists JOIN albums, tracks, genres
ON artists.id = albums.artist_id
AND albums.id = tracks.album_id
AND genres.id = genre_id
WHERE genres.name = 'Pop'
GROUP BY (artists.name);
```

## BONUS (very hard)

11. I want to return the names of the artists and their number of rock tracks
    who play Rock music
    and have more than 30 tracks -- stuck on this part
    in order of the number of rock tracks that they have
    from greatest to least
```sql
SELECT artists.name, COUNT(tracks.genre_id)
FROM artists
JOIN albums, tracks, genres
ON artists.id = albums.artist_id
AND albums.id = tracks.album_id
AND genres.id = genre_id
WHERE genres.name = 'Rock'
GROUP BY artists.name
HAVING COUNT(tracks.album_id) > 30
ORDER BY COUNT(tracks.genre_id) DESC;
```