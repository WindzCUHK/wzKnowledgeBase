# With ORM, you should be aware

http://blogs.tedneward.com/post/the-vietnam-of-computer-science/

Inheritance to relational
a. table-per-class
a. table-per-concrete-class
a. table-per-class-family

table-per-class
- class-table 1-to-1 mapping
- need unique ID for each object (PK)
- need JOIN to get all properties of the object
- JOIN is expensive in RDBMS

table-per-concrete-class
- denormalization
- may have data (or schema) consistency problem

table-per-class-family
- many null
- violate integrity constraints (some mandatory fields for some class need to allow null)
- discriminator column for class identification

Association to relational
- object: unidirectional
- relational: bidirectional, PK->FK, FK->PK
- m:n associations, need a third table...

Developer V.S. DBA
- object view <> relational view
- auto-report generation

Dual-schema problem
- object schema <> DB schema

Two layer of data
a. DB source (ACID)
a. object view (differenct across application intances, need sync. for consistency)
    - node-to-node broadcasting on update
    - data source broadcasting on update

Data Retrieval Mechansim
a. Query-By-Example (QBE)
    - no AND, OR, NOT
    - may need to allow null in mandatory fields
a. Query-By-API (QBA)
    - make query object (SQL-like)
    - need some hard-coded string (e.g. table names), but can use hybrid to solve
    - complexity, more complex than complex SQL @@
a. Query-By-Language (QBL)
    - new language
    - deep unstandard to optimize performance

Partial-Object Problem (network problem, select wanted columns only)
a. object should allow nullable fields
b. get all fields
c. on-demand load... (multiple query)
    - field-based (get field value 1-by-1)
    - object-based (all field or none field)

Some possible solutions
- no objects
- no relational DB
- manual mapping (with code generation)
- use ORM, but code your own when it fail u
- change your programming language, something more relational
- model your object in relational way (RowSet in Java)
