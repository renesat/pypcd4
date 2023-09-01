# pypcd4

## Description
pypcd4 is a modern reimagining of the original [pypcd](https://github.com/dimatura/pypcd) library,
offering enhanced capabilities and performance for working with Point Cloud Data (PCD) files.

This library builds upon the foundation laid by the original pypcd while incorporating modern
Python3 syntax and methodologies to provide a more efficient and user-friendly experience.


## Install
You can install pypcd4 via pip,
```shell
pip install pypcd4
```


## How to use
### Import pypcd4
```python
from pypcd4 import PointCloud
```

### Read from .pcd file
```python
pc: PointCloud = PointCloud.from_path("xyzi.pcd")
```

### PointCloud -> NumPy array
```python
array: np.ndarray = pc.numpy()

array.shape
# (1000, 4)
```

### NumPy array -> PointCloud
```python
# Depends on number of features of your array

# If PointXYZI,
pc = PointCloud.from_xyzi_points(array)

# If PointXYZL,
pc = PointCloud.from_xyzl_points(array, label_type=np.uint32)
```

#### Create custom conversion method
```python
# If you cannot find preferred point type in pre-defined conversion methods,
# you can create it easily like,

fields = ("x", "y", "z", "intensity", "new_field")
types = (np.float32, np.float32, np.float32, np.float32, np.float64)

pc = PointCloud.from_points(points, fields, types)
```

### Save as .pcd file
```python
pc.save("nice_point_cloud.pcd")
```


## TODO
- Supprt ROS message conversion
- Visualization
