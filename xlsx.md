# xlsx
[github链接](https://github.com/SheetJS/sheetjs)

前端操作excel的库。

## 相关概念

excel名词 | js-xlsx对应类型
-- |--
工作簿  | workBook
工作表 | Sheets
Excel引用样式(单元格地址) | cellAddress
单元格 | cell

excel数据操作的基本流程：
1. 打开xlsx文件（工作簿）
2. 打开一个工作表
3. 选中一个单元格
4. 针对数据进行操作
5. 保存（另存为）