# less

标签（空格分隔）： css css预处理语言

---
less 之坑(1)
`<link rel="stylesheet" href="./css/index.css">`
>注意引用时要引编译过的 css 文件

#### sublime + less + node 实现 less 自动编译
**sublime 插件需求**：
1.  less 语法高亮
2.  less2css(less to css)
    -   保存 less 文件时，自动生成同名 css 文件
    -   保存 less 时提示编译错误
    -   批量编译项目目录中所有 less 为 css

**npm 安装 less 相关依赖包**
> npm install -g less
  npm install less-plugin-clean-css -g

注释 //不会被编译
变量 && 变量计算
```
// 变量
@width: 200px;
.box{
	width: @width;
	height: @width/4;
	background: green;
	.boxstyle();
}
```
混合 相当于 js 中定义函数并实现函数调用
```
//混合
.boxstyle(@radius:5px) {
	-webkit-border-radius: @radius;
	-moz-border-radius: @radius;
	border-radius: @radius;
}
.box{
	width: @width;
	height: @width/4;
	background: green;
	.boxstyle();
}
```
匹配模式
```

//匹配模式 写三角
.trangle(@_) {
	width: 0;
	height: 0;
	overflow: hidden;
}
.trangle(top,@color,@w){
	border: solid @w/4;
	border-color: @color transparent transparent transparent;
}
.trangle(right,@color,@w){
	border: solid @w/4;
	border-color: transparent @color transparent transparent;
}
.trangle(bottom,@color,@w){
	border: solid @w/4;
	border-color: transparent transparent @color transparent;
}
.trangle(left,@color,@w){
	border: solid @w/4;
	border-color: transparent transparent transparent @color;
}
.endtrangle {
	.trangle(left,#f60,200px)
}
```
嵌套规则
```
// less 里的嵌套规则
ul {
	margin-top: 10px;
	li {
		line-height: 20px;
		background-color: #fcfcfc;

		a {
			text-decoration: none;
			padding: 0 10px;
			color: #000;
			display: block;

			//& 表示上一层目录
			&:hover {
				background-color: #ababab;
			}
		}
	}
}
```





