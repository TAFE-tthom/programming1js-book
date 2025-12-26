# Persistent Data Storage

It is one thing to handle requests and keep the data in memory, it is another to keep data beyond an instance/run. Persistent data is required for any production server application.

This can be handled by using file IO in which data can be saved and recorded into that file. However, the standard practice is to use a database that will hold the data and manage writing and reading the data.


## Using a database and SQL

You can use the following sequelize module to interact with an sql database. Without needing to know much about SQL, you can create a sql database through javascript by constructing the tables and entries through javascript.

It requires the following stages to be performed.

1. Initialise a connection to the database
2. Construct types with fields specified and the relevant types
3. Synchronise the model created with the database

### Installing the dependency

Make sure you install the following dependencies using `npm`.

* `sequelize`
* `sqlite3`

Afterwards, you should be able construct a connection and database mode.


### Make a connection and define a model

Using the scenario of a `todo` application and needing to keep a list of tasks, along with their id, title, description and completion state. We will need to start with defining a new `sequelize` object.

```js
const sequelize = new Sequelize({
  dialect: 'sqlite',
  storage: './todo.db'
});
```

The above snippet uses the `sqlite` dialect of SQL and specifies the file to create or use (if it exists). Afterwards, we will create a `Task` type that can be instantiated and written back to.

```js
  
const Task = sequelize.define(
  'Task',
  {
    id: {
      type: DataTypes.INTEGER,
      autoIncrement: true,
      primaryKey: true,  
    },
    title: {
      type: DataTypes.STRING,
      allowNull: false,
    },
    description: {
      type: DataTypes.STRING,
      allowNull: false,
    },
    completed: {
      type: DataTypes.BOOLEAN,
      allowNull: false,
      defaultValue: false
    }
  },
);
```

The above snippet defines the type among with matching the fields to the type that SQL unuderstands. In this instance, the fields mostly resemble those we are familiar with in Javascript.

After the definition, you will need to `sync` the model with the database. You will need to use `await Task.sync()`.


### Writing and Reading

Writing and reading from the database will need to be done through `async/await` syntax and the API that `sequelize` provides. The convention that sequelize leans into is by using `find` for retrieval and `.save()` for writing on a newly instantiated object.

### Writing

Using the `Task` type that has been created prior, you will need to create a new object that matches that type. A common way is to use the static method associated with the type called `build` which will allow you to input the data needed.

```js
const task = Task.build({
  title: "New Task",
  description: "New Task has a description",
});
```

Since prior, `id` and `completed` are autoincrement (for `id`) and have a default value (for `completed`), it is not necessary to input this data. It is optional regardless though.

We are able to save the data by using `.save()` method on `task`.

```js
await task.save();
```

This will write it back to the database and can be queried directly.


### Reading

Once there is data within the database, it can be queried, this can be done through two methods. `findByPk` and `find*`, `findByPk` assumes that we know the primary key value of the object being search for. This will usually be the fastest and can be done like so.

```js
const task = await Task.findByPk(taskId);  
```

It will use the model type and the static method associated with it.


You can use `findAll` or just `find` to query the relevant table. WIthout any criteria specified, it will retrieve all the data, however you will need to specify `where` within the object to create predicates and exclude certain pieces of data.

```js
const results = await Task.findAll()
```

These are not particularly tricky but they may seem unintuitive on first use.
