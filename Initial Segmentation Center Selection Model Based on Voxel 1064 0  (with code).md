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

