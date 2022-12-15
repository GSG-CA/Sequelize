## Association Task
Not let's assume that authors have published books.

Create a book model as follows:

![](https://i.imgur.com/DRlrBzP.png)

make sure that author has many books, but book has one author.
**let sequelize manage association, So don't create foreign Key by yourself.**

- insert data at `books.json`.
- find books start within `a`, and get author name.
- delete author with id `33`, and make sure to delete books related to this user
- try to insert new book without `authorId`, Does it success? If yes find away  to make foreignKey as a required value. 
- find all books for author with name `Joan Greer`.
- count all books for female authors.
- get top three `novel` books.

