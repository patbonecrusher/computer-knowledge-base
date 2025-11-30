---
creation date: 06/11/2025
tags:
  - database
  - graph-database
  - genealogy
  - learning
subject: databases
source: github
---

# 🕸️ Neo4j

Graph database platform for managing connected data and relationships.

## Related Topics

- [[02-subjects/genealogy/genealogy|Genealogy Research]] - Using Neo4j for family trees
- [[02-subjects/databases/databases|Databases]]

## Getting started

```shell
brew install neo4j
brew install --cask neo4j

neo4j start

# follow prompt
```


```cardlink
url: https://github.com/sylhare/family-tree/tree/master/examples/neo4j/javascript/movies-javascript-bolt-master
title: "family-tree/examples/neo4j/javascript/movies-javascript-bolt-master at master · sylhare/family-tree"
description: "Family tree made with neo4j. Contribute to sylhare/family-tree development by creating an account on GitHub."
host: github.com
favicon: https://github.githubassets.com/favicons/favicon.svg
image: https://opengraph.githubassets.com/64fb4567e4b1077642923c7c0cfd7c1a729ee39e944d5f5a280426a72a3d0b43/sylhare/family-tree
```

![Family Tree Graph](_attachments/Pasted%20image%2020250611223027.png)


### notes

**to switch database**

```graphql
:use system
```