# 我的jquery学习记录

markdown的使用说明(http://www.jianshu.com/p/q81RER) (http://wowubuntu.com/markdown/)

## 一、.html() .text() .val()的区别
[jquery的html,text,val](http://www.cnblogs.com/aqbyygyyga/archive/2011/11/03/2234926.html)
> .html(),.text(),.val()三种方法都是用来读取选定元素的内容；只不过
.html()是用来读取元素的HTML内容（包括其Html标签），
.text()用来读取元素的纯文本内容，包括其后代元素，
.val()是用来读取表单元素的"value"值。
其中.和.text()方法**不能**使用在表单元素上,而.val()**只能**使用在表单元素上；
另外.html()方法使用在多个元素上时，只读取第一个元素；
.val()方法和.html()相同，如果其应用在多个元素上时，只能读取第一个表单元素的"value"值，但是.text()和他们不一样，如果.text()应用在多个元素上时，将会读取所有选中元素的文本内容。

        <div class="demo">
         	<p><strong>hello world</strong></p>
         	<p><strong>hello2 world2</strong></p>
         	<input class="demo2" type="text" value="杨" />
        </div>
        
        $(function(){
        	alert($(".demo p").text());//将显示hello world
        	alert($(".demo p").html());//将显示<strong>hello world</strong>
        	alert($(".demo2").val()) //将显示杨
        })

## 二、层次选择器空格与>的区别
空格会选择父辈元素下了所子子元素，>则只选择第一个子元素
        
        <div>码农家族
            <p>
               <label>1</label>
            </p>
            <label>2</label>
        </div>
        
        <script type="text/javascript">
            $("div label").css("background-color","blue");//这个既会把div下的label(2)选择也会把div下的p下的label(1)选择
        </script>

## 三、选择器
  1. :eq(index)过滤选择器 可以使用负数表示倒数某个元素，如$("li:eq(-1)")表示倒数第一个li元素
  2. prev + next选择器 选择的是prev下的相邻元素next的第一个元素(下级)
  3. prev ~ siblings选择器 选择的是和prev为兄弟元素的所有元素(下级)
  4. :has(selector)过滤选择器 这里的selector是一个选择器($("li:has('label')"))
  5. :contains(text)过滤选择器 这里的text是网页中的文本($("li:contains('hello world')"))
  6. :hidden过滤选择器 可以选择到display:none 和type='hidden'的元素
  7. [attribute\*=value]属性选择器 指包含value的元素如$("li[title\*='果']")所有title中包含有'果'字的li元素
  8. :input表单选择器 不仅可以选择Input表单，还可以选择<textarea>、<select> 和 <button>标记的表单元素,:input前面有一个空格
  9. :submit提交按钮选择器 $("#frmTest input:submit") 这里input必不可少，少了以后会把普通的button也选择上
 
## 四、操作样式
1. 通过addClass()和css() 使用css可一次性的赋予多个值 $("#content").css({"color":'white',"background":'blue'})，单个值使用$("#content").css("color"，'white')
2. 使用appendTo()方法向被选元素内插入内容 $(content).appendTo(selector),$($html).appendTo(".green")
3. 使用before()和after()在元素前后插入内容 $(selector).before(content)和$(selector).after(content)
4. 替换内容 replaceWith()和replaceAll() $(selector).replaceWith(content)和$(content).replaceAll(selector)
5. 使用remove()和empty()方法删除元素 remove()方法删除所选元素本身和子元素,通过添加过滤参数指定需要删除的某些元素 如$("span").remove(".red") 表示删除class为red的span元素,empty则**无此参数**
 
 
 
 
 
