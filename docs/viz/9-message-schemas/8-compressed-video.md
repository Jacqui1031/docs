---
sidebar_position: 8
---

# 压缩视频

压缩视频码流中的单个帧。

## 面板支持
`CompressedVideo` 用于 [三维面板](../4-panel/2-3d-panel.md) 和 [图像面板](../4-panel/5-image-panel.md) 中。

## 字段定义

| 字段名         | 类型      | 描述     |
|--------------|-----------|----------|
| `timestamp`    | [`time`](./built-in%20types#time)     | 视频帧的时间戳          |
| `frame_id`     | [`string`](./built-in%20types#string)     | 视频的参考框架                         |
| `data`     | [`byte`](./built-in%20types#bytes)  | 压缩视频帧数据       |
| `format`    | [`string`](./built-in%20types#string)  | 视频格式                         |

### `frame_id`
该坐标系的原点是摄像头的光学中心。
- +x 方向指向视频画面的右侧
- +y 方向指向下方
- +z 方向指向视频平面

### `data`
对于基于数据包的视频编解码器，此数据必须在数据包边界上开始和结束（不能是部分数据包），并且必须包含足够的视频数据包来精确解码一张图片（关键帧或增量帧）。

> **注意**：coScene 不支持包含 B 帧的视频流，因为它们需要前视（lookahead）处理。

具体来说，不同格式的要求如下：

 - `h264`
   - 使用 Annex B 格式的数据
   - 每条 CompressedVideo 消息应包含足够的 NAL 单元，单元来解码一个视频帧
   - 每条包含关键帧（IDR）的消息还必须包含一个 SPS NAL 单元

 - `h265`（HEVC）
   - 使用 Annex B 格式的数据
   - 每条 CompressedVideo 消息应包含足够的 NAL 单元，单元来解码一个视频帧
   - 每个包含关键帧（IRAP）的消息还必须包含相关的 VPS / SPS / PPS NAL 单元

 - `vp9`
    - 每条 CompressedVideo 消息应包含恰好一帧视频

 - `av1`
   - 使用“低开销比特流格式”
   - 每条 CompressedVideo 消息应包含足够的 OBU，以解码恰好一帧视频
   - 每个包含关键帧的消息还必须包含一个序列头 OBU（Sequence Header OBU）

### `format`
支持的格式值：h264、h265、vp9、av1

> **注意**：压缩视频的支持受限于硬件能力和专利授权，因此并非所有平台都支持所有编码格式。请查看更多有关 [H.265](https://caniuse.com/hevc)、[VP9](https://caniuse.com/webm) 和 [AV1](https://caniuse.com/av1) 支持的信息。

## 参考

coScene 的架构类型（schemas）是与框架无关的，可以使用任何受支持的消息编码格式来实现。

| 编码格式     | Schema 名称                     |
|--------------|----------------------------------|
| ROS 1        |   [`foxglove_msgs/CompressedVideo`](https://github.com/foxglove/foxglove-sdk/blob/main/schemas/ros1/CompressedVideo.msg) |
| ROS 2        |   [`foxglove_msgs/msg/CompressedVideo`](https://github.com/foxglove/foxglove-sdk/blob/main/schemas/ros2/CompressedVideo.msg) |
| JSON         |   [`foxglove.CompressedVideo`](https://github.com/foxglove/foxglove-sdk/blob/main/schemas/jsonschema/CompressedVideo.json) |
| Protobuf     |   [`foxglove.CompressedVideo`](https://github.com/foxglove/foxglove-sdk/blob/main/schemas/proto/foxglove/CompressedVideo.proto) |
| FlatBuffers  |   [`foxglove.CompressedVideo`](https://github.com/foxglove/foxglove-sdk/blob/main/schemas/flatbuffer/CompressedVideo.fbs) |
| OMG IDL      |   [`foxglove::CompressedVideo`](https://github.com/foxglove/foxglove-sdk/blob/main/schemas/omgidl/foxglove/CompressedVideo.idl) |
> **注意**：必须使用上述指定的 schema 名称，coScene 才能正确识别。
