# Official website & Documentations:
http://wdb.freevar.com/ <br>
http://wdb.freevar.com/documentation.php

# QUICK USE
1) Include one of the following files in your script:
   src/WDB.php or vendor/autoload.php
  
  require "vendor/autoload.php";
  use \NCB01\WDB\WDB;

2) Create a WDB object

$db = new wdb(array(
  "server"  =>  "server_name",
  "port"    =>  "port_nummer", # optional
  "dbname"  =>  "db_name",
  "type"    =>  wdb::MYSQL,    # If you are under MYSQL or MariaDB
  "user"    =>  "user_name",
  "pswd"    =>  "passwort",
  "charset" =>  "charset",     # optional
));

If you want to use SQLite, it will be like this:

$db = new wdb(array(
  "type"    =>  wdb::SQLITE,
  "path"    =>  "path_to_db_file",  # optional
));

3) Selecting data with a shortened select
$where = array
(   "email"   => "some@email.com",
    "column3" => "some string",
    "column4" => 5
 
);
$db->select(
   "mytable",
   array
   (   "column1",
	   "column2",
   )
   $where
);

4) Selectinf data with a chained SELECT
$db->select($columns)
 ->from($table)
 ->join($tables_to_join)
 ->where($where)
 ->groupby($group_columns)
 ->having($condition)
 ->orderby($order)
 ->limit($nbr, $offset);
 
5) Retrieving results one by one. $row ist an array
while($row = $db->fetch()) var_dump($row);

6) Retrieving all results at once. $res is an array
$res = $db->fetchAll(); 

7) Deleting data with a condition
$db->delete("mytable", $where);

8) Deleting data with a list of ID values
$db->delete("mytable", "id_colum", $value1, $value2);

9) Updating data
$db->update(
   "mytable",
   array(
      "column1" => $value1,
      "column2" => $value2,
   ),
   $where
);
