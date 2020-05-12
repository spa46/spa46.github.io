---
title: "STL Map - C & C++"
header:
  image: images/main_algorithm1.jpg
  teaser: images/main_algorithm1.jpg
  caption: "Photo credit: [**pixabay**](https://pixabay.com)"
tag:
  - Dictionary
  - Map
  - STL
categories:
  - Programming
---

# STL Maps -- Associative Arrays

This is very useful to study associative array in C++.
If you have used variety of programming languages, sometimes it could be confusing which to use.
Associative Array is different concept compare to C language.

**map class** is part of the std namespace and to use it:

    std::map <key_type, data_type, [comparison_function]>

##### Assign
Unlike C, C++ uses associate strings.
For example, char type could be retrieved by strings:

    std::map<string, char> gradeList;
    gradeList["Sean"] = 'A';

##### Erase
gradeList["Sean"] = 'A';
gradeList.erase("Sean");

##### Find
Similar to normal search method:
std::map <string, char> gradeList;
gradeList["Sean"] = 'A';
if(gradeList.find("Tom") == gradeList.end())
{
    std::cout<<"Tom is not in the list"<<endl;
}


# Reference

http://www.cprogramming.com/tutorial/stl/stlmap.html
