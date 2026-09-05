# MySQL and SQL

**Priority:** Very High · **Prerequisite:** [[01 - Programming Logic/README|Programming Logic]] · **Related:** [[06 - MongoDB/README|MongoDB]], [[17 - Security/README|Security]]

## Relational model

A relational database represents entities in tables and relationships through keys. A CRM may have `customers`, `leads`, `users`, `activities`, and `orders`. A primary key uniquely identifies a row. A foreign key references another table and can enforce referential integrity.

## SQL execution order

Although written as `SELECT ... FROM ... WHERE ... GROUP BY ... HAVING ... ORDER BY ... LIMIT`, a useful conceptual processing order is `FROM/JOIN`, `WHERE`, `GROUP BY`, `HAVING`, `SELECT`, `ORDER BY`, and `LIMIT`. This explains why a `SELECT` alias is not always available in `WHERE`.

## CRUD and safety

`INSERT` creates, `SELECT` reads, `UPDATE` changes, and `DELETE` removes. `TRUNCATE` removes all rows using a table-level operation in many systems. `DROP` removes the table definition. Before changing production data, use a transaction, an exact `WHERE`, and a backup or recovery plan.

## Filtering and aggregation

`WHERE` filters rows before aggregation. `GROUP BY` forms groups. `HAVING` filters groups. `COUNT(*)` counts rows; `COUNT(column)` generally ignores null values. `DISTINCT` removes duplicate result combinations. `NULL` represents unknown/missing data and requires `IS NULL` or `IS NOT NULL`.

## Joins and cardinality

An inner join keeps matches. A left join keeps every left row and matching right rows. A many-to-many relationship usually requires a junction table such as `customer_tags(customer_id, tag_id)`. Incorrect join conditions can multiply rows and inflate counts.

## Normalization and constraints

Normalization reduces repeated facts and update anomalies. First Normal Form requires atomic values; later normal forms reduce dependency problems. Practical designs may denormalize for reporting or performance, but duplication must be controlled. Use `NOT NULL`, `UNIQUE`, `CHECK`, `DEFAULT`, and foreign-key constraints to make invalid states harder to store.

## Indexes and query plans

An index is a lookup structure. Composite indexes follow leftmost-prefix considerations in many engines: an index on `(status, created_at)` is generally most useful when queries constrain `status` first. Selectivity, sorting, joins, and write frequency affect index choices. Use `EXPLAIN` to inspect a query plan. Functions on indexed columns and leading wildcards can prevent efficient index use.

## Transactions and isolation

ACID means Atomicity, Consistency, Isolation, and Durability. `COMMIT` persists; `ROLLBACK` undoes uncommitted changes. Isolation levels trade consistency for concurrency. Dirty reads, non-repeatable reads, and phantom reads are classic anomalies. Deadlocks can occur when transactions lock resources in inconsistent orders.

## Security

Prepared statements bind values separately from SQL syntax. Least-privilege database accounts reduce damage. Never build SQL by concatenating untrusted input. Also protect sensitive output and logs.

## Checklist

- [ ] Keys, constraints, relationships, cardinality
- [ ] SQL conceptual execution order
- [ ] CRUD, DELETE/TRUNCATE/DROP
- [ ] WHERE, GROUP BY, HAVING, ORDER BY
- [ ] COUNT and null behavior
- [ ] Joins and many-to-many junction tables
- [ ] Normal forms and controlled denormalization
- [ ] Indexes, composite indexes, EXPLAIN
- [ ] Transactions, isolation, deadlocks
- [ ] Prepared statements
