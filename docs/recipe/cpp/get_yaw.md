# QuaternionからYawに変換する方法

## サンプルコード

```cpp
#include <tf2_geometry_msgs/tf2_geometry_msgs.hpp>
#include <tf2/utils.hpp>

geometry_msgs::msg::Pose pose;
double yaw = tf2::getYaw(pose.orientation);
```
