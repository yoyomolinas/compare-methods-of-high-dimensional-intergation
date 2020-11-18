# Comparison of Methods of High Dimensional Integration


Calculating the area under a curve has been a long-time problem in mathematics. Curves that can be represented by a formula, such as a parabola, can be integrated using mathematical resources, such as knowledge of integration techniques. Curves that are not represented by formulas but instead by data, can be approximated using numerical methods which heavily rely on computational resources, hence the need to construct efficient algorithms. However in the field of numerical methods, efficiency comes at the expense of accuracy. The problem of approximating high dimensional integrals presents an opportunity to observe this tradeoff between speed and precision in algorithms that approximate high dimension integrals.

  

A thought exercise would be appropriate to give an intuition about what it means to approximate a high Wdimensional integral. A game engineer is building a game which involves randomly generated mountainous regions. To have a sense of the space they occupy, he decides to compute volume. However, since the terrain is random, the volume cannot be calculated by integrating a function; the volume needs to be approximated. In this case, volume is obtained by approximating a three dimensional function, which has the x, y, and z coordinates as variables. With only 3 dimensions, this approximation is not computationally intensive. However, compared to a single dimensional case, this requires much more computation.

  

In very high dimensional space, that consists of more than 10 dimensions, it becomes nearly impossible to approximate integrals using traditional methods. This problem, also known as the curse of dimensionality, presents a need to develop algorithms that can cope with high dimensional settings. In terms of computational effort, Archimedes’ Quadrature, a method inspired by Archimedes’ work on approximating single dimensional integrals, is outperformed by Sparse Grids, a method serving the needs of domains like astrophysics, and finance.

### Archimedes’ Approach
    

Archimedes, the Greek mathematician, physicist and philosopher, lived in an era where derivatives and integrals did not exist, and he needed to calculate areas under non-linear functions. His approach was simple, by drawing triangles in a hierarchical fashion, and summing their areas he was able to approximate integrals. In Figure 1, a one dimensional Archimedes’ approximation is shown. Each triangle, or in other words piecewise linear basis function, is drawn with reference to its hierarchical level. The first level, places a basis function that has its base along the boundaries of the function and head in the middle. The basis drawn in the first level divides the function in two. These two functions are then further approximated with basis functions placed in remaining uncovered space. This presents a recursive strategy to tackle the problem of approximating integrals in arbitrary dimensions with high precision.

  

The question of how to construct basis functions in higher dimensions persists as a topic of research. The approach suggested by many is to take the tensor product of two piecewise linear basis functions [2]. Figure 2 shows the tensor product of two, single dimensional piecewise linear functions creating a 2D basis function. Similarly, a 3D basis function is constructed by taking tensor product of three 2D basis functions.

  

