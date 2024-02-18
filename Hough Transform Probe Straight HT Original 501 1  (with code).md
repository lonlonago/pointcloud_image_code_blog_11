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

