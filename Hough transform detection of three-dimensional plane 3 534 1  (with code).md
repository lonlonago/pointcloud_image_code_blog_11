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

