# Parallel_Distributed_Programming
Parallel Implementation of Mergesort Algorithm 
We have the same tasks and different data, so it is a good idea to use single instruction multiple parallel implementation. At first we partition the data equally into processors, but sometimes data cannot be equally dividable by processors. In order to have equal local data in each processor, we add one to local_n, the quotient of the number of data (n) divided by the number of processors. And we have some new elements so we should assign them into zero. In order to calculate the number of new elements we subtract the local_n  from r, the remainder of the dividing the number of data by the number of processors. Afterwards, we generate the elements of data randomly. In order to generate some three-digit numbers we use the remainder of dividing random numbers by 1000. 

Broadcasting the data 
We use the function MPI-Broadcast to send the size of local_n to all processors and also allocate memory for them. And we use the function MPI Scatter to send the needed components to each of the other processors.
Afterwards, we call the sort function for all processors.

We use the tree structure global sum strategy to merge the sorted data in each processor to produce a merged sorted array. 
We need to find the pattern the rank of receiver and sender processors. If the rank of a processor is dividable by our step it receives the sorted array of the processor the rank of which is not dividable by the step, and merge it with its sorted array . We assign steps the multiples of 2. 

We calculate the CPU time by using the function Clock to measure the run-time of both serial and parallel implementations.    
