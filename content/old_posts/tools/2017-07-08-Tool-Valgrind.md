+++
title = "valgrind"
date = 2017-07-08
weight = 400
tags = ["memory-leak", "valgrind"]
+++

# Valgrind

Just note one of the useful memory management tool checker tool:

This detects memory erros such as memory-leak and gives information about those.

Example:

    $ valgrind --tool=memcheck ./a.out -v

    ==15832== HEAP SUMMARY:
    ==15832==     in use at exit: 1,000,240 bytes in 3 blocks
    ==15832==   total heap usage: 3 allocs, 0 frees, 1,000,240 bytes allocated
    ==15832==
    ==15832== LEAK SUMMARY:
    ==15832==    definitely lost: 1,000,240 bytes in 3 blocks
    ==15832==    indirectly lost: 0 bytes in 0 blocks
    ==15832==      possibly lost: 0 bytes in 0 blocks
    ==15832==    still reachable: 0 bytes in 0 blocks
    ==15832==         suppressed: 0 bytes in 0 blocks
    ==15832== Rerun with --leak-check=full to see details of leaked memory
    ==15832==
    ==15832== For counts of detected and suppressed errors, rerun with: -v
    ==15832== ERROR SUMMARY: 0 errors from 0 contexts (suppressed: 0 from 0)

If you want to see it in detail, add --leak-check=full option.

# Note
On raspbian Jessie, it crashes due to some shared libraries of arm-linux-gnueabihf toolchain.

# Reference

valgrind Homepage: http://valgrind.org/
