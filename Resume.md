## 基本信息

 - 李希望/男/26
 - 河南大学/计算机科学与技术专业/本科
 - 工作年限：3年
 - 求职意向：Web前端
 - Github: https://github.com/lxw15337674

## 联系方式

- 手机/微信：15515255978
- Email：404174262@qq.com

## 职业技能

- 熟练使用Vue全家桶，能够基于业务封装公共组件，有大型PC端项目开发经验。
- 了解Webpack、Rollup脚手架工具，能够独立完成项目脚手架搭建。

## 工作经历
公司名称：**新华三技术有限公司**

在职时间：2017/07 ~ 至今

技术栈：Vue、ElementUI、Stylus、Echarts。

工作描述：

- 部门轮岗半年，参与解决方案部、技术服务部的工作。
- 使用echarts开发多个数据可视化大屏。
- 从0到1参与数据中台项目、协助开发政府服务平台项目。
- 基于业务需求，封装Vue公共组件供部门内部使用。
- 基于vue-cli搭建部门前端脚手架，引入ESlint+Prettier规范前端代码风格。
- 引入jenkins进行持续集成，推动部门测试流程改进。
- 参与部门内部微信小程序及h5技术选型。

## 项目经历

#### 数据中台

- 项目时间：2018.06-至今

- 项目描述：向政府内部提供数据填报、数据管理、数据共享、数据应用等功能模块的基础数据平台。

- 负责内容：担任组长和主开发，深度参与系统各个功能模块从提出到落地的整个流程，包括客户交流、功能需求梳理、原型图设计、开发计划制定、人员协调、功能开发。

- 项目难点：
  
  - 在使用`element-ui`的`el-table`，`row-click`事件没有提供行的索引值。
  
    解决方式：添加index作为每行的class，点击时再从class中获取。并给官方提了[issue](https://github.com/ElemeFE/element/issues/17152)。
  
  - element-ui的`el-form`无法满足分页表格的多数据校验。
  
    解决方式：研究`element-ui`源码找到使用的`async-validator`异步校验库，并利用webWorkers封装校验库满足功能需求。
  
  - 页面参数的缓存
  
    利用keep-alive组件、sessionStorage实现[页面缓存mixin](https://github.com/lxw15337674/toys/tree/master/vue/mixins)。

#### 政务服务平台

- 项目时间：2020.03-2020.05

- 项目描述：通过给企业打标签实现政策精准推送、政策申报、政企交流等功能，促进政府与企业的沟通。

- 负责内容：

  - 参与系统的功能原型图设计。
  - 搭建基于数据中台后台管理模块的前端脚手架。
  - 担任主开发，参与标签管理、权限管理、数据填报等功能的开发。

- 项目难点：

  - 使用`element-ui`的`el-dialog`，宽高固定、无法实现拖拽。

    解决方式：封装使对话框支持拖动、拉伸、双击全屏的对话框增强指令。[在线Demo](http://jsrun.net/mMfKp)

  - 使用`element-ui`的`el-upload`，无法显示多文件上传的上传进度、上传速度、文件大小等

    解决方式：参考百度网盘的上传列表界面，封装文件上传组件。[在线Demo](http://jsrun.net/SY2Kp)

## 个人项目

#### 在线文档

- 项目描述：基于DOM的在线Excel，功能类似于腾讯文档。目前实现表格的虚拟滚动、右键操作、单元格选取、行列拉伸、导入导出等基本功能。
- 项目地址：https://github.com/lxw15337674/xlsx

### v-virtualScroller

- 项目介绍：支持横纵向的虚拟滚动组件。
- 项目地址：https://github.com/lxw15337674/v-virtualScroller

### v-contextMenu

- 项目介绍：支持功能快捷键的右键菜单组件。

- 项目地址：https://github.com/lxw15337674/v-contextMenu

### v-tip

- 项目介绍：支持复杂展示的的vue提示框指令。
- 项目地址：https://github.com/lxw15337674/v-tip