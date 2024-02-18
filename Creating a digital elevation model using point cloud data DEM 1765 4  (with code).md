#  I. Introduction 

>  With the improvement of computer data processing capabilities, a new digital method for describing the earth's surface has been widely adopted, which is the Digital Elevation Model (DEM), which is organized in a certain structure in the form of numbers. It is a digital model of the physical ground model that represents the spatial distribution of actual terrain features, and is also a digital description of the size and undulation of the terrain shape. The core of DEM is the three-dimensional coordinate data of the terrain surface feature points and a set of algorithms that provide a continuous description of the surface. The most basic DEM is composed of a series of ground points x, y positions and their associated elevations Z, expressed in mathematical functions as: 

          z 

          = 

          f 

          ( 

          x 

          , 

          y 

          ) 

         z=f(x,y) 

     z=f(x,y)， 

          ( 

          x 

          , 

          y 

          ) 

         (x, y) 

     (X, y) The area where the EDEM is located. Although DEM was developed to simulate ground undulations, it can also be used to simulate other features that continuously change on two-dimensional surfaces. For example, it can also represent the properties of the ground landscape, such as ground temperature, precipitation, earth magnetism, gravity, land use, soil type, and other ground characteristic information. At this time, the DEM is also called Digital Terrain Models (DTM). 

#  Second, related functions in MATLAB 

pc2dem: This function will create and return a Digital Elevation Model (DEM) elevModel for the input point cloud. The output matrix contains generalized elevation information for the input point cloud. In addition, this function creates a Digital Elevation Model (DEM) for the point cloud data using a local chunking algorithm. The algorithm assumes that the elevation of the point is along the z-axis. The approximate process is as follows: 

>  1. Divide the point cloud into a grid along the x-axis direction (bird's-eye view). Use the gridResolution parameter to specify the grid size. 2. Using the elevation information of all points in the circular area around the grid corners, calculate the generalized grid value. You can use the'SearchRadius' and'CornerFillMethod 'parameters to specify the search radius and calculation method, respectively. 3. If there are no points in the circular area, the algorithm will not calculate the value, and these grid corners will not be filled. The function represents them as NaN. The algorithm uses the distance-weighted inverse interpolation (IDW) method to fill in the unfilled corners in the grid. To specify the filter size for the IDW interpolation method, use the'FilterSize' name-value parameter. 

#  III. Code implementation 

 ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574037711
 ```  
#  IV. Achieving results 

![avatar]( 0d87e4d760664df19098a4a27bbf4fc3.png) 

#  reference 

>  [1] Matlab help documentation (select the function name and press F1) 

