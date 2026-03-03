---
title: Mermaid图表样例
description: 展示 Mermaid 图表的各种类型和示例
created: 2026-03-02 21:25:33
updated: 2026-03-02 21:31:11
id: 3dcc68a1
---

## ⚠️注意

- 部分图表使用中文会出错，渲染失败时使用英文查看是否正常。

- 网页console警告``render.ts:36 Do not assign mappings to elements without corresponding data (i.e. ele `app-cache` has no mapping for property `label` with data field `label`); try a `[label]` selector to limit scope to elements with `label` defined``请忽略，不影响显示。

## 流程图（Flowchart）

flowchart：

```mermaid
flowchart LR
    A[开始] --> B{判断}
    B -->|是| C[结果1]
    B -->|否| D[结果2]
```

graph：

```mermaid
graph LR
    A[开始] --> B{判断}
    B -->|是| C[结果1]
    B -->|否| D[结果2]
```

## 序列图（SequenceDiagram）

```mermaid
sequenceDiagram
    用户->>系统: 登录请求
    系统-->>用户: 登录成功
```

## 类图（ClassDiagram）

```mermaid
classDiagram
    Animal <|-- Duck
    Animal : +int age
    class Duck{
        +swim()
    }
```

## 状态图（StateDiagram）

```mermaid
stateDiagram
    [*] --> 待机
    待机 --> 运行
    运行 --> [*]
```

## 实体关系图（EntityRelationshipDiagram）

```mermaid
erDiagram
    顾客 ||--o{ 订单 : 下单
    订单 ||--|{ 订单项 : 包含
```

## 旅行图（JourneyChart）

```mermaid
journey
    title 我的工作日
    section 早上
      起床: 5: 我
      洗漱: 3: 我
    section 下午
      工作: 1: 我
```

## 甘特图（GanttChart）

```mermaid
gantt
    title 项目计划
    dateFormat  YYYY-MM-DD
    section 设计
    需求分析 :done, 2023-01-01, 3d
    原型设计 :active, 2023-01-04, 2d
```

## 饼图（PieChart）

```mermaid
pie
    title 销售额占比
    "产品A" : 40
    "产品B" : 30
    "产品C" : 30
```

## 象限图（QuadrantChart）

```mermaid
quadrantChart
    title Product Strategy
    x-axis Low Value --> High Value
    y-axis Low Risk --> High Risk
    quadrant-1 Stars
    quadrant-2 Question Marks
    quadrant-3 Dogs
    quadrant-4 Cash Cows
    ProductA: [0.8, 0.3]
    ProductB: [0.2, 0.6]
```

## 需求图（RequirementDiagram）

```mermaid
requirementDiagram
    requirement login_req {
        id: 1
        text: User can log in
        risk: low
        verifymethod: test
    }
    element login_module {
        type: ui
    }
    login_req - satisfies -> login_module
```

## 版本控制图（GitGraph）

```mermaid
gitGraph
    commit
    branch feature
    checkout feature
    commit
    checkout main
    merge feature
```

## C4图表（C4 Model）-暂不支持

暂不支持。

## 思维导图（Mindmap）

```mermaid
mindmap
  根节点
    子节点1
    子节点2
```

## 时间线（Timeline）

```mermaid
timeline
    title 历史事件
    2020 : 历史事件1
    2021 : 历史事件2
    2022 : 历史事件3
    2023 : 历史事件4
    2024 : 历史事件5
    2025 : 历史事件6
    2026 : 历史事件7
```

## 序列图（ZenUML）-暂不支持

暂不支持。

## 桑基图（Sankey）

```mermaid
sankey
    SourceA, Middle, 100
    SourceB, Middle, 50
    Middle, Output, 120
    Middle, Loss, 30
```

## XY 图表（XY Chart）

```mermaid
xychart
    title Monthly Sales
    x-axis [Jan, Feb, Mar, Apr]
    y-axis "Revenue" 0 --> 100
    bar [50, 80, 60, 90]
    line [45, 70, 55, 85]
```

## 块图（Block）

```mermaid
block
    块1
    块2
    块1 --> 块2
```

## 数据包图（Packet）

```mermaid
packet
0-3: "版本"
4-7: "头长度"
8-15: "服务类型"
```

## 看板（Kanban）

```mermaid
kanban
    待办
        [任务1]
        [任务2]
    进行中
        [任务3]
    已完成
        [任务4]
```

## 架构图（Architecture）

```mermaid
architecture-beta
    group backend(cloud)[Backend Services]

    service web(server)[Web Server] in backend
    service app(server)[App Server] in backend
    service db(database)[Database] in backend
    service cache(disk)[Cache] in backend

    web:R -- L:app
    app:B -- T:db
    app:R -- L:cache
```

## 雷达图（Radar）

```mermaid
---
title: "学生成绩雷达图"
---
radar-beta
  axis m["语文"], s["数学"], e["英语"]
  axis h["历史"], g["地理"], a["政治"]
  curve a["小明"]{82, 91, 67, 74, 88, 95}
  curve b["小红"]{59, 76, 84, 93, 70, 68}
  curve c["小刚"]{47, 63, 89, 72, 81, 77}
  curve d["小方"]{95, 58, 82, 69, 73, 86}

  max 100
  min 0
```

## 树状图（Treemap）

```mermaid
treemap-beta
"分类1"
    "项1": 10
    "项2": 20
"分类2"
    "项3": 15
```