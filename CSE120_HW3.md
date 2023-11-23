# 1 
1. 8
2. 4
3. pageTable[0].vpn = 0
   
   pageTable[0].ppn = 2

   pageTable[1].vpn = 1

   pageTable[1].ppn = 0

   pageTable[2].vpn = 2

   pageTable[2].ppn = 6

   pageTable[3].vpn = 3

   pageTable[3].ppn = 4
4. 256
5. 768
6. 6
7. 42
8. 810
9. System.arraycopy assumes contiguous physical pages. With paging, the virtual pages may map to non-contiguous physical pages. In this case, it will not work. 
# 2
`a` 100ns + 100ns = 200ns

`b` 100ns*0.75 + 200ns*0.25 = 125ns

`c` 100ns*0.995 + 200ns*0.005 = 100.5ns
# 3
`a` 32 - 10 = 22 bits

`b` page address = 0xFC00, 0xFCC0 >> 10 = 0x3F (virtual value)

`c` offset = 0xFFFF & 0x3FFF = 0x3FF

`d` do 10 left shifts of 0x4 = 0x4 << 10 = 0x1000

`e` physical address = 0x1000 & 0x3FF = 0x13FF
# 4
`a` 2^44 / 2^16 = 2^28 pages

`b` 
1. offset: log2(page size) = log2(2^16) = 16 bits
2. index into 2nd page: log2(entries per page) = log2(2^14) = 14 bits
3. index into root page: 44 - 16 - 14 = 14 bits

`c` program pages + pages needed for each level = 2^16 + 3 pages
# 5
`Average Instruction Time` 2ns + 10ms/20000000 = 2.5ns

`Average Instruction Time after REDO` 1ns + 10ms/20000000 = 1.5ns
# 6
`FIFO` 8 faults
1. [1] 4
2. [2] 42
3. [3] 427
4. [3] 427
5. [4] 4275
6. [5] 2753
7. [5] 2753
8. [5] 2753
9. [6] 7531
10. [7] 5312
11. [8] 3126

`LRU` 7 faults
1. [1] 4
2. [2] 42
3. [3] 427
4. [3] 472
5. [4] 4725
6. [5] 7253
7. [5] 2753
8. [5] 7532
9. [5] 7523
10. [6] 5231
11. [6] 5312
12. [7] 3126



# 7
The working set alog will balance these conditions as it can adjust the amount of memory allocated to different processed based on the working sets. By doing so, it is posssible to maximize the CPU utilization. 
# 8
 1.  Install a faster CPU: not much help, it can improve the CPU performace but not the utlization as CPU is not the control of the utlization
 2.  Install a bigger paging disk: not much help, there is no storage issues
 3.  Increase the degree of multiprogramming: can possibly improve. However, it may also requires more resources then lead to more faults
 4.  Decrease the degree of multiprogramming: can possibly improve. However, if less program are being executed, it may need more time wait other operations being completed
 5.  Install more main memory: highly possible to improve as it can reduce the page faults
 6.  Install a faster hard disk, or multiple controllers with multiple hard disks: can improve overall performace but may not directly impact the CPU utilization
 7.  Add prepaging to the page-fetch algorithms: can improve the CPU utilization as reduce the chances of page faults and keeps CPU busy barely wasting any resources.  
 8.  Increase the page size: can hardly improve the CPU utilization as ut can increase the chances of wasting memory. 

