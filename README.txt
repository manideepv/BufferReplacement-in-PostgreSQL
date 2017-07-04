In the .zip folder, all the files that have been changed ae placed.
The files that have been changed are given as follows and all the changes in the code are mentioned with comments.
 
buf_inint.c
buf_internals.c
bufmrg.c
freelist.c

The difference between the given clocksweep algorithm and LRU is that, in case of LRU we do not make use of usage_count 
and therefore all code and declarations related to this are edited or commented out. In case of LRU we make use of a 
single refcount whose value when zero is considered to be available for replacement.
*In LRU, Buffer pointed by least recently used which is present at the head of the list is returned to the requesting thread.  
*If the freelist is empty, message will be logged and also in the case when buffer is available, it is logged 
and this is then returned to the requesting thread. For this purpose elog() functions are added to the code.
*A previous pointer is introduced and implemented, after getting the node from the head of the list. 
*Also changes have been made so that buffer is always added to the tail of the list in LRU.
*StrategyGetBuffer and StrategyFreeBuffer are present which make sure that appropriate page is released for replacement and
also that once a page is released it is added at the tail of the buffer.
*We add two new functions one for find whether buffer is present in the freelist to the freelist.c file.


