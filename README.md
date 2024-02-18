#  I. Introduction 

>  Inspired by the reference [1], I tried to obtain a concave package by removing the larger area of the triangular surface on the basis of the three-dimensional convex hull (here we achieved it by specifying an area threshold). Although the final result is not very ideal haha, but here I still record it. 

#  Implementation code 

>  Delaunay3D.m 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 202402030957406514
 ```  
> 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 202402030957406514
 ```  
#  III. Achieving results 

>  Original convex hull appearance 

![avatar]( 680d8faebb9f4425b1bfc778ff0f8536.png) 

>  culling effect 

>  The area threshold is 0.3. 

![avatar]( 1070120a38a54c89a0535d44b4118d3f.png) 

>  The area threshold is 0.1. 

![avatar]( 972a2773a4214b59abc928f012679313.png) 

#  References 

>  [1] Accurate calculation of single tree canopy volume based on 3D laser scanning data 



--------------------------------------------------------------------------------

#  I. Introduction 

>  With the improvement of computer data processing capabilities, a new digital method for describing the earth's surface has been widely adopted, which is the Digital Elevation Model (DEM), which is organized in a certain structure in the form of numbers. It is a digital model of the physical ground model that represents the spatial distribution of actual terrain features, and is also a digital description of the size and undulation of the terrain shape. The core of DEM is the three-dimensional coordinate data of the terrain surface feature points and a set of algorithms that provide a continuous description of the surface. The most basic DEM is composed of a series of ground points x, y positions and their associated elevations Z, expressed in mathematical functions as: 

          z 

          = 

          f 

          ( 

          x 

          , 

          y 

          ) 

         z=f(x,y) 

     z=f(x,y)， 

          ( 

          x 

          , 

          y 

          ) 

         (x, y) 

     (X, y) The area where the EDEM is located. Although DEM was developed to simulate ground undulations, it can also be used to simulate other features that continuously change on two-dimensional surfaces. For example, it can also represent the properties of the ground landscape, such as ground temperature, precipitation, earth magnetism, gravity, land use, soil type, and other ground characteristic information. At this time, the DEM is also called Digital Terrain Models (DTM). 

#  Second, related functions in MATLAB 

pc2dem: This function will create and return a Digital Elevation Model (DEM) elevModel for the input point cloud. The output matrix contains generalized elevation information for the input point cloud. In addition, this function creates a Digital Elevation Model (DEM) for the point cloud data using a local chunking algorithm. The algorithm assumes that the elevation of the point is along the z-axis. The approximate process is as follows: 

