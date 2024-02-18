![avatar]( 9e7f2c9903424f61841241388e314292.gif) 

#  I. Introduction 

>  In 1978, Green and Sibson first implemented a growth algorithm for generating Dirichlet polygonal graphs. Subsequent scholars have improved the growth algorithm, such as Brassel and Reif. However, the growth algorithm has been less studied in the literature in the 1980s, and more attention has been paid to the divide-and-conquer algorithm and the point-by-point insertion method. Although this is the case, the idea of this method has many references and is worth learning and understanding. 

#  Second, algorithm implementation 

##  2.1 Algorithm steps 

>  The steps of the growth algorithm are relatively simple, as follows: (1) Construct the initial baseline. Take any point 1 in all the data (usually a point near the geometric center, which can be grown faster), find the point 2 closest to this point, and the two points are connected to form the initial baseline. (2) Construct the first triangle. Apply the Delaunay rule to the right of the initial baseline to find the third point (so that the angle 132 reaches the maximum) to form the first Delaunay triangle. (3) Growth process. Based on the new side of the first triangle (2-3, 3-1), repeat the process of (2) until all data points are processed. 

##  2.2 Code implementation (MATLAB) 

>  main.m 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573969715
 ```  
>  CrossProductV1.m 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573969715
 ```  
>  CircumCircleContains.m 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573969715
 ```  
>  BiggestAngle.m 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573969715
 ```  
>  DrawCircle.m 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573969715
 ```  
#  III. Achieving results 

![avatar]( 8e764f999ac1495da85f0bd5a3abc8f3.png) 

![avatar]( 7fba2f3d58204766aa2d8e27dc979aa7.png) 

![avatar]( 5a883a494cc74f86b3370d0b28961ec7.png) 

![avatar]( 655097bf183746d9983fdb95362b2881.png) 

#  References 

>  [1] Accurate calculation of single tree canopy volume from 3D laser scanning data [2] Research on generation algorithm of Delaunay triangulation net 

