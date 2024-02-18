I've always wanted to implement a Delaunary triangulation, but I did it while I was just free.  

#  I. Introduction 

>  Delaunary triangulation, as a main DTM representation method, has a very wide range of uses. So, a triangulation of a point set can take many forms. Why is Delaunary triangulation a favorite? This is mainly due to its following properties: 1. Delaunary triangulation of any point set is unique. 2. Delaunary triangulation strives for the best triangular geometry, and each triangle is as close to an equilateral triangle as possible. 3. Ensure that the nearest points form a triangle, that is, the sum of the sides of the triangle is the smallest. Due to the above properties, Delaunary triangulation is the best in terms of terrain fitting among all possible triangulation networks, so it is often used in the generation of TIN (irregular triangulation). In addition, the Delaunary triangulation is a set of adjacent and non-overlapping triangles, and the circumscribed circle of each triangle contains no other points. This basic law is also called the empty circle rule. 

>  At present, there are three main types of Delaunary triangulation generation algorithms: divide-and-conquer algorithm, point-by-point insertion method and growth algorithm. On this basis, many other triangulation generation algorithms have been derived. Interested students can look up relevant literature for learning. These mainstream triangulation generation algorithms have their advantages and disadvantages. For example, the divide-and-conquer algorithm is a typical "space-for-time" algorithm, which has high time efficiency, but it also occupies more memory space; while the point-by-point insertion rule is the opposite, its time consumption is poor, but it takes up less memory space. In addition, the implementation process of point-by-point insertion method is relatively simple and easy to be implemented by programs. 

#  Point-by-point insertion method 

##  2.1 Algorithm steps 

>  1. Build a flat point set 

          p 

         p 

     The hypertriangle of p (which can also be other hyperpolygons), and use it as a convex closure of the point set. 2. Set the point set 

          p 

         p 

     Insert a point in p into the triangular network, and pay attention to satisfying the above-mentioned empty circle rule of the Delaunary triangular network during the insertion process. If there are triangles in the triangular network 

           T 

           i 

         T_i 

     The circumscribed circle of Ti contains the insertion point and deletes it. 3. Use the insertion point and the triangle 

           T 

           i 

         T_i 

     Construct a new triangulation network based on the non-common edges of Ti, and iterate until the point set 

          p 

         p 

     The algorithm stops when p is empty. 

##  2.2 Code implementation 

The code may be a bit rough, because it was originally designed to understand this algorithm, so please forgive me if there are any errors *~ *. Point2.hpp 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573926861
 ```  
Edge.hpp 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573926861
 ```  
Triangle.hpp 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573926861
 ```  
Delaunay.hpp 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573926861
 ```  
main.cpp 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573926861
 ```  
![avatar]( 2020102515174621.png) 

 Achieve the effect:  

#  III. Summary 

>  Point-by-point insertion method is a classic convex closure shrinkage algorithm. The idea is to first find the smallest convex hull polygon containing the data area, and form a Delaunary triangulation network from the outside to the inside from the polygon. Therefore, every time it inserts a new point, it will delete the corresponding triangle to construct a triangulation network. This process is often accompanied by a large number of query calculations, which also leads to its powerlessness in the face of a large amount of data. But its idea is very simple and ingenious, and it is more suitable for implementation through programs. However, because I have not learned C++ visualization tools yet, there is no visual triangulation. When you have the opportunity to learn, you can make up for it. If there is an error in the above code, I hope you can correct it in time. 

>  Reference: "Principles and Methods of Geographic Information Systems" 

