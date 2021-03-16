ArangoDB Example graph data
===========================

This repository is created for ArangoDB learning purposes.

This repository contains datasets organized in graphs to be used with [ArangoDB](https://github.com/arangodb/arangodb).

More about ArangoDB and graphs: [Graph documentation](https://www.arangodb.com/docs/stable/graphs.html)

Debian Dependency Graph
========================

The [debian linux distribution](http://debian.org) consists of packages, which relate to each others by dependencies, which demand or recommend other packages to be installed.
Also conflicts are a possible relation, which prohibits two packages to be installed at once.
The script used to [gather this graph data is available alongside with pyarango](https://github.com/tariqdaouda/pyArango/blob/master/examples/debiangraph.py).
However, it takes a while to translate the debian package database into arangodb documents, so here is a dump of the Debian Jessie package database.

Since this is a dump of a complete database, you can use [`arangorestore`](https://www.arangodb.com/docs/stable/programs-arangorestore.html) to import this. We will create an own database `debianGraph` so it doesn't interfere with your existing data:

```
arangorestore --input-directory path-to-file//DebianDependencyGraph --create-collection true --include-system-collections true --create-database true --server.database debianGraph
```

Using the [ArangoDB graph viewer](https://github.com/arangodb/arangodb), we can browse random starting points in the graph:
![graph screenshot](DebianDependencyGraph/debian_dependency_graph.png)
