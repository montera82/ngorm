# Definitive Guide to Object Relational Mapping with ngorm

Welcome! Thanks you for taking your time to check out on ngorm. This is a rather
TL:DR doc which will walk you through all things necessary to get started with
ngorm. Please check godoc reference too, there is a lot of good details there.

Enjoy!

## Table of contents

- [Getting started](#getting-started)
 - [Installation](#installation)
 - [Connecting to databases](#connecting-to-database)
 - [Migrations](#migrations)
 - [Create](#create)
 - [Query](#query)
 - [Preload](#preload)
 - [Update](#update)
 - [Delete](#delete)
 - [Associations](#associations)
    - [Belogs To](#belongs-to)
    - [Has one](#has-one)
    - [Has many](#has-many)
    - [Many to many](many-to-many)
    - [Polymorphism](#polymorphism)

- [Advanced](#advanced)
 - [Hooks](#hooks)
 - [Logging](#logging)
 - [SQL building](#sql-building)
 - [SQL execution](#sql-execution)
 - [Transactions](#transactions)

- [Primer on `database/sql` package](#primer-on-database-sql-package)


# Getting started

NGORM is a fork of gorm. I initially forked gorm for the purpose of improving
performance, after navigating through the whole code base it dawned to me that
there was no straight way to benchmark and any efforts won't be conveying the
truth about what is happening.

Queries are executed using `database/sql` package, majority of the time is spent
generating the queries from models. So there can be two places for
benchmarking.

First is the code that is responsible to take models and generate SQl. Second is the
code that uses `database/sql` to run the queries i.e measure how fast/efficient
are the generated queries.

The second part is too broad and vague, and might have different outcomes based
on the nature of the database. So the focus of ngorm is to make sure all the
cases are addressed, in a way that  the library generates the best possible
queries for the supported databases.

## Installation

	go get -u github.com/gernest/ngorm