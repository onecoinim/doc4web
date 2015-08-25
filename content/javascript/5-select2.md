1. Jquery select2插件

[官方网站](https://select2.github.io/)
[github](https://github.com/select2/select2)
[常用操作](http://www.danqingyu.com/138.html)

常用操作
```
//单选
$(".qingyu").click(function () { alert("Selected value is: "+$("#qingyu").select2("val"));});//获取选中值
$(".qingyu").click(function () { alert("Selected value is: "+$("#qingyu").select2("data").text);});//获取文本
$(".qingyu").click(function () { $("#qingyu").select2("val", "CA"); });//设置选中值
$(".qingyu").click(function() { $("#qingyu").select2("val", ""); });//清除选中值为初始值
$(".qingyu").click(function () { var data = $("#qingyu").select2("data"); delete data.element; alert("Selected data is: "+JSON.stringify(data));});//下拉框元素信息
$(".qingyu").click(function () { $("#qingyu").select2("data", {id: "CA", text: "California"}); });//添加且选中
$(".qingyu").click(function () { $("#qingyu").select2("open"); });//打开下拉框
$(".qingyu").click(function () { $("#qingyu").select2("close"); });//关闭下拉框

//多选
$(".qingyu").click(function () { alert("Selected value is: "+$("#e8_2").select2("val"));});//获取选中值
$(".qingyu").click(function () { $("#qingyu").select2("val", ["CA","MA"]); });//设置选中值
$(".qingyu").click(function () { alert("Selected value is: "+JSON.stringify($("#qingyu").select2("data")));});//下拉框元素信息
$(".qingyu").click(function () { $("#qingyu").select2("data", [{id: "CA", text: "California"},{id:"MA", text: "Massachusetts"}]); });//添加且选中
$(".qingyu").click(function() { $("#qingyu").select2("val", ""); });//清除选中值为初始值
$(".qingyu").click(function () { $("#qingyu").select2("open"); });//打开下拉框
$(".qingyu").click(function () { $("#qingyu").select2("close"); });//关闭下拉框
```