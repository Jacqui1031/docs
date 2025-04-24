---
sidebar_position: 7
---

# 压缩图像

## 面板支持
`CompressedImage` 用于 [三维面板](../4-panel/2-3d-panel.md) 和 [图像面板](../4-panel/5-image-panel.md) 中。

## 字段定义

| 字段名         | 类型      | 描述     |
|--------------|-----------|----------|
| `timestamp`    | [`time`](./built-in%20types#time)     | 图像的时间戳                         |
| `frame_id`     | [`string`](./built-in%20types#string)     | 图像的参考坐标系。坐标系的原点是相机的光学中心。+x 指向图像右侧，+y 指向图像下方，+z 指向图像平面内部。                         |
| `data`     | [`byte`](./built-in%20types#bytes)  | 压缩图像数据                          |
| `format`    | [`string`](./built-in%20types#string)  | 图像格式                         |

### `format`
支持的值：Chrome 支持的图片媒体类型，例如`webp`、`jpeg`、`png`

## 参考

coScene 的架构类型（schemas）是与框架无关的，可以使用任何受支持的消息编码格式来实现。

| 编码格式     | Schema 名称                     |
|--------------|----------------------------------|
| ROS 1        |  [`foxglove_msgs/CompressedImage`](https://github.com/foxglove/foxglove-sdk/blob/main/schemas/ros1/CompressedImage.msg) |
| ROS 2        |  [`foxglove_msgs/msg/CompressedImage`](https://github.com/foxglove/foxglove-sdk/blob/main/schemas/ros2/CompressedImage.msg) | 
| JSON         |  [`foxglove.CompressedImage`](https://github.com/foxglove/foxglove-sdk/blob/main/schemas/jsonschema/CompressedImage.json) |
| Protobuf     |  [`foxglove.CompressedImage`](https://github.com/foxglove/foxglove-sdk/blob/main/schemas/proto/foxglove/CompressedImage.proto) |
| FlatBuffers  |  [`foxglove.CompressedImage`](https://github.com/foxglove/foxglove-sdk/blob/main/schemas/flatbuffer/CompressedImage.fbs) |
| OMG IDL      |  [`foxglove::CompressedImage`](	foxglove::CompressedImage) |

> **注意**：必须使用上述指定的 schema 名称，coScene 才能正确识别。
