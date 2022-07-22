# SQL

```text

SQL
    statements
        DDL = Data Definition Language
            CREATE
                CREATE DATABASE
                    creates new database by copying template1
                    constraints
                        PRIMARY KEY
                            indicates uniqueness of
                                column
                                set of columns
                            functionally almost the same as
                                UNIQUE NOT NULL
                            tables can have at most one
                            all tables should have one
                            useful for
                                documenting purpose
                                database clients
                        UNIQUE
                            ensures uniqueness
                            can be used to specify
                                column contraint
                                    ensures uniqueness of column value among all rows in table
                                table constraint
                                    ensures uniqueness of the combination of indicated columns' values
            ALTER
            DROP
            GRANT
            REVOKE
            ...
        DML = Data Manipulation Language
            DELETE
            INSERT
            UPDATE
            limited form
                SELECT
                    read only
            ...
        Transaction Control
            ROLLBACK
            ...
        Session Control
            ALTER SESSION
            SET ROLE
        System Control
            ALTER SYSTEM
        Embedded
            programming language
            SQL

```

