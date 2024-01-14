---
layout: post
title:  Building a GraphQL HTTP server with Express and MongoDB
date:   2023-12-05 16:40:16
description: 
tags: GraphQL Express HTTP
categories: 
---

GraphQL has become a popular choice for building APIs due to its flexibility and efficiency in data retrieval. 
In this post, we'll explore a GraphQL server implemented using Express, backed by a MongoDB database.
Specifically, we'll create a robust API to manage players and matches for a hypothetical gaming platform.

Check this code link: [https://github.com/ngcxy/GraphQL-HTTP-Express]

(Source: adapted from several assignments of source [USC EE547](https://web-app.usc.edu/soc/syllabus/20221/31250.pdf))

> Background

We choose **Express.js** Framework to set up our API endpoints, and **MongoDB** to store our data.

The setup for **Express.js** is as follows, in which we initialize an instance of **Express.js** as `app`:

```javascript
const express = require('express');
const PORT = 3000;

const app = express();
app.use(express.json());
app.use(express.urlencoded({ extended: true }));
app.use(express.static("public"));
```

The setup for **MongoDB** is as follows, in which we import the `mongodb` and the config file (it's ok if there's no config file):

```javascript
const { MongoClient, ObjectId} = require("mongodb");
const MONGO_CONFIG_FILE = `./config/mongo.json`;
```

> Main Operations

In the `SourceMongo` class lie main operations for "players" and "matches" in the database.

Before assigning the functions, the first thing we need to do is to config our database.

```javascript
    constructor(FILEPATH){
        try{
            this.config = require(FILEPATH);
        }
        catch{
            this.config = {
                "host":"localhost",
                "port":"27017",
                "db":"dbname",
                "opts":{
                    "useUnifiedTopology":true
                }
            }
        }
        const uri = `mongodb://${this.config.host}:${this.config.port}`;
        const client = new MongoClient(uri, this.config.opts);
        try {
            const database = client.db("dbname");
            this._db = database;
            const player = database.collection("player");
            const match = database.collection("match");
        } catch (err) {
            process.exit(5);
        }
    };
```

Then we are able to create operations including:

<ul>

    <li>createPlayer</li>

    <li>getPlayers/getPlayer</li>

    <li>getPlayerMatchInfo</li>

    <li>updatePlayer</li>

    <li>deletePlayer</li>

</ul>

<ul>

    <li>createMatch</li>

    <li>getMatches/getMatche</li>

    <li>dqPlayer(disqualify a player in the match)</li>

    <li>awardPlayer</li>

    <li>endMatch</li>

</ul>

You can view these functions in the code through the link.

#### * More classes: Validator, Error, and Decorator

---
These are the additional classes that help keep our code more organized - understandable manageable. 
`Validator` is used to validate the value of the input. 
`Error` serves to give specific feedback about what error takes place.
`Decorator` rearrange the information into the object with form we expect.

By separating these classes, we're able to reuse several functions and modify quickly in our code.

---

> GraphQL Implementation

In GraphQL, the building blocks of your API are defined using three key concepts: **typeDefs** (type definitions),**resolvers**, and **schema**.

#### typeDefs

Type definitions define the data types available in the GraphQL API. 
They include object types, input types, enums, queries, mutations, and other elements.
In Express.js, it is a string containing the GraphQL schema.

Our typeDefs contains two main part:

```text
type Query {
  # operations for query, with required params and return type
  # for example
  players(
    limit:      Int    
    offset:     Int    
    sort:       String          
    is_active:  Boolean
    q:          String
  ): [Player]!  
}
```
```text
type Mutation {
  # operations for mutation, with required params and return type
  # for example
  matchCreate(
    pid1:                ID!
    pid2:                ID!
    entry_fee_usd_cents: Int!
    prize_usd_cents:     Int!
  ): Match  
}
```

and other necessary elements:

<ul>

    <li>type Player, type Match</li>

    <li>some inputs with type</li>

    <li>types for additional use, e.g., dashboard</li>

</ul>

#### resolvers

Resolvers take the responsibility to actually handle the queries and mutations - they are functions that interact with our database operations. 
Each field in the schema has a corresponding resolver function that determines how to retrieve or calculate the data.

The resolvers are created like this:

```javascript

const resolvers = {
    Mutation: {
        playerCreate: async (obj, { playerInput }, DB) => {
            const b = playerInput;
            let error = e.error_post_player(b.fname, b.lname, b.handed, b.initial_balance_usd_cents);
            if (error.length === 0) {
                const player =  await db.createPlayer(b.fname, b.lname, handedURL2Data[b.handed], true, b.initial_balance_usd_cents);
                return player;
            } else {
                e.error_print(error);
                throw new Error();
            }
        },
        playerUpdate: async (obj, { pid, playerInput }, DB) => {
            let is_active = d.deco_is_active(playerInput.is_active);
            let lname = playerInput.lname ?? null;
                return db.updatePlayer(pid, lname, is_active, null);
        },
        
        // other mutations...
        
    },

    Query: {
        player: async ({}, { pid }, DB) => {
            return await DB.getPlayer(pid);
        },

        players: async ({}, { is_active, q }, DB) => {
            if (q !== undefined) {
                let name = decodeURIComponent(q.split(";")[0]);
                var vars = q.split(";")[1] || "fname,lname";
                return await DB.getNamePlayers(name, vars);
            }
            if (is_active == undefined || is_active == "*") {
                return await DB.getPlayers();
            } else {
                return DB.getSomePlayers(is_active);
            }
        },
        
        // other queries for match...
        
    },
};
```

#### Schema

When under Express.js framework, the `makeExecutableSchema` function from the `@graphql-tools/schema` library is used to combine typeDefs and resolvers into a GraphQL schema:

```javascript
const schema = makeExecutableSchema({
    resolvers,
    resolverValidationOptions: {
        requireResolversForAllFields: "warn",
        requireResolversToMatchSchema: "warn",
    },
    typeDefs,
});
```

Now, we successfully generate our schema, which is the overarching structure of the API.

---

Finally, we need to create the endpoint for graphQL. 
I also implement the GraphQL playground for Express.js, which is an interactive environment to where you can play around with GraphQL.

```javascript
app.all('/graphql', createHandler({ schema }));
app.get('/playground', expressPlayground({ endpoint: '/graphql' }));
app.get("/ping", (req, res) => {
    res.sendStatus(204);
});
app.listen(PORT);
```

After you start the server, you can find your API running on http://localhost:3000/graphql, and playground available on http://localhost:3000/playground



<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/post/1/qu.png" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/post/1/mu.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>