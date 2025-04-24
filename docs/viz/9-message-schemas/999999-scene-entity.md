---
sidebar_position: 99999999
---

#  场景实体

3D 场景中的视觉元素。一个实体可能由多个共享同一参考框架的图元组成。

## 父级架构

`SceneEntity` 出现在 [`SceneUpdate`](插入场景更新文档链接)消息模式中。

## 字段定义

| 字段名         | 类型      | 描述     |
|--------------|-----------|----------|
| `timestamp`    | [`time`](./built-in%20types#time)     | 实体的时间戳 |
| `frame_id`    | [`string`](./built-in%20types#string)     |  参照系 |
| `id`    | [`string`](./built-in%20types#time)     | 实体的标识符。一个实体将用相同的 替换同一主题上的任何先前实体 `id` |
| `lifetime`    | [`duration`](./built-in%20types#duration)     | `timestamp` 实体应自动删除的时间长度（相对于）。零值表示实体应保持可见，直到被替换或删除。 |
| `frame_locked`    | [`boolean`](./built-in%20types#duration)     | 实体是否应保持其在固定框架中的位置（false）或跟随相`frame_id`对于固定框架移动的指定框架（true） |
| `metadata`    | [`KeyValuePair[]`](插入键值对的文档链接)     | 与实体关联的用户提供的其他元数据。键必须是唯一的|
| `arrows`    | [`ArrowPrimitive[]`](./3-arrow-primitive.md)     | 箭头原语 |
| `cubes`    | [`	CubePrimitive[]`	](原始立方体文档链接) | 立方体基元
| `spheres`    | [`	SpherePrimitive[]`](原始文档链接) | 球体基本体
| `cylinders`    | [`	CylinderPrimitive[]`	](原始文档链接)	 | 圆柱体基本体
| `lines`    | [`	LinePrimitive[]`	](原始文档链接) | 线基元
| `triangles`    | [`	TriangleListPrimitive[]	`	](原始文档链接) | 三角形列表基元
| `texts`    | [`	TextPrimitive[]	`	](原始文档链接) | 文本基元
| `models`    | [`	ModelPrimitive[]`		](原始文档链接) | 模型原语

## 参考

coScene 的架构类型（schemas）是与框架无关的，可以使用任何受支持的消息编码格式来实现。

| 编码格式     | Schema 名称                     |
|--------------|----------------------------------|
| ROS 1        |   [`foxglove_msgs/SceneEntity`](https://github.com/foxglove/foxglove-sdk/blob/main/schemas/ros1/SceneEntity.msg) |
| ROS 2        |   [`foxglove_msgs/msg/SceneEntity`](https://github.com/foxglove/foxglove-sdk/blob/main/schemas/ros2/SceneEntity.msg) |
| JSON         |   [`foxglove.SceneEntity`](https://github.com/foxglove/foxglove-sdk/blob/main/schemas/jsonschema/SceneEntity.json) |
| Protobuf     |   [`foxglove.SceneEntity`](https://github.com/foxglove/foxglove-sdk/blob/main/schemas/proto/foxglove/SceneEntity.proto) |
| FlatBuffers  |   [`foxglove.SceneEntity`](https://github.com/foxglove/foxglove-sdk/blob/main/schemas/flatbuffer/SceneEntity.fbs) |
| OMG IDL      |   [`foxglove::SceneEntity`](https://github.com/foxglove/foxglove-sdk/blob/main/schemas/omgidl/foxglove/SceneEntity.idl) |
> **注意**：必须使用上述指定的 schema 名称，coScene 才能正确识别。
