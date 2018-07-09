# Sqoop

- To find the hostname of the machine you are using use teh following command.
  ```
  hostname
  ```

- Sqoop is used to import data from a database to HDFS file system.

- Inorder to get the available commands for sqoop use `help` command.
  ```
  sqoop help
  sqoop help *command*
  ```
- To list all databses in MySQL using sqoop use `list-databases` command.
  ```
  sqoop list-databases \
  --connect jdbc:mysql://quickstart.cloudera:3306/ \
  --username retail_dba \
  --password cloudera 
  ```
- To list all tables in a MySQL database use the `list-tables` command.
  ```
  sqoop list-tables \
  --connect jdbc:mysql://quickstart.cloudera:3306/retail_db \
  --username retail_dba \
  --password cloudera 
  ```
- To run SQL queries from command line use `eval` command.
  ```
  sqoop eval \
  --connect jdbc:mysql://quickstart.cloudera:3306/retail_db \
  --username retail_dba \
  --password cloudera \
  --query "SELECT * FROM orders WHERE orders.order_id > 10 LIMIT 10"
  ```
- To import a single table from a database use `import` command. 
  - Using `--target-dir` argument will import the contents into the given address
  - Using `--warehouse-dir` will argument create a sub directory with table name in the given address and then imports the contents.
    ```
    sqoop import \
    --connect jdbc:mysql://quickstart.cloudera:3306/retail_db \
    --username retail_dba \
    --password cloudera \
    --table orders \
    --target-dir /user/cloudera/test 
    ```
    ```
    sqoop import \
    --connect jdbc:mysql://quickstart.cloudera:3306/retail_db \
    --username retail_dba \
    --password cloudera \
    --table orders \
    --warehouse-dir /user/cloudera/test 
    ```
  - To change the number of mappers during import use `--num-mappers` argument. 
    ```
    sqoop import \
    --connect jdbc:mysql://quickstart.cloudera:3306/retail_db \
    --username retail_dba \
    --password cloudera \
    --table orders \
    --num-mappers 1 \
    --target-dir /user/cloudera/test
    ```
      By default the number of mappers will be 4, but in the above example number of mappers will be 1. We can also use `-m` to assign the  number of mappers.

































































