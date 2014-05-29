---
Description: ""
Keywords:
- Development
- MongoDB
- Ruby
- Python
- Node.js
- Scala
- Java
- php
Tags:
- Development
- MongoDB
- Ruby
- Python
- Node.js
- Scala
- Java
- php
Title: 9 MongoDB 2.6 Drivers Released
Topics:
- Development
- MongoDB
date: 2014-04-07
---

I’m pleased to announce the coordinated release of drivers in 9
languages in preparation for the release of  MongoDB 2.6. This is the
largest driver release in the history of MongoDB, both in terms of code
changes as well as in terms of drivers released. Official Drivers for C,
C++, C# (.net), Java, Node.js, PHP, Python, Ruby and Scala were all
released with Perl following shortly. In the upcoming weeks community
drivers  will be updated to take advantage of the new features present
in MongoDB 2.6. With both community and official drivers MongoDB is
supported in over two dozen languages and platforms.

The new drivers support the following features:

## Write Operations
- Full support for the new MongoDB [Bulk Operations](http://docs.mongodb.org/master/reference/method/Bulk/#Bulk)
- Seamless Support for the new MongoDB [Write Operations](http://docs.mongodb.org/master/release-notes/2.6/#new-write-operation-protocol)

## Aggregation Improvements
- Writing [aggregation results to a collection](http://docs.mongodb.org/master/release-notes/2.6/#aggregation-enhancements)
- [Aggregation cursors](http://docs.mongodb.org/master/release-notes/2.6/#aggregation-enhancements)
- Improved [aggregation sorting](http://docs.mongodb.org/master/release-notes/2.6/#aggregation-enhancements)
- [Aggregation explain](http://docs.mongodb.org/master/release-notes/2.6/#aggregation-enhancements)

## Security Improvements
- [x.509 Authentication](http://docs.mongodb.org/master/release-notes/2.6/#security-improvements)
- [LDAP Support for Authentication](http://docs.mongodb.org/master/release-notes/2.6/#ldap-support-for-authentication)
- Support for (server side) [parallel collection scanning](http://docs.mongodb.org/master/reference/command/parallelCollectionScan/)

## General Improvements
- [Text Search](http://docs.mongodb.org/master/release-notes/2.6/#text-search-integration)
- Support for [Server Side Query Timeouts](https://jira.mongodb.org/browse/SERVER-2212)
- Better [Index Creation](http://docs.mongodb.org/master/release-notes/2.6/#index-build-enhancements)

A more complete list can be found on the [MongoDB 2.6 Release Notes](http://docs.mongodb.org/master/release-notes/2.6/)

In addition to these general feature individual improvements were made
to each driver. Please refer to the release notes of each individual
driver (linked below):

- [C 0.94.0](https://github.com/mongodb/mongo-c-driver/releases)
- [C++ 0.0-2.6](https://github.com/mongodb/mongo-cxx-driver/releases)
- [C# 1.9.0](https://github.com/mongodb/mongo-csharp-driver/releases)
- [Casbah 2.7.0](http://mongodb.github.io/casbah/whats_new.html#casbah-2-7-and-mongo-db-2-6-features) (Scala)
- [Java 2.12.0](https://github.com/mongodb/mongo-java-driver/releases)
- [Node 1.4.0](https://www.npmjs.org/package/mongodb)
- [Python 2.7](http://api.mongodb.org/python/current/changelog.html)
- [PHP 1.5.0](http://pecl.php.net/package/mongo/1.5.0)
- [Ruby 1.10.0](https://github.com/mongodb/mongo-ruby-driver/releases)

