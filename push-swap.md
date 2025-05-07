Comparisons don't matter, which means that you can create a "clever algorithm" without worrying about the complexity of comparing. 

This, so far, means that insertion sorting seems to be the fastest method.

Optimizations can be done by crunching together some operations. 

When deciding the best route to take when attempting an insertion, I thought of the most optimal way to do it first on a line. In a line you always go to the closest point between the furthest point of each side. After that, picture a circle. Now, think that you always go to the closest point between the furthest point of each side, but in a circle, how do you know where it stops? My best conclusion is that it stops before the biggest gap between 2 consecutive points. Once you reach said point, you take the closest path.

My idea for the algorithm: 

1. Take the longest increasing subsequence of the list.
2. Take the shortest route to push the elements that dont belong to the subsequence to the other list. While you do this, take the opportunity to insert any elements that should go at the top of the stack a.
3. Once you push the last element, take the shortest route to push remaining elements in b.
4. Take the shortest route to rotate the stack a to the correct order. 

Notes:
1. The shortest route to visit all arbitrary points in a circle is to find the biggest gap between 2 consecutive points. Then, you move to the closest one to you, and then you take the shortest route to the next. 
2. It may be even better to take into account the route you will need to take after collecting the elemnts that don't belong to the LIS on stack b. Not sure tho.