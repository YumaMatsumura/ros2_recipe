# ParameterDescriptorについて

## 解説

rcl_interfaces::msg::ParameterDescriptorを使用すると、パラメータの詳細設定が可能となる。

nameはパラメータ名、typeは型、descriptionはパラメータの説明、read_onlyは初期化後にパラメータを変更できないようにするかどうか（trueだと変更できない）、dynamic_typingは型の変更を許可するかどうか（trueだと変更できる）、floating_point_rangeはdouble型でパラメータの範囲指定、integer_rangeはint型でパラメータの範囲指定を設定することが可能。

typeについては、rcl_interfaces::msg::ParameterTypeで定義されており、以下にその一覧を示す。

- uint8 PARAMETER_NOT_SET=0
- uint8 PARAMETER_BOOL=1
- uint8 PARAMETER_INTEGER=2
- uint8 PARAMETER_DOUBLE=3
- uint8 PARAMETER_STRING=4
- uint8 PARAMETER_BYTE_ARRAY=5
- uint8 PARAMETER_BOOL_ARRAY=6
- uint8 PARAMETER_INTEGER_ARRAY=7
- uint8 PARAMETER_DOUBLE_ARRAY=8
- uint8 PARAMETER_STRING_ARRAY=9

サンプルコードは以下の通りである。

```cpp
rcl_interfaces::msg::ParameterDescriptor descriptor;
descriptor.name = "low_battery_threshold";
descriptor.type = rcl_interfaces::msg::ParameterType::PARAMETER_DOUBLE;
descriptor.description = "Low battery and capacity threshold to display in GUI";
descriptor.read_only = false;
descriptor.dynamic_typing = false;
rcl_interfaces::msg::FloatingPointRange range;
range.from_value = 0.0;
range.to_value = 100.0;
descriptor.floating_point_range.push_back(range);
this->declare_parameter("low_battery_threshold", 20.0, descriptor);
```

## 参考記事

- [https://qiita.com/NeK/items/74f5d45b01a277f40d1c](https://qiita.com/NeK/items/74f5d45b01a277f40d1c)

## サンプルコード

- [https://github.com/OctoMap/octomap_mapping/blob/6132fdb77bb5070d1c0e932f7168a6c1a3c44d3a/octomap_server/src/octomap_server.cpp#L74-L82](https://github.com/OctoMap/octomap_mapping/blob/6132fdb77bb5070d1c0e932f7168a6c1a3c44d3a/octomap_server/src/octomap_server.cpp#L74-L82)
- [https://github.com/rt-net/raspimouse_ros2_examples/blob/8eedd499d433539c1a1c4f54779685be98f8454d/src/direction_controller_component.cpp#L55-L60](https://github.com/rt-net/raspimouse_ros2_examples/blob/8eedd499d433539c1a1c4f54779685be98f8454d/src/direction_controller_component.cpp#L55-L60)
