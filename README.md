# Sequelize

[![npm version](https://badgen.net/npm/v/sequelize)](https://www.npmjs.com/package/sequelize)
[![Travis Build Status](https://badgen.net/travis/sequelize/sequelize?icon=travis)](https://travis-ci.org/sequelize/sequelize)
[![Appveyor Build Status](https://ci.appveyor.com/api/projects/status/9l1ypgwsp5ij46m3/branch/master?svg=true)](https://ci.appveyor.com/project/sushantdhiman/sequelize/branch/master)
[![npm downloads](https://badgen.net/npm/dm/sequelize)](https://www.npmjs.com/package/sequelize)
[![codecov](https://badgen.net/codecov/c/github/sequelize/sequelize?icon=codecov)](https://codecov.io/gh/sequelize/sequelize)
[![Last commit](https://badgen.net/github/last-commit/sequelize/sequelize)](https://github.com/sequelize/sequelize)
[![Merged PRs](https://badgen.net/github/merged-prs/sequelize/sequelize)](https://github.com/sequelize/sequelize)
[![GitHub stars](https://badgen.net/github/stars/sequelize/sequelize)](https://github.com/sequelize/sequelize)
[![Slack Status](https://sequelize-slack.herokuapp.com/badge.svg)](http://sequelize-slack.herokuapp.com/)
[![node](https://badgen.net/npm/node/sequelize)](https://www.npmjs.com/package/sequelize)
[![License](https://badgen.net/github/license/sequelize/sequelize)](https://github.com/sequelize/sequelize/blob/master/LICENSE)
[![semantic-release](https://img.shields.io/badge/%20%20%F0%9F%93%A6%F0%9F%9A%80-semantic--release-e10079.svg)](https://github.com/semantic-release/semantic-release)

This port to use with react native and expo.

NOTE: compatible with web but replace `dialectModule: SQLite` with `dialectModule: window`, and websql API in browser is limited (check TODO), catch all queries

TODO

- [ ] In web use sql.js

## Contributing

- Open Source!

## Example

```js
import React, { useEffect } from "react";
import { StyleSheet, Text, View, Platform } from "react-native";
import * as SQLite from "expo-sqlite";
import Sequelize from "rn-sequelize";
const Op = Sequelize.Op;
const Model = Sequelize.Model;

const sequelize = new Sequelize({
  dialectModule: SQLite,
  database: "mydb",
  dialectOptions: {
    version: "1.0",
    description: "Test DB"
    //size: 2 * 1024 * 1024
  }
});

class User extends Model {}
User.init(
  {
    name: Sequelize.STRING,
    email: Sequelize.STRING
  },
  {
    sequelize,
    modelName: "user"
  }
);
export default function App() {
  useEffect(() => {
    async function init() {
      try {
        await sequelize.sync({
          //force: true
        });

        await User.create({
          name: "Mike",
          email: "user@gmail.com"
        }).then(console.log);
      } catch (error) {
        console.log(error);
      }
    }
    init();
  }, []);

  return (
    <View style={styles.container}>
      <Text>Open up App.js to start working on your app!</Text>
    </View>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: "#fff",
    alignItems: "center",
    justifyContent: "center"
  }
});
```

## Thanks to Sequelize

# Sequelize

Sequelize is a promise-based Node.js ORM for Postgres, MySQL, MariaDB, SQLite and Microsoft SQL Server. It features solid transaction support, relations, eager and lazy loading, read replication and more.

Sequelize follows [SEMVER](http://semver.org). Supports Node v6 and above to use ES6 features.

New to Sequelize? Take a look at the [Tutorials and Guides](https://sequelize.org/master). You might also be interested in the [API Reference](https://sequelize.org/master/identifiers).

## Table of Contents

- [Installation](#installation)
- [Documentation](#documentation)
- [Responsible disclosure](#responsible-disclosure)
- [Resources](#resources)

## Installation

```bash
$ npm install --save sequelize # This will install v5

# And one of the following:
$ npm install --save pg pg-hstore # Postgres
$ npm install --save mysql2
$ npm install --save mariadb
$ npm install --save sqlite3
$ npm install --save tedious # Microsoft SQL Server
```

## Documentation

- [v5 Documentation](https://sequelize.org/master)
- [v4 Documentation](https://sequelize.org/v4)
- [v3 Documentation](https://sequelize.org/v3)
- [Contributing](https://github.com/sequelize/sequelize/blob/master/CONTRIBUTING.md)

## Responsible disclosure

If you have security issues to report please refer to our [Responsible Disclosure Policy](./SECURITY.md) for more details.

## Resources

- [Changelog](https://github.com/sequelize/sequelize/releases)
- [Slack](http://sequelize-slack.herokuapp.com/)
- [Stack Overflow](https://stackoverflow.com/questions/tagged/sequelize.js)

### Tools

- [Sequelize CLI](https://github.com/sequelize/cli)
- [Sequelize & TypeScript](https://sequelize.org/master/manual/typescript.html)
- [Enhanced TypeScript with decorators](https://github.com/RobinBuschmann/sequelize-typescript)
- [Sequelize & GraphQL](https://github.com/mickhansen/graphql-sequelize)
- [Add-ons & Plugins](https://sequelize.org/master/manual/resources.html)
- [Sequelize & CockroachDB](https://github.com/cockroachdb/sequelize-cockroachdb)

### Learning

- [Getting Started](https://sequelize.org/master/manual/getting-started)
- [Express Example](https://github.com/sequelize/express-example)

### Translations

- [English v3/v4/v5](https://sequelize.org) (OFFICIAL)
- [中文文档 v4/v5](https://github.com/demopark/sequelize-docs-Zh-CN) (UNOFFICIAL)
