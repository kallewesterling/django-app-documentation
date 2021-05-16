# MySQL settings

Currently, we're running the Curriculum website in a `sqlite` solution, but it's on [the roadmap](/roadmap.md) to implement MySQL. Thus, the following information will be important.

In order for MySQL to work, you will need to follow these steps.

## Step 1: Create the file

In the `root` directory (the folder `curriculum.dhinstitutes.org` after you SSH into the Reclaim server), place a plain file called `sql.cnf`

## Step 2: Fill out the information

```
[client]
database = <database name>
user = <user with access>
password = <password for username>
default-character-set = utf8
host = dhinstitutes.org
port = 3306
sql_mode = STRICT_TRANS_TABLES
```

!!! info

    `database` in the file used to be `dhinstit_curriculum` so that might work for you as well.

