+++
title = "Min-Max Median Heap"
date = 2016-10-19
weight = 400
tags = ["Heap", "MinMax-Heap", "Median-Heap"]
+++

One of the way of getting track of median in real-time: using two heaps (Min & Max heaps)

![Min-Max Median Heap](/images/algorithm/minmax/minmax.jpg)

Design of Algorithm:

	1. compare the value with median
	2. if the value is smaller than the median, insert it to Max heap,
	     else Min heap
	3. balance two trees: the difference of size of the node should be under 1,
		 otherwise, pop root from the bigger size heap and push it into smaller size heap.
	4. get Median value:
		 if same size of two heaps => median = (minRoot + maxRoot) >> 1,
            more nodes in max heap => median = minRoot,
            else median maxRoot
<br>


 # Latency comparison

 From the graph, the median using priority queue shows high latency compare to that of using an array. To program a priority queue, I used C++ queue library, and for an array, I made my implementation, swap node (write operation) every time it compares. So this algorithm could have been optimized as write operation takes more time than read(access) operation.

![gnuplot](/images/algorithm/minmax/heap.png)
