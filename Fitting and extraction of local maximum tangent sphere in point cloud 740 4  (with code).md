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

