all my GSoC works are in [pull request](https://github.com/MariaDB/mariadb_kernel/pull/29/commits) and [one commit](https://github.com/MariaDB/server/commit/768c51880a5aa6d25d4c0fe7de7a88561ff46422)

This project's autocompletion is based on popular python packages - mycli. And do some enhancement, bug fix, and extend its functionality.

## the list of my work(not list trivial commits)

### integrate mycli with mariadb_kernel
implement three main classes - 「SQLFetch, SQLAnalyze, Autocompleter」 describe in [this comment](https://github.com/MariaDB/mariadb_kernel/pull/29#issuecomment-872046209)
#### related commits
1. [implement SQLFetch class](https://github.com/MariaDB/mariadb_kernel/pull/29/commits/f41c29ee5f3625e98c8b5fa382cca18d1def2eee)
2. [Implement AutoCompleter and SQLAnalyze](https://github.com/MariaDB/mariadb_kernel/pull/29/commits/1e7e06f3fe368aea2019c02ceb25dbd3dbf24bad)
3. [Successfully create basic autocomplete feature on mariadb_kernel](https://github.com/MariaDB/mariadb_kernel/pull/29/commits/a237724b921652a4a2321a6d123afff438946e1b)
4. [fix not select any database error in SQLFetch](https://github.com/MariaDB/mariadb_kernel/pull/29/commits/9884b711828042269054fb3ba7d1e0d20f331c23)
5. [Refactor for SQL command position and SQLFetch.Refresher's arguments passing](https://github.com/MariaDB/mariadb_kernel/pull/29/commits/1dac33b7169956eea8ee494eff9cc419c69e63b8)
6. [let autocompletion can show the type of completion in the list](https://github.com/MariaDB/mariadb_kernel/pull/29/commits/9141aee44cec373048f491e0dfe6975d5d9550fd)
   
   https://user-images.githubusercontent.com/33860799/129854594-c5d235eb-d694-4b0c-8222-a85dce0b13a7.mp4
7. asyc refresh autocompleter's data
    1. [create basic async refresh by thread
](https://github.com/MariaDB/mariadb_kernel/pull/29/commits/178fc979a670e28e8171e33df9c00e6deca8b5a2)
    2. [Merge branch 'async_refresh' into integrated_with_mycli](https://github.com/MariaDB/mariadb_kernel/pull/29/commits/05f62b39140fb5de6d150c407d7d69615d38c703)

#### enhancement of mycli
1. can set the keyword and function list and would automatically fetch the lastest keyword and function list from new information_schema tables that work in my GSoC([link](https://github.com/MariaDB/server/commit/768c51880a5aa6d25d4c0fe7de7a88561ff46422)) -
    [commit](https://github.com/MariaDB/mariadb_kernel/pull/29/commits/9a01a4ec0ff7ae5dc0271b7342c16700bfccf1a1)
2. Database suggestion before 「.」. Ex: 「insert into db_name_to_be_completed.table_name VALUES (...) 」
    commit
    1. [Database suggestion before .table_name
](https://github.com/MariaDB/mariadb_kernel/pull/29/commits/8b04cf6f96b87239bf435a899287fa898d9a983a)
    2. [Enhancement of database suggestion before 「.」
](https://github.com/MariaDB/mariadb_kernel/pull/29/commits/f673cdcdee885bac4bcc0e27881bc4ab6e6b0ef6)
   
   https://user-images.githubusercontent.com/33860799/129856199-be2a40fc-5d51-4539-937a-5ccb4f1c52e8.mp4
3. add global and session variable suggestions
    commit
    1. [add global and session variable suggestion on completion_engine and update sql_fetch for them](https://github.com/MariaDB/mariadb_kernel/pull/29/commits/ce111a05a744772d7cd3e6a9e42acc6c9870cb2c)
    2. [Add global and session variable suggestions and fix some problem](https://github.com/MariaDB/mariadb_kernel/pull/29/commits/1984d90b1247b0eb325f76dfc5a3f7e93ca71eae)

   https://user-images.githubusercontent.com/33860799/129861325-a1f04cf6-c8ee-43b4-96b5-b836123bb0b2.mp4
4. enhancement of database suggestions
    commit
    1. [Add column suggest for system table like mysql.user. And fix the problem like 「select user, `<tab>` from mysql.user;」 would get a user list](https://github.com/MariaDB/mariadb_kernel/pull/29/commits/4430709f81d77a0ea6427e9bbd03fd40807415d7)
    2. [Autocompletion about database_name.table_name_to_be_completed could suggest the table not in currently seleted database](https://github.com/MariaDB/mariadb_kernel/pull/29/commits/2831635f7db6ee6b19bd4f9edde6f917a9e7aa38)
    3. [Autocompletion for database in select, insert into, ... , like statement
](https://github.com/MariaDB/mariadb_kernel/pull/29/commits/58ba70d856eef31d18492d7deb3919cebd0d384f)
5. fix some bugs related to the name `user` is the column name and keyword
    commits:
    1. [Autocompletion for keyword after user column name](https://github.com/MariaDB/mariadb_kernel/pull/29/commits/9c9a8e6fd718c6cfd323ad0ddec1ec550f28cf44)
6. Remove autocompletion suggest column name from a statement like 「insert into table_name values (<tab> 」
    commits:
    1. [Remove autocompletion suggest column name from statement like 「insert into table_name values (<tab> 」](https://github.com/MariaDB/mariadb_kernel/pull/29/commits/baaad7cb10532ab80a167a4f15b662557141d36f)
    2. [fix the bug for 【Remove autocompletion suggest column name from statement like 「insert into table_name values (<tab> 」】](https://github.com/MariaDB/mariadb_kernel/pull/29/commits/635a90e0df613ebca0e0045889a4701d94df4f77)
#### extend of autocomplete feature - introspection
1. [Complete basic introspection functionality](https://github.com/MariaDB/mariadb_kernel/pull/29/commits/dc288c7706fdc35de968c8fce7d94d5092de3e3f)
2. [Let introspection show some real data](https://github.com/MariaDB/mariadb_kernel/pull/29/commits/b0215f8ef5bde1503739d90cfa7114507e9bb72f)
3. [Change setup.py to include data folder and create a new feature about introspection provide column hint](https://github.com/MariaDB/mariadb_kernel/pull/29/commits/febd264e8a0e841aa850b5b84a22a9aea491c67d)
4. [feature about introspection provide column hint can handle multi values](https://github.com/MariaDB/mariadb_kernel/pull/29/commits/6bbbc123eb8ccef941411189c96a5afb8df87e45#diff-ba5fa5711361ceaf463bbfa8cf4a50b081727b471364ca32c88e8ac35b06c439R102)
5. [introspect function would provide documentation
](https://github.com/MariaDB/mariadb_kernel/pull/29/commits/c3dc53100c518b9bd70792163c87a2fbadf98ba7)
6. [introsptect user keyword would pop up user list
](https://github.com/MariaDB/mariadb_kernel/pull/29/commits/5f92f1824908cbba011c39dbf3ec7601f8d82df5)
7. [Merge branch use_mycli_for_introspection('febd264e8a0e841aa850b5b84a22a9aea491c67d') into integrated_with_mycli](https://github.com/MariaDB/mariadb_kernel/pull/29/commits/ddd84aea11645f8d2996d64758d333deb72ccd6e)
8. [Solve some introspection problems about the different type of words have the same name](https://github.com/MariaDB/mariadb_kernel/pull/29/commits/811c6dc1824b0e2c28e8399907801409c8a77e0e)

#### related to mariadb_kernel
1. [fix mariadb_client's run_statement courrent problem](https://github.com/MariaDB/mariadb_kernel/pull/29/commits/8abef4f116d0b3c0e899a4141b86312b2d69f2a7)
2. [Add more testing about mariadb_client concurrent execute run_statement and the multi mariadb_client's selected database sync](https://github.com/MariaDB/mariadb_kernel/pull/29/commits/3523bcdcb2a2697b986e0f3e09e7cc84f2ee7e09)
