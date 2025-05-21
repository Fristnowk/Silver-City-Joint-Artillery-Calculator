# 联力炮计算器

这是一个基于 `uni-app` 开发的简单计算器，专为帮助玩家计算《游戏王》中的联力炮（联合炮）相关规则而设计。用户可以通过输入双方手牌及场上卡牌总和、对方怪兽阶级等信息，快速获得需要除外的超量怪兽与融合怪兽等级。

## 功能特性

- 输入双方手牌及场上卡牌总合。
- 输入对方怪兽阶级（多个使用空格分隔）。
- 自动计算并展示每个怪兽阶级对应的联力炮所需资源（除外的超量 & 融合怪兽等级）。
- 响应式 UI，适配移动端。

## 使用方法

1. 打开应用后，在首页输入：
   - 双方手牌及场上卡牌总数量。
   - 对方场上的怪兽阶级（用空格分隔）。
2. 系统会自动根据公式进行计算，并在下方展示结果。

## 公式说明

对于每个怪兽阶级 `R` 和总卡牌数 `T`：

- 需要除外的超量怪兽等级：`T - R`
- 需要除外的融合怪兽等级：`R - (T - R)`

## 技术栈

- Vue 3
- uni-app
- 小程序跨平台支持（如微信小程序、H5、Android/iOS App）

## 目录结构

```
白银城-联力炮计算器/
├── App.vue
├── manifest.json
├── pages.json
├── readme.md
└── /pages
    └── /index
        └── index.vue
```

## 协议

本项目采用 [MIT License](https://opensource.org/licenses/MIT)，请自由使用、修改和分发。

---

### MIT License

> Copyright (c) 2024 Your Name

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
