##SASS基础语法##

-	变量定义

<font color="red">如果变量需要镶嵌在字符串之中，就必须需要写在#{}之中。</font>

```css
$blue:#ff0000;
body:{background:#00f;}
```

```css
.bg {
  background: #00f;
}
```

-	计算功能

```css
.margin-h{
  margin-height:(20px/2)
}
```

```css
.margin-h {
  margin-height: 10px;
}

```

-	代码嵌套

```css
ul{
	width:100%;
	li{
		height:24px;
		line-height:24px;
		a{
			display:inline-block;
			&:hover{
				color:red
			}
		}
	}
}
```

```css
/* line 37, ../sass/common.scss */
ul {
  width: 100%;
}
/* line 39, ../sass/common.scss */
ul li {
  height: 24px;
  line-height: 24px;
}
/* line 42, ../sass/common.scss */
ul li a {
  display: inline-block;

/* line 44, ../sass/common.scss */
ul li a:hover {
  color: red;
}
```

-	代码继承

使用extend语法：class2继承class1两者会代码公用</p>

```css
.btn{
	@include countrycolor(china);
	@include border-radius(5px)
}
.primary{
	@extend .btn
}
```

```css
.btn, .primary {
  color: yellow;
  -moz-border-radius: 5px;
  -webkit-border-radius: 5px;
  border-radius: 5px;
}
```

-	Mixin

使用@mixin定义代码块 可以在形参中定义默认参数。当不传参数的时候使用默认参数

使用@include调用代码块

<font color="red">理解mixin和function的区别</font>

```css
@mixin countrycolor($country:blue){
	color:$country
}

.mycountry-china{
	@include countrycolor();
}
.mycountry-American{
	@include countrycolor(red);
}

```

再来一个复杂的mixin demo

```css
@mixin countryradius($vert,$horz,$radius:10px){
	border-#{$vert}-#{$horz}-radius:$radius;
	-moz-border-#{$vert}-#{$horz}-radius:$radius;
	-webkit-border-#{$vert}-#{$horz}-radius:$radius;
}
```

```css
/* 理解输出和调用的区别(#{$radius}和$radius)*/
/* line 67, ../sass/common.scss */
.china-radius {
  border-top-left-radius: 10px;
  -moz-border-top-left-radius: 10px;
  -webkit-border-top-left-radius: 10px;
}

/* line 70, ../sass/common.scss */
.american-radius {
  border-top-left-radius: 5px;
  -moz-border-top-left-radius: 5px;
  -webkit-border-top-left-radius: 5px;
}
```

-	function

自己来定义函数 函数一定要有返回值的(return前面要掉用一下@)

```css
@function double($n){
  @return $n*2;
}
.doublecont{
  width:double(10em)
}
```

```css
/* line 78, ../sass/common.scss */
.doublecont {
  width: 20em;
}

```

常用的颜色函数

```css
lighten
darken
grayscale /**重置成灰色**/
complement/*颜色反转*/
```

-	if else

```css
@mixin countrycolor($country){
	@if $country==france {
		color:red;
	}
	@else{
		color:yellow;
	}
}
.box{
	@include countrycolor(china);
}
```

```css
.mycountry-china {
  color: blue;
}
```

-	for循环

for循环有两种格式 一种是from start to end.另外一种是from start through end to不包含end throught b包含end

```css

@for $i from 1 to 5{
	.border-#{$i}{
		border:#{$i} solid #ccc;
	}
}

```

```css
/* line 83, ../sass/common.scss */
.border-1 {
  border: 1 solid #ccc;
}

/* line 83, ../sass/common.scss */
.border-2 {
  border: 2 solid #ccc;
}

/* line 83, ../sass/common.scss */
.border-3 {
  border: 3 solid #ccc;
}

/* line 83, ../sass/common.scss */
.border-4 {
  border: 4 solid #ccc;
}
```

-	each

```css
@each $member in jared,olynick,marcus,kevin,paul {
	.member-#{$member}{
		background:url('http://g.assets.com/pics/#{$member}.png')
	}

}
```

```css
/* line 97, ../sass/common.scss */
.member-jared {
  background: url("http://g.assets.com/pics/jared.png");
}

/* line 97, ../sass/common.scss */
.member-olynick {
  background: url("http://g.assets.com/pics/olynick.png");
}

/* line 97, ../sass/common.scss */
.member-marcus {
  background: url("http://g.assets.com/pics/marcus.png");
}

/* line 97, ../sass/common.scss */
.member-kevin {
  background: url("http://g.assets.com/pics/kevin.png");
}

/* line 97, ../sass/common.scss */
.member-paul {
  background: url("http://g.assets.com/pics/paul.png");
}
```

* sass的编译风格

sass提供四种编译风格

-	nested:嵌套缩进css代码，默认值
-	expanded:没有缩进、扩展的css代码
-	compact:简洁风格的css代码
-	compressed:压缩的css代码。一般生产环境采用这种风格