>  1. Divide the point cloud into a grid along the x-axis direction (bird's-eye view). Use the gridResolution parameter to specify the grid size. 2. Using the elevation information of all points in the circular area around the grid corners, calculate the generalized grid value. You can use the'SearchRadius' and'CornerFillMethod 'parameters to specify the search radius and calculation method, respectively. 3. If there are no points in the circular area, the algorithm will not calculate the value, and these grid corners will not be filled. The function represents them as NaN. The algorithm uses the distance-weighted inverse interpolation (IDW) method to fill in the unfilled corners in the grid. To specify the filter size for the IDW interpolation method, use the'FilterSize' name-value parameter. 

#  III. Code implementation 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574037711
 ```  
#  IV. Achieving results 

![avatar]( 0d87e4d760664df19098a4a27bbf4fc3.png) 

#  reference 

>  [1] Matlab help documentation (select the function name and press F1) 



--------------------------------------------------------------------------------

#  I. Introduction 

>  If you manually configure the header files and library files required by Open3D in the vs project, it will be a headache, so we should learn to manage and configure these by using the cmake tool. 

#  Implementation code 

>  CmakeLists.txt 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574080592
 ```  
>  main.cpp 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574080592
 ```  
![avatar]( 3ad0fbd73ab2478d93dc56b0b7e215ee.png) 

#  III. Achieving results 

![avatar]( 62b97e012fb84d89bd06c4d850d45536.png) 

 ![avatar]( a526465d5f7d4554b23f601604b14a01.png) 



--------------------------------------------------------------------------------

#  Delaunay triangulation alpha shape 2D point set edge line extraction 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573928829
 ```  


--------------------------------------------------------------------------------

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



--------------------------------------------------------------------------------

#  I. Introduction 

>  There are many ways to obtain depth images, such as lidar, structured light, and depth cameras. Many tutorials on the Internet explain the conversion of depth images acquired by depth cameras into 3D point cloud data (camera internal and external parameters), but the depth cameras generated by lidar are usually different from those generated by cameras. For details, please refer to the following figure: 

![avatar]( f7df58f37a574f21a66c8b0e0bc090fa.png) 

>  As shown in the figure above, in the depth image generated by the laser point cloud data, the brightness value of each pixel represents the distance value from the object to the scanner. The pitch angle of each row is the same, and the yaw angle of each column is the same. Therefore, such a depth image represents each point in the point cloud through the depth value, pitch angle and yaw angle. This is mainly because the process of generating depth images through laser point cloud data is actually a sampling process, as shown in the figure below. 

          O 

         O 

     O represents the position of the laser scanner, which is sampled by equal pitch horizontal and vertical rotation viewing angles. If there is a point in this viewing angle, record its distance value as the luminance value of the pixel, and record the pitch angle and yaw angle at this time at the same time. Otherwise, it is recorded as 0. Then the depth image can be converted into the original point cloud data in reverse through these three, of course, there are still errors in the process. 

![avatar]( 9b7c37c0ff354de1b38c0caabea9b180.png) 

>  According to the above figure, let 

          O 

          P 

         OP 

     The distance of the OP is 

          D 

         D 

     D, the specific point cloud coordinate formula is: 

#  Code implementation 

We take the open source dataset (https://rosbag.tier4.jp/) as an example, obtain a depth image in the dataset, and we restore it. 

>  AngleToRad.m 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 202402030957405455
 ```  
>  RangeImageToPointCloud.m 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 202402030957405455
 ```  
#  III. Achieving results 

>  Original data source 

![avatar]( f6147410a182425094d6dab3d2eb57b4.png) 

>  Transformed point cloud data 

![avatar]( ffe789c95aac41f58e2da32279b958f8.png) 

![avatar]( 165d14a51781405ebfa40acbc153ae81.png) 

#  References 

>  [1] Real-Time Streaming Point Cloud Compression for 3D LiDAR Sensor Using U-Net [2] Acquisition and Processing of Depth Image 



--------------------------------------------------------------------------------

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



--------------------------------------------------------------------------------

## 

Easy3D

#  First, the basic configuration 

#  Data IO 

#  Third, data lake visualization 

#  IV. Surface reconstruction 

#  Point cloud segmentation 

#  Point cloud characteristics 

#  other 

## 

CGAL

#  First, the basic configuration 

#  II. File IO 

#  Point cloud sampling 

#  Point cloud registration 

#  Point cloud clustering 

#  Surface geometry 

#  Seven, point cloud smoothing 

#  Eight, point cloud characteristics 

#  Point cloud segmentation 

#  Visualization 

#  other 



--------------------------------------------------------------------------------

#  I. Introduction 

>  The main ideas are: (1) Construct a triangular network of canopy point cloud slices, on this basis, we will remove the gaps existing in the point cloud slices. (2) Eliminate the external gaps according to the threshold. To remove the external gaps in the canopy point cloud data boundary, the outermost triangle filter threshold needs to be set. When the side length of the outer triangle exceeds the threshold, the triangle is considered to be an external gap and then rejected. When any side of the outer triangle is less than the threshold, the search can be stopped. 

#  Code implementation 

>  main.m 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574076372
 ```  
>  EdgeSort.m 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574076372
 ```  
#  III. Achieving results 

![avatar]( eb1de16b6d2342c692a9f06ccbd2bc4c.png) 

>  Since I have sorted this edge set, I can use Green's discretization formula (students who are not clear can read this article in detail: https://blog.csdn.net/dayuhaitang1/article/details/122815437) to calculate the area of the concave bag, so this method can also be used in the table method to obtain the canopy volume. 

#  IV. Summary 

>  The above method has not been able to achieve the effect of the paper, such as if the threshold is set too small, the following situation may occur, and then improve it when there is time later "~". 

![avatar]( 890a42c719244034a9358c447d65a240.png) 

>  Reference: [1] Accurate Calculation of Single Tree Canopy Volume from 3D Laser Scanning Data 



--------------------------------------------------------------------------------

#  I. Introduction 

>  If there is a sphere S inside a point cloud that is not completely surrounded by any other spheres that belong within the point cloud, then that sphere is the maximum tangent sphere (defined) of the point cloud. One application of tangent spheres is to build the skeleton of an object, which has been used in the literature. 

>  The specific extraction process is as follows: Starting from a point inside the model, by calculating the vector between it and the nearest point on the model surface, and extending backwards to the inside of the model to adjust the position of the inner point, the initial point is moved from a low distance to a high distance. After adjusting the inner point iteratively for many times, the locally largest internal cut ball and its spherical center in the three-dimensional model can be found. For specific steps, please refer to the reference "^" for details. 

#  Second, algorithm implementation 

>  MaximumInCutBall.m 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574046417
 ```  
>  Extend.m 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574046417
 ```  
>  PointsAverageSpacing.m 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574046417
 ```  
>  DrawBall.m 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574046417
 ```  
#  III. Achieving results 

![avatar]( e96adf85c46448f29cce870434eb0337.png) 

![avatar]( ef1555dd8acb4f00b4d14817c4d9cee9.png) 

#  IV. Summary 

>  The above program also has the following problems: (1) Specify the local inner point. Here I used the center of mass as the starting point, but if the center of mass of the object is not inside the object, the method will not be applicable, so the method at this stage is more suitable for interactive point selection. (2) The nearest point does not select the surface point. Since the point cloud is not reconstructed by the curved surface, the nearest point is still the point in the original point set. The surface point of the model should be selected. If the point cloud is denser, the impact will be small, but if it is sparse, the inner tangent ball calculated by this method will have a large error. Let's improve the method in the future "~" > > > 

>  References: [1] Extraction of grid model skeleton based on maximum tangent sphere fitting _ Miao Yongwei 



--------------------------------------------------------------------------------

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



--------------------------------------------------------------------------------

#  I. Introduction 

>  Basic theory: If the position and normal vector of a point in object space can be accurately determined, then a plane passing through the point can be completely defined, so it can also be used to accelerate the Hough transform and improve reliability. This is because the parameters of the plane can be directly mapped to a single point in the parameter space, which can greatly reduce the number of votes for each point, saving the calculation time and space of the Hough transform. The specific operation process is as follows: 

>  (1) First calculate the normal vector of each point in the out-point cloud. (2) Convert the normal direction of each point to the form expressed in angle and distance parameters to facilitate the execution of the voting process, the formula is as follows: 

![avatar]( fd70320fc09e454d878107a004d81c78.png) 

>  (3) Determine the division interval of the accumulator and use the ( θ， φ， ρ) obtained by each point transformation to vote. (4) Find the plane we want in the point cloud. 

#  Implementation code 

>  HTV _ N.m 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574068800
 ```  
#  III. Achieving results 

![avatar]( 73d03b3e92464de58d5fa9f2def10893.png) 

 ![avatar]( 473972cf11e34d19bbf86c781c30faf6.png) 

>  At this time, the number of point cloud points is 40,000, and the time is about 5 seconds, which improves the computational efficiency. However, when extracting the plane in the horizontal direction, there are still some problems in this method, which still need to be solved later "_". 

#  References 

>  [1] Application of 3D Hough Transform in Laser Point Cloud Feature Extraction [2] RECOGNISING STRUCTURE IN LASER SCANNER POINT CLOUDS 



--------------------------------------------------------------------------------

#  I. Introduction 

>  In the previous article (one of the three-dimensional planes detected by the Hough transform), we roughly understood how the Hough transform detects the plane contained in some points. In simple terms, it is "try". This is a bit like an exhaustive method, a bit violent, but it can indeed solve some problems. So here we will really use it in a point cloud to see how it works. 

#  Second, the testing process 

>  The original version 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574075968
 ```  
>  Test Effect 1: 

![avatar]( 64253eb08624435e98f5f9f06457c283.png) 

![avatar]( 1f169c298341435f94a0d74075431fe8.png) 

Overall, the calculation takes a long time and requires a lot of memory. About 3,000 computers have some cards. 

>  So in order to detect the plane more accurately and quickly, here is an attempt to detect the plane by randomly selecting points: 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574075968
 ```  
>  Test Effect 2: 

![avatar]( 878c0620b7e74f20b841e6efd06d4748.png) 

![avatar]( ddab38e204fb47579032cc43caebd793.png) 

>  This time the effect is much better than the previous one, so let's rotate the data to see the effect. 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574075968
 ```  
![avatar]( 7cdc557291c2447caf741c198e030607.png) 

![avatar]( 2ebbcc7c6fe14ce18d5dc44a44c4baf8.png) 

#  III. Summary 

>  The standard Hough transform method has high spatial and time complexity, so it cannot withstand a large amount of data in the actual calculation process. The reason for this is that it is closely related to the parameter discretization of the method and the design of the accumulator. In addition, the accumulator is prone to multiple peaks, and the selection of appropriate parameters still needs subsequent research "_". 

#  References 

>  [1]The 3D Hough Transform for Plane Detection in Point Clouds: A Review and a new Accumulator Design [2]Iterative Hough Transform for Line Detection in 3D Point Clouds 



--------------------------------------------------------------------------------

#  Overview of the principle 

>  The "Hough Transform" (HT) algorithm, originally published as a US patent, is a general method for locating any shape. It was first applied in the field of two-dimensional images, but it is still suitable for detecting various shapes in two-dimensional and three-dimensional point sets. 

>  Basic theory: In two-dimensional space, every point in the Cartesian coordinate system has an explicit two-dimensional coordinate 

          ( 

          x 

          , 

          y 

          ) 

         ( x, y) 

     (X, y), taking the two-dimensional straight line feature as an example, as shown in the following formula. in the formula, 

          i 

         i 

     Theta takes any angle, every point in two-dimensional space 

          ( 

          x 

          , 

          y 

          ) 

         ( x, y) 

     (X, y) can find the corresponding Hough transform coordinates in two-dimensional Hough space 

          ( 

          i 

          , 

          r 

          ) 

         (i, r) 

     (Theta, r). where  

          i 

         i 

     theta and  

          r 

         r 

     The geometric meaning of r is: from the origin  

          O 

         O 

     O-direction passing point  

          P 

         P 

     The straight line of P, as the vertical line, the vertical line and  

          x 

         x 

     The angle between the x-axis is  

          i 

          ， 

          r 

         i, r 

     Theta, r is the origin  

          O 

         O 

     O over point 

          P 

         P 

     P The vertical distance of the straight line, as shown in the figure. 

![avatar]( 1bf129a676814fd8a97355735da5fda6.png) 

>  In this way, a straight line in the Cartesian coordinate system can be converted into a Hough space. 

          i 

          , 

          r 

         \theta,r 

     If there are countless lines passing through a point in the theta, r parameter space (as shown below), then mapping to a Hough space will naturally result in a sine curve. 

![avatar]( ef8213348db2407a8e3f7b0da461b7de.png) 

>  Here we take three points as an example and map the line passing through them into Hough space as follows: 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574028659
 ```  
![avatar]( b7e605f4655f4a789096901b49a77c5b.png) 

>  It is obvious that these three curves will have an intersection point, so this intersection point is the line parameter we want to probe. In the Hough transform, it uses an accumulator idea to vote for each parameter (essentially counting the number of intersections under each parameter), and finally we can get the line parameter we want based on the voting result. 

>  According to the above basic description, we will now look at the specific detection process, which will be much better. 

>  (1) Build the accumulator. The process is actually relatively simple, which is to divide the angle interval and the distance interval into several parts, such as 

          m 

          and 

          n 

         mmailn 

     M and n, where our angle interval is [0, 

          i 

         \pi 

     Pi], the distance interval will be determined according to the angle, here we first record as 

          [ 

          r 

          m 

          i 

          n 

          , 

          r 

          m 

          a 

          x 

          ] 

         [rmin,rmax] 

     [rmin,rmax]，那么就可以构建我们的累加器矩阵并获得角度增量和距离增量。 

>  (2) Map the line passing through each point to the Hough space. (3) Use the accumulator to vote. Essentially, it records the position where each line is mapped to the Hough space. If the position is a mapping of a line, the accumulator at that position is incremented by 1. If there are multiple lines all mapped to this position, the accumulator at that position is the number of lines. (4) Analyze the accumulator to get the line parameters we want. 

#  Implementation code 

>  HT.m 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574028659
 ```  
#  III. Achieving results 

![avatar]( 91ef76da2f324d90a6660683ed1d68a4.png) 

>  There are still many problems in the above code, here is just a simple demonstration to facilitate subsequent understanding of the Hough transform algorithm * _ *. 

#  reference 

>  [1] Principles of Digital Image Processing [2] Application of 3D Hough Transform in Laser Point Cloud Feature Extraction 



--------------------------------------------------------------------------------

#  Overview of the principle 

>  For the feature recognition of 3D laser point clouds, it is relatively easy to extend to 3D Hough transform by adding a parameter φ on the basis of 2D Hough transform. The formula is as follows: 

>  In the equation, the parameter theta represents the angle between the projection of the normal direction n of the plane in the xoy plane and the forward direction of the x-axis; phi represents the angle between the n and xoy planes; r represents the distance of the origin O from the plane, as shown in the figure below. 

![avatar]( cd09421a437a4f959bb2616e20ea9016.png) 

>  After understanding some of this, the specific process of 3D Hough Transform Probing Plane is (analogous to the process of Hough Transform Probing Straight Lines (the original version of HT)): (1) Build the accumulator. That is, the angle 

          i 

          , 

          e 

         \theta,φ 

     Theta, phi and distance 

          r 

         r 

     How many parts of r are divided. (2) Map the plane passing through each point to the Hough space. (3) Use the accumulator to vote. (4) Analyze the accumulator to get the plane parameters we want. 

#  Implementation code 

>  HTPlane.m 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574078174
 ```  
#  III. Achieving results 

![avatar]( 8bdd245cc0e6401ebbb255c23fbdd0b1.png) 

![avatar]( 16e4635b08de4c76a45e6f92acf6b4c9.png) 

#  References 

>  [1] Application of 3D Hough Transform in Laser Point Cloud Feature Extraction 



--------------------------------------------------------------------------------

These days, because I was learning about point cloud data, I learned about the ICP algorithm.  

#  First, the algorithm steps 

>  (1) Take the point set pi 😉 P in the target point cloud P; (2) Find the corresponding point set qi 😉 Q in the source point cloud Q, such that | | qi-pi | | = min; (3) Calculate the rotation matrix R and the translation matrix t, so that the error function is minimized; (4) Rotate and translate pi using the rotation matrix R and translation matrix t obtained in the previous step to the new corresponding point set pi '= {pi' = Rpi + t, pi 😉 P}; (5) Calculate the average distance between pi 'and the corresponding point set qi; (6) If d is less than a given threshold or greater than a preset maximum number of iterations, the iteration calculation is stopped. Otherwise, return to step 2 until the convergence condition is satisfied. 

#  Second, the implementation code and effects 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574090195
 ```  
ShowData.m 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574090195
 ```  
![avatar]( 20200306135315452.png) 

 Achieve the effect:  

#  III. Summary 

>  Because I took the closest point in the European style as the corresponding point, and used the enumeration method to traverse and filter the corresponding points, which caused the process of matching the corresponding points to take a long time (3105.396793 seconds). If you want to improve the efficiency, you can use the k-d tree structure to achieve it, but at this stage I will not haha, and I will learn to make up for it later. 

Note: Improved https://blog.csdn.net/dayuhaitang1/article/details/123477076 

参考文章： 【1】https://zhuanlan.zhihu.com/p/35893884 【2】https://blog.csdn.net/sinat_29886521/article/details/77506426?utm_source=blogxgwz0 【3】https://blog.csdn.net/kksc1099054857/article/details/80280964 【4】https://blog.csdn.net/u013517182/article/details/53995993?depth_1-utm_source=distribute.pc_relevant.none-task&utm_source=distribute.pc_relevant.none-task 



--------------------------------------------------------------------------------

#  I. Introduction 

>  The specific algorithm process can refer to this article: https://blog.csdn.net/dayuhaitang1/article/details/104694535. I won't go into details here. This time, I mainly use kdtree to improve the previous code to get the closest point faster. The computational efficiency has indeed been greatly improved, so record it here. 

#  Code implementation 

>  ICPV2.m 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574031019
 ```  
>  ShowData.m 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574031019
 ```  
#  III. Achieving results 

>  Two target point clouds of about 150,000 points are registered, and the threshold of d is set to 0.0005: 

![avatar]( 689f8dfbd79d498786e49ad4b9bd916a.png) 

![avatar]( 4d43bbc20a144cb6b9e2bdda8be73368.png) 

>  The two points are about 1 million the target point cloud for registration, and the threshold of d is set to 0.002: 

![avatar]( 7746b35c5af8446483597b0f91f7acbc.png) 

![avatar]( bb37b4fe5245430ca5efd56fa7bce435.png) 

#  IV. Summary 

>  1. It is very dangerous to use the threshold of d as the stop condition of the program. If there is too much noise in the two point clouds, the threshold of d is too small to cause an infinite loop. This is because due to the presence of noise, d will reach saturation after falling to a certain value, so that it cannot be reduced, resulting in an infinite loop of the program. The solution is to set the number of iterations to limit. 2. The ICP algorithm should be combined with the key points of the target, because if all points participate in the calculation, the solved result is the global optimum, but if there is too much noise in the target, it will not achieve what we want 

>  If there are students who need the data of the algorithm test, I have also uploaded it to the csdn, which can be downloaded directly: ICP algorithm registration test data 



--------------------------------------------------------------------------------

#  I. Introduction 

>  In the K-means clustering algorithm, the selection of the initial center has a direct impact on the segmentation effect. Good initial center selection is an important prerequisite for obtaining the expected segmentation effect. Therefore, relevant papers have explored the initial clustering center. 

>  The specific process of the initial segmentation center selection model based on voxel is as follows: (1) Calculate the range of the point cloud, that is, obtain the cube bounding box of the point cloud. (2) Calculate the size of the voxel according to the number of voxels we set. (3) Count the point density of each voxel to obtain the top k individual elements with the highest density. (4) Calculate the top k individual element center with the highest density as the initial segmentation center of the cluster, that is, the extraction is completed. 

#  Implementation code 

>  VoxelInit.m 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 202402030957405843
 ```  
#  III. Achieving results 

![avatar]( e949c255e6a94db9924d8281e1c04cba.png) 

#  References 

>  [1] Research on key technologies of 3D discrete point cloud data processing 



--------------------------------------------------------------------------------

#  I. Introduction 

>  Mainly record the various point cloud libraries and the use of kdtree in some open-source software. 

#  Second, the use of kdtree 

##  2.1 PCL 

>  There are two main types of kdtree in PCL: pcl :: search :: Kd Tree < PointT, Tree > and pcl :: Kd Tree FLANN < PointT, Dist >, both of which make use of Marius Muja and David Lowe's FLANN project (the third-party library FLANN), although the former implements some more query functions. 

>  Get k neighboring points: 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574096345
 ```  
![avatar]( fb8cae13d2be4cf4a01ee93baf47d6c1.png) 

>  Acquire neighboring points within a certain distance: 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574096345
 ```  
![avatar]( 9c7e780dfe3043f4bccc1053e88e6173.png) 

>  Get k neighboring points: 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574096345
 ```  
![avatar]( b9deb9ba5089435a8d541a1feda416cc.png) 

>  Acquire neighboring points within a certain distance: 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574096345
 ```  
![avatar]( 775db63dbb164accae7f7689f1f43293.png) 

##  2.2 Open3D 

>  Open3D also uses FLANN, a third-party project, to build kdtree, which can quickly retrieve the nearest neighbor point set. 

open3d::geometry::KDTreeFlann 

>  Get k neighboring points: 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574096345
 ```  
![avatar]( 12a3dca40da2497d9267759111801aa6.png) 

>  Acquire neighboring points within a certain distance: 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574096345
 ```  
![avatar]( 775db63dbb164accae7f7689f1f43293.png) 

## 

>  Meshlab uses the kdtree structure from the third-party library vcg. 

vcg :: KdTree < typename _ scalar > 

>  Get k neighboring points: 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574096345
 ```  
![avatar]( fda7fd32b6ba4470832de753fdd5100f.png) 

>  Acquire neighboring points within a certain distance: 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574096345
 ```  
![avatar]( 2508d5ad5a8d477f8d5fa7be63e98c12.png) 

##  2.4 MATLAB 

>  Get k neighboring points: 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574096345
 ```  
![avatar]( 53c6cf59a40841f18f7c22397584a9e5.png) 

>  Acquire neighboring points within a certain distance: 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574096345
 ```  
![avatar]( d0d411314722471eba2e5fa98586c639.png) 

#  reference 

>  [1]https://pointclouds.org/documentation/classpcl_1_1_kd_tree_f_l_a_n_n.html#details [2]https://pointclouds.org/documentation/classpcl_1_1search_1_1_kd_tree.html [3]http://www.open3d.org/docs/release/tutorial/geometry/kdtree.html 



--------------------------------------------------------------------------------

#  I. Introduction 

>  The convex hull algorithm in Matlab is different from the classical Graham algorithm. It uses Delaunay triangulation to obtain the convex hull, which is also recorded here. 

#  Implementation code 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574055141
 ```  
#  III. Achieving results 

![avatar]( b2af7e4e62774e7295b9baf9504bde3a.png) 

#  reference 

>  [1] Matlab Help Documentation 



--------------------------------------------------------------------------------

