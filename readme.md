### TS-Node-Dev

Automatically converts Typescript code into Javascript code. You should also add the following script package.json

```
"scripts": {
    "dev": "ts-node-dev src/server.ts",
},
```

#### Express Routes

Express routes defines from where certain functionalitiles can be accessed. The routes are accessed through URL, so for a route "/users" on a server running locally you may use "http://localhost:3333/users" to access it.

Each single route receives 3 informations: The method used (get, post, put, delete...) and two params. The first one is the name of the route, the second one the function with what the accessed route will do when a request is made and a response is sent.

Example:

- app.get("/", (request, response) => {
    return response.json ({ message: "Hello World - NLW04"});
});


### Database Management with Node.JS

#### Using Typeorm

- Getting started:
```
yarn add typeorm reflect-metadata pg
```

- You must also choose a database driver (such as PostgreSQL, MySQL, SQLite). Example:
```
yarn add sqlite3
```

- Config ormconfig.json
```
{
    "type": "sqlite",
    "database": "./src/database/database.sqlite"
}
```

#### Migrations

Migrations are documentations of what database commands were executed. It also contains the 'down' command which is used to revert the migration changes.

- Creating Migrations example:
```
new Table({
                name: "users",
                columns: [
                    {
                        name: "id",
                        type: "uuid",
                        isPrimary: true
                    },
                    {
                        name: "name",
                        type: "varchar"
                    }
})
```

### Controllers

Controllers are responsibles to create business rules for the database. It controls how the data will be read, changed, deleted and saved.

- routes.ts will get rules from Controllers and use in it's methods.

- server.ts:

```
app.use(express.json());
// Allows express to read json requests and responses
```

### Models

Models stablish the data structure of each entity. It also contains data generations strategies and relations between tables.

Example:

```
@Entity("users")
class User {

    @PrimaryColumn()
    readonly id: string;

    @Column()
    name: string;
}
```
where:
- @PrimariColumn sets column to primary key
- readonly tells that this kind of data cannot be changed
- string is the type of data