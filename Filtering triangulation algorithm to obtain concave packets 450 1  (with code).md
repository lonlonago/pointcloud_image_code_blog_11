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

