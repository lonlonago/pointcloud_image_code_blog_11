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

