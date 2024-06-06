# node-express-sequelize-mysql-api-crud
Build REST API for CRUD Operations with Node, Express, Sequelize &amp; MySQL

```bat
mkdir node-express-sequelize-mysql-api-crud
cd node-express-sequelize-mysql-api-crud

npm init -y

npm i express sequelize mysql2 cors --save
```

package.json
```json
{
  "name": "express-sequelize-mysql-api-crud",
  "version": "1.0.0",
  "description": "Build REST API for CRUD Operations with Node, Express, Sequelize &amp; MySQL",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "dependencies": {
    "cors": "^2.8.5",
    "express": "^4.19.2",
    "mysql2": "^3.10.0",
    "sequelize": "^6.37.3"
  }
}
```

index.js
```javascript
const express = require("express");
const cors = require("cors");
const app = express();

app.use(cors({
    origin: "http://localhost:8081"
}));

// parse requests of content-type - application/json
app.use(express.json());

// parse requests of content-type - application/x-www-form-urlencoded
app.use(express.urlencoded({ extended: true }));

// base path
app.get("/", (req, res) => {
    res.json({ message: "Hello World!" });
});

require("./app/routes/tutorial")(app);

// set port, listen for requests
const PORT = process.env.PORT || 8080;
app.listen(PORT, () => {
    console.log(`Server is running on port ${PORT}.`);
});
```

```bat
node index.js
```