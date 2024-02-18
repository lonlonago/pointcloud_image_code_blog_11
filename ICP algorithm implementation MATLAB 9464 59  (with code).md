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