It is crucial to note that the number of basis functions required to approximate an integration grows exponentially with each new dimension. For example, in the single dimensional case, the first two hierarchical levels contain 3 triangles in total. In the two dimensional case, the number of basis functions increase to 9. It is clear that, due to the ‘curse of dimensionality‘, Archimedes’ method has exponential complexity. To be more precise, the algorithm has O(2^nd) complexity where n is the hierarchical levels utilized, where each hierarchical level contains 2^n basis functions, and d the number of dimensions [2]. As one might observe, exponential complexity is not an issue in lower number of dimensions. However, for very high number of dimensions it renders the algorithm highly inefficient.

  
![](https://lh3.googleusercontent.com/p2bv8H10IBMI2GVJg6Zv3szTKzFwzQThSyTYBfUZhHP6iSjQASC-EvOVAN2N9TLorxLYoKx8y-3P4luhkpeUIhQ9gO0Y2DURPha8yufDLnOjyYxcKLlUnchoCOQ1X3TqNArtJG2nBssUQ8cdFA)  
 ***Figure 1**: Archimedes' Quadrature in single dimension [2].*





![](https://docs.google.com/drawings/u/0/d/se36G5wRJMLfzQA2BgehpHw/image?w=321&h=57&rev=1&ac=1&parent=1XoDgtvooup4YO7NCbOo7v8aXokZfgo1M-TH2KoypjnU)

Before moving on to Sparse Grids, it is important to recognize that the weight of importance of each higher level basis function in the process of approximation decays. The higher one goes up Archimedes’ hierarchies, the more the speed of improvement of accuracy will decrease. This observation forms the foundation of the Sparse Grid approach.![](https://lh6.googleusercontent.com/gAGgW3V5rAxEgrmyceSR8Hbb9O3ykbvGw_3JwnQwYWbvnegCkfbYiZJa0k6_PgPX88ZLGAiGt1h_ft2-7VmVvNae6kkLQ3KHNCgirFocl76xpB6WxLhy6myuQ9DFpD7l-L98y2tXLyJMjy0lFQ)
***Figure 2**: Tensor product of two single dimensional basis functions [3].* 

### Sparse Grids
    

Sparse grids, not as ancient as Archimedes’ algorithm, in fact devised in the 20th century, is a method that emerged from the need to efficiently approximate very high dimensional integrals. The method theoretically estimates the cost-precision ratio to decide which basis functions have negligible weight in the resulting approximation. As mentioned in the previous section, hierarchical construction of basis functions provides an opportunity to cut out some them due to their low importance in the approximation. The set of negligible basis functions are chosen in an algorithmic way such that the Sparse Grids method has reasonable complexity and precision.

  

When doing the cost-precision analysis, certain presuppositions have to be made about the properties of the types of basis functions used in the approximation, which means that not all types of basis functions might provide a favorable cost-accuracy ratio. Thus, types of basis functions are chosen after an arduous process assessing their cost-accuracy performance.

  

Sparse Grids use Archimedes’ Quadrature as a base to approximate high dimensional integrals. However, to achieve better efficiency, Sparse Grids neglect certain aspects of the computation, hence their polynomial complexity. In simpler terms, this means that in very high dimensional problem domains, Sparse Grids can decrease the time required for computation from days to hours.

### Comparison
    

Computational complexity is a fundamental metric in computer science to measure efficiency. In high dimensional integral approximation, Archimedes’ approach has exponential complexity while, sparse grids have proven to exhibit polynomial complexity [2]. This fact renders sparse grids suitable to approximate very high dimensional integrals.

  

When working with lower dimensional data, Archimedes’ approach achieves better precision without demanding extravagant resources for computation. In other words, due to less computational complexity, there is no need to cut back on accuracy.

  

Nevertheless, modern era problems are rarely low dimensional. For example certain applications in finance rely on cost efficient methods to integrate high dimensional functions [1]. The method of Sparse Grids is devised to serve the needs of domains that can sacrifice precision for efficiency to a certain degree. Moreover, ongoing research regarding Sparse Grids’ cost vs. accuracy enables scientists to assess the suitability of the method to a problem domain. If precision is vital, then Sparse Grids might not be the best approach in a solution domain.

### Conclusion
    

Like every other problem, there are different approaches to approximating high dimensional integrals. Archimedes’ method is reliable and can serve as a method yielding precise results, with relatively less efficient means. It also forms the foundation of Sparse Grids method, which is specifically designed for approximating very high dimensional integrals. Given the ratio of margin of error over speed of computation, sparse grids achieve much better than Archimedes’ method, which renders them the industry preference.

  

Methods for efficient high dimensional integral approximation are still a topic of research today. Many universities have been invested in the subject for the past decades. Sparse grids have evolved into adaptive sparse grids, and even better methods are under research.

  

In today’s society, as the amount of data collected is growing rapidly, the need to have better, more efficient, and accurate approximation methods becomes more apparent. Therefore, methods yet to be devised will be built on the grounds of being capable of handling massive amounts of data yet to come.

### References

**[1]** Brumm Johannes, Scheidegger Simon. Using Adaptive Sparse Grids To Solve High-Dimensional Dynamic Models. Econometrica. [Online]. 85(5), pp. 1575-1612. Available: [http://johannesbrumm.com/wp-content/uploads/2017/09/Brumm-Scheidegger-2017-ECTA.pdf](http://johannesbrumm.com/wp-content/uploads/2017/09/Brumm-Scheidegger-2017-ECTA.pdf)
    
**[2]** Grace Jochen. “Sparse Grids in a Nutshell,” in Sparse Grids and Applications. Heidelberg, Germany: Springer, 2012, pp. 57-80.
    
**[3]** Bungartz Hans-Joachim, Griebel Michael. Sparse Grids. Acta Numerica. pp. 1-123. Available: http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.92.9392&rep=rep1&type=pdf
