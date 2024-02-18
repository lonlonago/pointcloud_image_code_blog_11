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

