# SHOW

SHOW tables;

| Tables_in_elevage |
| ----------------- |
| Animal            |
| Espece            |
| Race              |

# DESCRIBE

DESCRIBE Animal;

| Field          | Type                 | Null | Key | Default | Extra          |
|----------------|----------------------|------|-----|---------|----------------|
| id             | smallint(6) unsigned | NO   | PRI | NULL    | auto_increment |
| sexe           | char(1)              | YES  |     | NULL    |                |
| date_naissance | datetime             | NO   |     | NULL    |                |
| nom            | varchar(30)          | YES  | MUL | NULL    |                |
| commentaires   | text                 | YES  |     | NULL    |                |
| espece_id      | smallint(5) unsigned | NO   | MUL | NULL    |                |
| race_id        | smallint(5) unsigned | YES  | MUL | NULL    |                |
| mere_id        | smallint(5) unsigned | YES  | MUL | NULL    |                |
| pere_id        | smallint(5) unsigned | YES  | MUL | NULL    |                |

DESCRIBE Espece;

| Field       | Type                 | Null | Key | Default | Extra          |
|-------------|----------------------|------|-----|---------|----------------|
| id          | smallint(5) unsigned | NO   | PRI | NULL    | auto_increment |
| nom_courant | varchar(40)          | NO   |     | NULL    |                |
| nom_latin   | varchar(40)          | NO   | UNI | NULL    |                |
| description | text                 | YES  |     | NULL    |                |

DESCRIBE Race;

| Field       | Type                 | Null | Key | Default | Extra          |
|-------------|----------------------|------|-----|---------|----------------|
| id          | smallint(5) unsigned | NO   | PRI | NULL    | auto_increment |
| nom         | varchar(40)          | NO   |     | NULL    |                |
| espece_id   | smallint(5) unsigned | NO   | MUL | NULL    |                |
| description | text                 | YES  |     | NULL    |                |

# Keys and Index

SHOW keys FROM Animal;

| Table  | Non_unique | Key_name              | Seq_in_index | Column_name |
|--------|------------|-----------------------|--------------|-------------|
| Animal |          0 | PRIMARY               |            1 | id          |
| Animal |          0 | ind_uni_nom_espece_id |            1 | nom         |
| Animal |          0 | ind_uni_nom_espece_id |            2 | espece_id   |
| Animal |          1 | fk_espece_id          |            1 | espece_id   |
| Animal |          1 | fk_race_id            |            1 | race_id     |
| Animal |          1 | fk_mere_id            |            1 | mere_id     |
| Animal |          1 | fk_pere_id            |            1 | pere_id     |

SHOW keys FROM Espece;

| Table  | Non_unique | Key_name  | Seq_in_index | Column_name |
|--------|------------|-----------|--------------|-------------|
| Espece |          0 | PRIMARY   |            1 | id          |
| Espece |          0 | nom_latin |            1 | nom_latin   |

SHOW keys FROM Race;

| Table | Non_unique | Key_name          | Seq_in_index | Column_name |
|-------|------------|-------------------|--------------|-------------|
| Race  |          0 | PRIMARY           |            1 | id          |
| Race  |          1 | fk_race_espece_id |            1 | espece_id   |
