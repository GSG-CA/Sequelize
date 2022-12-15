## Define your first model

To create your first model, You need to install sequelize, create a postgres database, and connect sequelize with your db.

Now it's the time! Create the model below, with these specification:
- `id` is the primary key, serial and not null.
- `name`, `fname`, `email`, `password`, and `gender` must not be null.
- `gender` must be either male or female.
- `avatar` should have a default value as [profile picture](https://cdn.pixabay.com/photo/2015/10/05/22/37/blank-profile-picture-973460__480.png) 


![](https://i.imgur.com/dOOYTJG.png)



## Model Querying - Basics

create your first record, multi records, find by condition.


- **Insert data to your model**
There's attached [authors JSON file](./authors.json), try to insert these data to your model
  > hint:  
  search about `create`, and `bulkCreate`

- find female authors.
- find authors whose name start with `s` or `S`.
- find userID and password for author with email `aenean.eget@icloud.couk`
- update `avatar` for user with id `5`
- delete author with id `17`, `13`
- insert new author

