## 4.27

1.描述下如何实作用户找回密码的功能

思路：

```
可以参考：[Ruby on Rails章节](https://railstutorial-china.org/book/chapter12.html)
还要考虑到重置密码的链接（验证码）需在15分钟或30分钟后失效
```

2.假设数据表里有以下的用户信息：

```
id: 1, location: beijing
id: 2, location: shanghai
id: 3, location: beijing
id: 4, location: hangzhou
id: 5, location: suzhou
id: 6, location: hangzhou
```

前端如何以location分组显示并计算每个location里的人数？

思路：

用group_by方法以location排序 `@users = User.all.group_by{ |u| u.location }`
views页面写为
```
<% @users.each do |location, users| %>
  <%= location %>(<%= users.count %>)
  <% users.each do |user| %>
    #show user info
  <% end %>
<% end %>
```
3.如何让页面固定左右两块布局，当一边的高度发生变化时，另一边的高度随之变化并保持一致。

思路：
```
<html>
	<head>
    <style>
  		.left-block {
    		background: red;
    		float: left;
    		width: 30%;
  		}

  		.right-block {
    		background: #aaa;
    		float: right;
    		width: 70%;
  		}
  	</style>
	</head>
  <body>
    <div class="left-block">
    	I am on the left<br>
    	another row
 		</div>
		<div class="right-block">
 			I am on the right
		</div>
		<script>
      var leftHeight = $(".left-block").height();
  		var rightHeight = $(".right-block").height();
  		if (leftHeight >= rightHeight) {
    		$(".right-block").height(leftHeight);
  		} else {
    		$(".left-block").height(rightHeight);
  		};
		</script>
  </body>
</html>
```
 

