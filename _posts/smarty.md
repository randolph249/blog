###smarty学习笔记
* ####smarty comment: <&\*comment code\*&>
* ####smarty foreach
* #####foreach 用户循环数组
* #####foreach必须指定from和item属性
```php
<&$myarr=['Kevin','Paul','Rajon','Smarty']&>
<!--note:定义player的时候不能带$.引用的时候必须有$-->
<&foreach from=$myarr item=player&>
球员姓名：<&$player&>
<&/foreach&>
```
最后输出
```html
球员姓名：Kevin
球员姓名：Paul
球员姓名：Rajon
球员姓名：Smarty
````
* #####foreach 属性：[@index]()、 [@iteration]() [@first](), [@last](), [@show](), [@total]()

1.  ######<font color="red">$var@property是smarty3新增的语法</font>
2.  ######<font color="red">foreach的语法可以接受没有名称的属性，该语法是Smarty 3新增的。然而Smarty 2语法 {foreach from=$myarray key="mykey" item="myitem"}也同样支持。</font>
3.  ######<font color="red">即使你在循环语法里{foreach $myArray as $myKey => $myValue} 已经指定了key的变量名，但循环体内$myValue@key还是可用的</font>

  输出带有下表的数组
  ```php
  <&$myarr=['Kevin','Paul','Rajon','Smarty']&>
  <!--note:定义player的时候不能带$.引用的时候必须有$-->
  <&foreach from=$myarr item=player&>
  <&$player@index&><&$plaer@key&>球员姓名：<&$player&>
  <&/foreach&>
  ```
* #####foreach 语法：[break]()、[continue]()
  break:跳出循环
```
<&*新首页模块部分*&>
<div id="s_wrap" class="s-isindex-wrap">
<&$myarr=['Kevin','Paul','Rajon','Smarty']&>
<&foreach $myarr as $name&>
<&if $name@index==2&>
<&break&>
<&/if&>
<&$name@index&>球员姓名：<&$name&>
<&/foreach&>
```
continue:跳过本次循环执行下次循环
```
<&*新首页模块部分*&>
<div id="s_wrap" class="s-isindex-wrap">
<&$myarr=['Kevin','Paul','Rajon','Smarty']&>
<&foreach $myarr as $name&>
<&if $name@index==2&>
<&continue&>
<&/if&>
<&$name@index&>球员姓名：<&$name&>
<&/foreach&>
```

* ####smarty ifelse
* ####smarty function
* #####函数必须有函数名
```php
<&function name=menu&><&/function&>
```
* #####函数形参：可以给函数定义形参&执行形参默认值
```php
<!--形参名不能带$(是因为$表示真实变量？)-->
<&function name=menu val="100">$val is:<&$val&><&/function>
```
```php
<&menu value="200"&>//$value is:200?
<&menu&>//$value is:100?
```

* ####include
* ####extend
* ####smarty |
* #####|表示对|前面的内容执行|后面的方法。个人感觉就像在JS中的. 例如：$sid|cat:123 相当于JS中的 sid.concat([])
* ####smarty cat
* #####cat 将cat里的值连接到给定的变量后面.
* ####smarty strpos
* #####strpos php的用法.相当于JS中的indexOf  
