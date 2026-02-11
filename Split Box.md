---
category: Scripts
uuid: PrhaZPR8MyrmYyJU
title: Split Box
aliases:
  - Split Box
priority: 10
status: 已完成
autosync-database: Obsidian
view-count: 0
date_created: 2026-02-08 01:52:41
date_modified: 2026-02-08 01:52:41
tags: []
---
/*

自定义脚本：对矩形框进行水平或者垂直方向的拆分，或同时进行水平和垂直拆分形成矩阵。
自定义脚本的定义和使用：
1. 在 Excalidraw/Scripts 脚本目录下新建一个md文件，名称任意。
2. 内容的格式是  ````javascript` 必须在注释块内
3. 脚本代码直接AI生成
4. 使用：选中要拆分的矩形框元素，点击如下图所示的按钮，或者可以为其配置快捷键，或者通过 ctrl p 命令行执行。
![](https://image.systemcaller.online:/images/2026/02/ca7f9dbec14a5b3c17b4c89a9e27d33f-20260208011939115.png)

```javascript
*/

// 1. 检查选中元素
const elements = ea.getViewSelectedElements();
if (elements.length !== 1 || elements[0].type !== "rectangle") {
    new Notice("请选中一个矩形 (Please select one rectangle)");
    return;
}
const box = elements[0];

// 2. 获取用户输入
// 选择拆分模式：单向拆分 或 矩阵拆分
const mode = await utils.suggester(
    ["单向拆分（水平或垂直）", "矩阵拆分（同时水平和垂直）"],
    ["single", "matrix"],
    "请选择拆分模式"
);

if (!mode) return;

// 3. 根据模式获取参数
let rows, cols;

if (mode === "matrix") {
    // 矩阵拆分：需要行数和列数
    const rowOptions = [2, 3, 4, 5, 6, 8, 10];
    const rowLabels = rowOptions.map(function(n) { return n + " 行"; });
    rows = await utils.suggester(rowLabels, rowOptions, "选择行数（水平切几份）");

    const colOptions = [2, 3, 4, 5, 6, 8, 10];
    const colLabels = colOptions.map(function(n) { return n + " 列"; });
    cols = await utils.suggester(colLabels, colOptions, "选择列数（垂直切几份）");

    if (!rows || rows < 2 || !cols || cols < 2) return;
} else {
    // 单向拆分：只需要一个份数
    const countOptions = [2, 3, 4, 5, 6, 8, 10, 12];
    const countLabels = ["2 份", "3 份", "4 份", "5 份", "6 份", "8 份", "10 份", "12 份"];
    const count = await utils.suggester(
        countLabels,
        countOptions,
        "拆分成几份?"
    );

    if (!count || count < 2) return;

    // 选择拆分方向
    const direction = await utils.suggester(
        ["水平拆分 (上下切)", "垂直拆分 (左右切)"],
        ["h", "v"],
        "请选择拆分方向"
    );

    if (!direction) return;

    // 单向拆分时，根据方向设置行数和列数
    if (direction === "v") {
        // 垂直拆分（左右）：1行，count列
        rows = 1;
        cols = count;
    } else {
        // 水平拆分（上下）：count行，1列
        rows = count;
        cols = 1;
    }
}

// 4. 复制原矩形样式到 EA 全局样式
ea.style.strokeColor = box.strokeColor;
ea.style.backgroundColor = box.backgroundColor;
ea.style.strokeStyle = box.strokeStyle;
ea.style.strokeWidth = box.strokeWidth;
ea.style.roughness = box.roughness;
ea.style.roundness = box.roundness;
ea.style.opacity = box.opacity;
ea.style.fillStyle = box.fillStyle;

// 保存 groupIds 和 frameId 用于新元素
const groupIds = box.groupIds || [];
const frameId = box.frameId || null;

// 5. 计算坐标并生成新矩形
const width = box.width;
const height = box.height;
const x = box.x;
const y = box.y;
const newWidth = width / cols;
const newHeight = height / rows;

// 双重循环创建矩阵
for (let row = 0; row < rows; row++) {
    for (let col = 0; col < cols; col++) {
        const rectId = ea.addRect(
            x + col * newWidth,
            y + row * newHeight,
            newWidth,
            newHeight
        );
        const rect = ea.getElement(rectId);
        rect.groupIds = groupIds;
        rect.frameId = frameId;
    }
}

// 6. 提交更改：添加到视图并删除旧矩形
await ea.addElementsToView(false, false, true);
ea.deleteViewElements([box]);
