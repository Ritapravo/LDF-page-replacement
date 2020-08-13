# LDF-page-replacement

The theory about the algorithm is taken from https://www.researchgate.net/publication/319467661_A_Novel_Longest_Distance_First_Page_Replacement_Algorithm

The basic idea behind this algorithm is Locality of Reference11,12 as used in LRU but the difference is that in LDF, locality is based on distance not on the used references. In the LDF, replace the page which is on longest distance from the current page. If two pages are on same distance then the page which is next to current page in anti-clock rotation will get replaced.

Logic behind the LDF is that most of the program or portion of program execute sequentially so if current instruction is nth then probability of executing next
instruction closed to it is more than any other instructions. Similarly probability of executing (n+1),(n+2) ... instructions is more than (n-1),(n-2)....instructions respectively. And by considering locality we can say, chances of executing instructions close to current instruction is more than other instructions. This is the main reason behind the LDF. In page replacement if current page is nth then probability of executing next page closed to it is more than other and (n+1), (n+2).. pages probability is more than (n-1),(n-2).. pages.

## Calculation of Distance

For the calculation of distance of a page from the current page, arrange page reference numbers in circular form and count how many number of pages it is away from the current page in both directions, clock wise and anti-clock wise. From these two distances minimum distance will be taken.

For example; suppose a page reference string is 0 1 2 3
0 1 4 0 1 2 3 4. Total pages in this reference string are five
i.e., 0 1 2 3 4.Now arrange these numbers in circular form
