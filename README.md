# hello-world
Initial repository  
I would like to write a bit

Since `\sum_{j=0}^{N-1} s^j = s^N-1/s-1,`  
`\sum_{j=0}^{N-1} (s-1) s^j = s^N-1`

If `s=2,`  
`\sum_{j=0}^{N-1} 1 * 2^j = 1...1B /* N bits */ = 2^N-1`  
If `s=16,`  
`\sum_{j=0}^{N-1} F * 16^j = F...FH /* N hexes */ = 16^N-1 = 2^{4N}-1 = \sum_{j=0}^{4N-1} 1 * 2^j = 1......1B /* 4N bits */`

If we set `N=4` specifically,  
`FFFFH = 0xffff = 1111 1111 1111 1111B`

```
8-bit = 0000 0000B -- 1111 1111B = 00H -- FFH = 0 -- 2^8-1 = 0 -- 255
16-bit = 0000 0000 0000 0000B -- 1111 1111 1111 1111B = 0000H -- FFFFH = 0 -- 2^16-1 = 0 -- 65,535
32-bit = 0000 0000 0000 0000 0000 0000 0000 0000B -- 1111 1111 1111 1111 1111 1111 1111 1111B 
= 0000 0000H -- FFFF FFFFH = 0 -- 2^32-1 = 0 -- 4,294,967,295
```

Assume that `b_{4j+3}b_{4j+2}b_{4j+1}b_{4j} B = h_j H` for all `j=0 -- N-1`  
Then  
```
b_{4N-1}b_{4N-2}b_{4N-3}b_{4N-4} ... b_3b_2b_1b_0 B
= \sum_{j=0}^{4N-1} b_j * 2^j /* an arbitrary 4N-bit number */
= \sum_{j=0}^{N-1} (b_{4j} * 2^{4j} + b_{4j+1} * 2^{4j+1} + b_{4j+2} * 2^{4j+2} + b_{4j+3} * 2^{4j+3})
= \sum_{j=0}^{N-1} (b_{4j} * 2^0 + b_{4j+1} * 2^1 + b_{4j+2} * 2^2 + b_{4j+3} * 2^3) * 16^j
= \sum_{j=0}^{N-1} (b_{4j+3}b_{4j+2}b_{4j+1}b_{4j} B /* arbitrary 4-bit numbers, 0H--FH */ ) * 16^j
= \sum_{j=0}^{N-1} h_j * 16^j
= h_{N-1} ... h_0 H
```

For example  
```
0x8000 = 1000 0000 0000 0000B
0x4000 = 0100 0000 0000 0000B
0x2000 = 0010 0000 0000 0000B
0x1fff = 0001 1111 1111 1111B
```

One memory location can afford 8-bit numbers `0--255`  
The minimum addressable data unit is `1byte=8bits`  
```
1KB = 2^10 bytes = 1,024 bytes = about a thousand bytes = address 0 -- address 1,023
1MB = 2^20 bytes = 1,048,576 bytes = about a million bytes = address 0 -- address 1,048,575
1GB = 2^30 bytes = 1,073,741,824 bytes = about a billion bytes = address 0 -- address 1,073,741,823
1TB = 2^40 bytes = 1,099,511,627,776 bytes = about a trillion bytes = address 0 -- address 1,099,511,627,775
```

For example  
```Z-80 (8-bitCPU, 2MHz) can afford 64KB memory
2^16 bytes = address 0 -- address 65,535 = address 0000 0000 0000 0000B -- address 1111 1111 1111 1111B
= address 0000H -- address FFFFH  /* the address space is 16-bit */
```
```Pentium4 (32-bitCPU, 3GHz) can afford 4GB memory
2^32 bytes = address 0 -- address 4,294,967,295
= address 0000 0000 0000 0000 0000 0000 0000 0000B -- address 1111 1111 1111 1111 1111 1111 1111 1111B
= address 0000 0000H -- address FFFF FFFFH  /* the address space is 32-bit */
```

I like it  

