### css 选择器

- 通配选择器(星号\*)
  不推荐使用，因为是性能最低的一个选择器
- 标签选择器
- 类选择器
- ID 选择器
- 属性选择器(通过属性名或属性值匹配元素)
  [MDN 的例子](https://developer.mozilla.org/zh-CN/docs/Web/CSS/Attribute_selectors)
- 伪类选择器

  以下为我常用的，还有更多的伪类选择器没写出来

  - 伪类(用单冒号)
    - :active
      被激活的元素(常用于 tab 切换)
    - :checked
      被选中的元素(常用于单选按钮和多选按钮)
    - :disabled
      被禁用(在 form 表单中的提交按钮)
    - :first-child
      一组兄弟元素中的第一个(parent 不是必须的)
    - :last-child
      一组兄弟元素中的最后
    - :has
    - :nth-of-type
    - :nth-child
      > nth-of-type 与 nth-child 的区别:nth-of-type 只限于同种类型的标签元素兄弟,nth-child 可以是多个不同类型的标签元素兄弟。
  - 伪元素(用双冒号，区分伪类)
    - ::placeholer
    - ::before
    - ::after

- 基于关系的选择器

  - 相邻兄弟选择器  
    p + span,第二个元素紧跟第一个元素，并且有同一个父元素。

  - 通用兄弟选择器  
    p ~ span ,p 标签的后面所有兄弟。

  - 子代选择器  
    p > span,p 标签的所有第一代子元素。

  - 后代选择器
    p span,p 标签的所有子代包括(孙子等)。

### css 选择器的权重

1. 内联样式 > ID 选择器 > 类、属性、伪类选择器 > 标签、伪元素选择器
2. 通配符(\*),子代选择器(>),相邻选择器(+)等不影响以上的优先级
3. 最后是继承的样式
