# angularjs入门小demo

- ng-app指令（得到页面结果为200）

```html
<!DOCTYPE html>
<html>
<head>
	<title>angularJS入门小demo-1 表达式</title>
	<script src="angular.min.js"></script>
</head>
<body ng-app>
	{{100+100}}
</body>
</html>
```

- ng-model指令（双向绑定，互相绑定）最显著特征

```html
<!DOCTYPE html>
<html>
<head>
	<title>angularJS入门小demo-2 双向绑定</title>
	<script src="angular.min.js"></script>
</head>
<body ng-app>
请输入姓名：<input ng-model="name">
<input ng-model="name">
{{name}}
</body>
</html>
```

- ng-init 初始化指令

```html
<!DOCTYPE html>
<html>
<head>
	<title>angularJS入门小demo-3 初始化指令</title>
	<script src="angular.min.js"></script>
</head>
<body ng-app ng-init="name='陈大海'">
请输入姓名：<input ng-model="name">
<input ng-model="name">
{{name}}
</body>
</html>
```

- 控制器指令

```html
<!DOCTYPE html>
<html>
<head>
	<title>angularJS入门小demo-4 控制器</title>
	<script src="angular.min.js"></script>
	<script>
		//建立模块
		var app=angular.module("myApp",[]);
		//创建控制器 $scope就是控制层与视图层之间交换数据的桥梁(类似与public，不加$scope就类似与private)
		app.controller("myController",function($scope){
			
			$scope.add=function(){
				return parseInt($scope.x)+parseInt($scope.y);//(默认字符串拼接)
			}
		});
	</script>
</head>
<body ng-app="myApp" ng-controller="myController">
	第一个数:<input ng-model="x"> 第二个数:<input ng-model="y">
	{{add()}}
</body>
</html>
```

