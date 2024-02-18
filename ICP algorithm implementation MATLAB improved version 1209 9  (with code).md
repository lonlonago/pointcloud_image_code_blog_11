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

