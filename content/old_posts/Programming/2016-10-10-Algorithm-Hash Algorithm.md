---
title: "Hashmap VS Hashset (including HashMulti)"
header:
  image: images/main_algorithm1.jpg
  teaser: images/hashtag_640.jpg
  caption: "Photo credit: [**pixabay**](https://pixabay.com)"
tag:
  - Hash
  - Hashtable
  - Hashset
  - Hashmap
  - HashMultiset
  - HashMultimap
  - Map
  - Set
  - Algorithm
categories:
  - Algorithm
---

# map and set with and without hash

Dealing with key value is widely used in data world but there are many terms such as hashmap and hashset based on its structure including those which do not have hash in front of the words. Then what are the difference?

## Hash(unordered) versus Non-hash

This is about ordering data which could cause performance. When inserting and deleting data, non-hash classes (such as map and set) sort data; therefore, it takes longer processing time than hash or unordered method. On the contrary,
using hash method, even though elements are not ordered, it uses its hash feature to search data quickly.

## MAP versus SET

The biggest difference is that SET contains only the key in contrast to the MAP which contains key and value.
For the key duplication, both of these do not allow duplicate keys. When it is attempted, data is dropped. To have multiple duplicated keys, multiset and multimap could be used.


## Confusion
I believe someone who programs both Java and C++/C# sometimes have confusion. Due to the complexity of the language, terminology could also bring confusion: using hashtable, hashmap and hashset in Java is different to those in C++ (Concept is similar though).

By my investigation, **in Java**, it seems more focused on having synchronization, and thread-safe as well as of course data structure. The detail is shown below:

|                   |  Hashtable | Hashmap | Hashset |
|-------------------| ---------- | ------- |-------- |
|**Synchronized**   | O          | X       | X       |
|**Key duplication**| X          | X       | X       |
|**Allows Null**    | X          | O       | O       |

To allow duplicated keys, use class such as HashMultiMap / Hash MultiSet


In **C++ STL**, Mutex is needed to have a synchronization.
