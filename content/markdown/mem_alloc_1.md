
Memory is allocated in chunks. There are multiple types of allocators including linear allocator, which as the name suggests allocates chunks one after the other and heap allocator, which assigns chunks of variable/dynamic size.

## Linear Allocator

Suppose we have a completely fresh **pool of memory**, which i will denote like so:

<center><b>[Free]-[Free]-[Free]-[Free]</b></center>

Here there are 4 **fixed-size** free slots. I now allocate a chunk of memory.

<center><b>[Chunk]-[Free]-[Free]-[Free]</b></center>

and 2 more so on.

<center><b>[Chunk]-[Chunk]-[Chunk]-[Free]</b></center> 

Now we deallocate the second the second chunk. We do this in O(1) time.

<center><b>[Chunk]-[Free]-[Chunk]-[Free]</b></center> 

For **allocating the a new chunk**, we will have to iterate from the beginning, find the first free slot and allocate. This takes **O(n)** time.
To fix this, we keep another array free[] which points to the free chunks. This allows us to check and allocate in less time. We can do this only because our chunks are of **fixed size**.


## Dynamic Allocator

Our memory pool now looks like this:

<center>[Free]-[++Free++]-[Fr]-[+Free+]</center>

As you can see all chunks are of different sizes.Now we allocate a new chunk like before. 
