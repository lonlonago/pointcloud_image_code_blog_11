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

