This project is for test DPDK's ring lockless performance.
I add a mutex lock in ring and test their performance. 
And use $RTE_SDK/app/test to test dpdk ring performance.
The cpu RDSTC is 2GH.
The result is following:

The lockless performance is :
```
RTE>>ring_perf_autotest
### Testing single element and burst enq/deq ###
SP/SC single enq/dequeue: 11
MP/MC single enq/dequeue: 47
SP/SC burst enq/dequeue (size: 8): 4
MP/MC burst enq/dequeue (size: 8): 9
SP/SC burst enq/dequeue (size: 32): 3
MP/MC burst enq/dequeue (size: 32): 4

### Testing empty dequeue ###
SC empty dequeue: 2.41
MC empty dequeue: 3.30

### Testing using a single lcore ###
SP/SC bulk enq/dequeue (size: 8): 4.64
MP/MC bulk enq/dequeue (size: 8): 9.54
SP/SC bulk enq/dequeue (size: 32): 3.45
MP/MC bulk enq/dequeue (size: 32): 4.62

### Testing using two hyperthreads ###
SP/SC bulk enq/dequeue (size: 8): 15.40
MP/MC bulk enq/dequeue (size: 8): 24.20
SP/SC bulk enq/dequeue (size: 32): 6.89
MP/MC bulk enq/dequeue (size: 32): 7.90

### Testing using two physical cores ###
SP/SC bulk enq/dequeue (size: 8): 30.26
MP/MC bulk enq/dequeue (size: 8): 64.44
SP/SC bulk enq/dequeue (size: 32): 12.70
MP/MC bulk enq/dequeue (size: 32): 20.16

### Testing using two NUMA nodes ###
SP/SC bulk enq/dequeue (size: 8): 55.61
MP/MC bulk enq/dequeue (size: 8): 183.63
SP/SC bulk enq/dequeue (size: 32): 21.95
MP/MC bulk enq/dequeue (size: 32): 51.76
Test OK
```
The locked ring permormance is :
```
RTE>>ring_perf_autotest
### Testing single element and burst enq/deq ###
SP/SC single enq/dequeue: 11
MP/MC single enq/dequeue: 173
SP/SC burst enq/dequeue (size: 8): 4
MP/MC burst enq/dequeue (size: 8): 25
SP/SC burst enq/dequeue (size: 32): 3
MP/MC burst enq/dequeue (size: 32): 8

### Testing empty dequeue ###
SC empty dequeue: 2.42
MC empty dequeue: 69.72

### Testing using a single lcore ###
SP/SC bulk enq/dequeue (size: 8): 4.64
MP/MC bulk enq/dequeue (size: 8): 25.60
SP/SC bulk enq/dequeue (size: 32): 3.41
MP/MC bulk enq/dequeue (size: 32): 8.59

### Testing using two hyperthreads ###
SP/SC bulk enq/dequeue (size: 8): 13.73
MP/MC bulk enq/dequeue (size: 8): 53.37
SP/SC bulk enq/dequeue (size: 32): 6.91
MP/MC bulk enq/dequeue (size: 32): 16.79

### Testing using two physical cores ###
SP/SC bulk enq/dequeue (size: 8): 30.18
MP/MC bulk enq/dequeue (size: 8): 141.87
SP/SC bulk enq/dequeue (size: 32): 12.66
MP/MC bulk enq/dequeue (size: 32): 37.86

### Testing using two NUMA nodes ###
SP/SC bulk enq/dequeue (size: 8): 60.75
MP/MC bulk enq/dequeue (size: 8): 422.54
SP/SC bulk enq/dequeue (size: 32): 21.97
MP/MC bulk enq/dequeue (size: 32): 113.99
Test OK

```