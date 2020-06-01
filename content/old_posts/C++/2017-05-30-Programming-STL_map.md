+++
title = "STL Map"
date = 2017-05-30
weight = 500
tags = ["STL", "map"]
+++

# STL Maps -- Associative Arrays

This is very useful to study the associative array in C++.
If you have used a variety of programming languages, sometimes it could be confusing which to use.
Associative Array is a different concept compare to C language.

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
