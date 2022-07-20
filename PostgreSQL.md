# PostgreSQL

```text

PostgreSQL
    logs
        /usr/local/var/log/postgres.log
    libpq
        API
        engine for other APIs
    datatypes
        SERIAL
            PostgreSQL-specific datatype
                create auto-incrementing column
    cluster
        database(s)
            schema(s)
                has distinct namespace
                functions
                data types
                operators
                table(s)
    roles
        shared across cluster
    constraints
        UNIQUE constraint
            as column constraint
                value in the indicated column is unique across table
            as table constraint
                combination of values in the indicated columns is unique across table
            null == null evaluates into false

```

