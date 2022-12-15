# Sequelize

## Table of Contents
- [What is ORM](#what-is-orm-)
- [Start with sequelize](#Start-with-sequelize)
- [Sequelize installation and connection](#sequelize-installation-and-connection)
    - [Sequelize connection](#sequelize-connection)
    - [What is dialect and other options](#what-is-dialect-and-other-options)
- [Create your first model (simple exercise)](#create-your-first-model--simple-exercise-)
    - [Initializing Sequelize](#initializing-sequelize)
    - [Model synchronization](#model-synchronization)
    - [Task over models]()
- [Associations](#associations)
    - [Creating the standard relationships](#creating-the-standard-relationships)
    - [Task goes here]()
- [Resources](#resources)


## What is ORM?

An `ORM` is known as Object Relational Mapper. This is a tool or a level of abstraction which maps(converts) data in a relational database into programmatic objects that can be manipulated by a programmer using a programming language(usually an `OOP` language). ORMs solely exist to map the details between two data sources which due to a mismatch cannot coexist together.

## Start with sequelize
Sequelize is a modern TypeScript and Node.js ORM for Oracle, Postgres, MySQL, MariaDB, SQLite and SQL Server, and more. Featuring solid transaction support, relations, eager and lazy loading, read replication and more.

## Sequelize installation and connection

```bash
npm install --save sequelize
```
### Sequelize connection

create an instance from sequelize and connect with connection url.

### What is dialect and other options
sequelize options
- dialect (database language)
- logging
A function that gets executed while running the query to log the sql.
    ```
    logging?: boolean | ((sql: string, timing?: number) => void)
    ```
- dialectOptions
the following options for postgres
    - ssl: SSL options. See the pg docs for details.
    - client_encoding: // Setting 'auto' determines locale based on the client LC_CTYPE environment variable. See the Postgres docs for details.



## Create your first model (simple exercise)
Define a model using [sequelize.define](https://sequelize.org/api/v6/class/src/sequelize.js~sequelize#instance-method-define)

### Initializing Sequelize
starting with sequelize by 
- creating an instance from sequelize.
- connect with your database.
- Sync your models.

### Model synchronization
When you define a model, you're telling Sequelize a few things about its table in the database. However, what if the table actually doesn't even exist in the database? What if it exists, but it has different columns, less columns, or any other difference?

This is where model synchronization comes in. A model can be synchronized with the database by calling `model.sync(options)`, an asynchronous function (that returns a Promise). With this call, Sequelize will automatically perform an SQL query to the database. Note that this changes only the table in the database, not the model in the JavaScript side.

- `User.sync()` - This creates the table if it doesn't exist (and does nothing if it already exists)
- `User.sync({ force: true })` - This creates the table, dropping it first if it already existed
- `User.sync({ alter: true })` - This checks what is the current state of the table in the database (which columns it has, what are their data types, etc), and then performs the necessary changes in the table to make it match the model.


**You can use `sequelize.sync()` to automatically synchronize all models.**

Let's start with [creating your first model](./create-your-first-model.md)

## Associations 
[Associations](https://sequelize.org/docs/v6/core-concepts/assocs/)
Sequelize supports the standard associations: `One-To-One`, `One-To-Many` and `Many-To-Many`.

To do this, Sequelize provides four types of associations that should be combined to create them:

- The `HasOne` association
- The `BelongsTo` association
- The `HasMany` association
- The `BelongsToMany` association

```js
A.hasOne(B, { /* options */ });
A.belongsTo(B, { /* options */ });
A.hasMany(B, { /* options */ });
A.belongsToMany(B, { through: 'C', /* options */ });
```

The order in which the association is defined is relevant. In other words, the order matters, for the four cases. In all examples above, `A` is called the **source model** and `B` is called the **target model**. This terminology is important.

The `A.hasOne(B)` association means that a *One-To-One* relationship exists between A and B, with the **foreign key** being defined in the target model **(B)**.

The `A.belongsTo(B)` association means that a *One-To-One* relationship exists between A and B, with the **foreign key** being defined in the source model **(A)**.

The `A.hasMany(B)` association means that a *One-To-Many* relationship exists between A and B, with the **foreign key** being defined in the target model **(B)**.

These three calls will cause Sequelize to automatically add foreign keys to the appropriate models (unless they are already present).

The `A.belongsToMany(B, { through: 'C' })` association means that a *Many-To-Many* relationship exists between A and B, using table C as junction table, which will have the foreign keys (aId and bId, for example). Sequelize will automatically create this model C (unless it already exists) and define the appropriate foreign keys on it.

### Creating the standard relationships
As mentioned, usually the Sequelize associations are defined in pairs. In summary:

- To create a **One-To-One** relationship, the `hasOne` and `belongsTo` associations are used together.
- To create a **One-To-Many** relationship, the `hasMany` and `belongsTo` associations are used together.
- To create a **Many-To-Many** relationship, two `belongsToMany` calls are used together

No lets start practice, [playing with associations](./model-associations.md)


## Resources
- [Intro to sequelize](https://medium.com/the-javascript-dojo/introduction-to-sequelize-1cbfc2d2d1bf)
- [Getting Started with Sequelize](https://sequelize.org/docs/v6/getting-started/)
- [Sequelize Model Basics](https://sequelize.org/docs/v6/core-concepts/model-basics/)
- [Associations](https://sequelize.org/docs/v6/core-concepts/assocs/)