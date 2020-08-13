# LDF-page-replacement

The theory about the algorithm is taken from https://www.researchgate.net/publication/319467661_A_Novel_Longest_Distance_First_Page_Replacement_Algorithm

The basic idea behind this algorithm is Locality of Reference11,12 as used in LRU but the difference is that in LDF, locality is based on distance not on the used references. In the LDF, replace the page which is on longest distance from the current page. If two pages are on same distance then the page which is next to current page in anti-clock rotation will get replaced.

Logic behind the LDF is that most of the program or portion of program execute sequentially so if current instruction is nth then probability of executing next instruction closed to it is more than any other instructions. Similarly probability of executing (n+1),(n+2) ... instructions is more than (n-1),(n-2)....instructions respectively. And by considering locality we can say, chances of executing instructions close to current instruction is more than other instructions. This is the main reason behind the LDF. In page replacement if current page is nth then probability of executing next page closed to it is more than other and (n+1), (n+2).. pages probability is more than (n-1),(n-2).. pages.

##  Calculation of Distance

For the calculation of distance of a page from the current page, arrange page reference numbers in circular form and count how many number of pages it is away from the current page in both directions, clock wise and anti-clock wise. From these two distances minimum distance will be taken

For example; suppose a page reference string is 0 1 2 3 0 1 4 0 1 2 3 4. Total pages in this reference string are five i.e., 0 1 2 3 4.Now arrange these numbers in circular form.

![](https://github.com/Ritapravo/LDF-page-replacement/blob/master/img/im1.jpeg)

Now we can calculate distance of any page from any other page, page number 4 and 1 is on distance of one, and 3 and 2 is on distance of two from page number 0. Similarly distance of page number 2 from 0 is 2 clock wise and 3 anti-clock wise so here the smallest distance will be considered as 2

 ## LDF Page Replacement
 
Example1: Let us consider above page reference string i.e. 0 1 2 3 0 1 4 0 1 2 3 4 and number of frames in memory is 3. In the Figure 4 given reference string using LDF total page fault is 8. The first three page reference cause page fault because initially memory frames are free and no page replacement is required. Fourth page reference i.e., page number 3 will also cause page fault as now memory frames are full, so it requires page replacement, using LDF, page 1 will be replaced with page 3 because distance of 0 and 1 from 3 is 2 and distance of page 2 from 3 is 1. Pages 0 and 1 are on same distance from current page 3 so the page which is next to page 3 will be replaced in anti-clock rotation and it is page number 1. Fifth page reference 0 will not cause page fault. Sixth page 1 will cause page fault so page 3 will be replaced because it is on longest distance from 1. Seventh page 4 will also cause page fault so page 2 will be replaced with 4. Page references Eight, Nine and Twelfth will not cause page fault but tenth and eleventh page will cause page faults. 

![](https://github.com/Ritapravo/LDF-page-replacement/blob/master/img/im2.jpeg)

Total page faults for above taken reference string will be 8.


## Here are the code input/outputs

### Input/Output - 1

![](https://github.com/Ritapravo/LDF-page-replacement/blob/master/img/im3.jpeg)

### Input/Output - 2

![](https://github.com/Ritapravo/LDF-page-replacement/blob/master/img/im4.jpeg)
