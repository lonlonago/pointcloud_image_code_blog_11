#  I. Introduction 

>  There are many methods for determining whether a point is inside a polygon, such as ray method, scanning method, etc. However, these methods all require rasterization or establishment of equations, so the cross-multiplication method may be more suitable for point clouds. Although doing so will increase the amount of computation and be a bit expensive, this method also has its advantages: it is simple and does not destroy the original data. 

>  The specific idea is very simple, as shown in the figure below, if a point is inside a polygon, then the cross product of the green boundary vector and the blue vector pointing to the inner point should be a positive number (that is, on the left side of the boundary vector). If each boundary of the polygon is judged in this way in a counterclockwise order, then all calculated values should be positive, otherwise the point is not inside the polygon. 

![avatar]( fe06864b50244b98afcece9a7c44b326.png) 

#  Code implementation 

Here we take the previous convex hull algorithm as an example. If you don't know much about the convex hull algorithm, you can take a look at this article: https://blog.csdn.net/dayuhaitang1/article/details/122821546, there will be no more details here. 

>  IsInConvexHull.m 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 202402030957401376
 ```  
>  Graham.m 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 202402030957401376
 ```  
#  III. Achieving results 

>  Original data source 

![avatar]( 51a64fc1693f4d4da2a7d829e663f64c.png) 

>  judgment result 

![avatar]( 42d7af301c8d44b5ad8dcfb30cf534f2.png) 

![avatar]( 31780b3b456c439ba8b2cf856c538451.png) 

