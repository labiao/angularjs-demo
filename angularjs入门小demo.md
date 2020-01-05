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

- 事件指令

  ```html
  <!DOCTYPE html>
  <html>
  <head>
  	<title>angularJS入门小demo-5 事件指令</title>
  	<script src="angular.min.js"></script>
  	<script>
  		//建立模块
  		var app=angular.module("myApp",[]);
  		//创建控制器 $scope就是控制层与视图层之间交换数据的桥梁(类似与public，不加$scope就类似与private)
  		app.controller("myController",function($scope){
  			
  			$scope.add=function(){
  				$scope.z= parseInt($scope.x)+parseInt($scope.y);//(默认字符串拼接)
  			}
  		});
  	</script>
  </head>
  <body ng-app="myApp" ng-controller="myController">
  	第一个数:<input ng-model="x"> 第二个数:<input ng-model="y">
  	<button ng-click="add()">运算</button>
  	运算结果：{{z}}
  </body>
  </html>
  ```

- 循环数组

- ```html
  <!DOCTYPE html>
  <html>
  <head>
  	<title>angularJS入门小demo-6 循环数组</title>
  	<script src="angular.min.js"></script>
  	<script>
  		//建立模块
  		var app=angular.module("myApp",[]);
  		//创建控制器 $scope就是控制层与视图层之间交换数据的桥梁(类似与public，不加$scope就类似与private)
  		app.controller("myController",function($scope){
  			$scope.list=[102,203,394,555];
  		});
  	</script>
  </head>
  <body ng-app="myApp" ng-controller="myController">
  	<table>
  		<tr ng-repeat="x in list">
  			<td>{{x}}</td>
  		</tr>
  </body>
  </html>
  ```

  循环对象数组

  ```html
  <!DOCTYPE html>
  <html>
  <head>
  	<title>angularJS入门小demo-7 循环对象数组</title>
  	<script src="angular.min.js"></script>
  	<script>
  		//建立模块
  		var app=angular.module("myApp",[]);
  		//创建控制器 $scope就是控制层与视图层之间交换数据的桥梁(类似与public，不加$scope就类似与private)
  		app.controller("myController",function($scope){
  			$scope.list=[
  			{name:'张三',shuxue:100,yuwne:100},
  			{name:'李四',shuxue:90,yuwne:92},
  			{name:'张三',shuxue:40,yuwne:50}
  			];
  		});
  	</script>
  </head>
  <body ng-app="myApp" ng-controller="myController">
  	<table>
  		<tr>
  			<td>姓名</td>	
  			<td>数学</td>
  			<td>语文</td>
  		</tr>
  		<tr ng-repeat="entity in list">
  			<td>{{entity.name}}</td>	
  			<td>{{entity.shuxue}}</td>
  			<td>{{entity.yuwen}}</td>
  		</tr>
  	</table>
  </body>
  </html>
  ```

- 内置服务

  ```
  <!DOCTYPE html>
  <html>
  <head>
  <meta charset="UTF-8">
  <title>angularJS入门小demo-8 内置服务$http</title>
  <script src="angular.min.js"></script>
  <script>
  		//建立模块
  		var app=angular.module("myApp",[]);
  		//创建控制器 $scope就是控制层与视图层之间交换数据的桥梁(类似与public，不加$scope就类似与private)
  		app.controller("myController",function($scope,$http){
  			$scope.findList=function(){
  				$http.get("data.json").success(//data.json文件中的格式要正规，加双引号
  						function(response){
  							$scope.list=response;
  						});//success方法的参数是函数类型。ajax请求
  			}
  			//$scope.findList();别的页面用到这个控制器也会调用这个函数。
  		});
  	</script>
  </head>
  <body ng-app="myApp" ng-controller="myController" ng-init="findList()">
  	<table>
  		<tr>
  			<td>姓名</td>	
  			<td>数学</td>
  			<td>语文</td>
  		</tr>
  		<tr ng-repeat="entity in list">
  			<td>{{entity.name}}</td>	
  			<td>{{entity.shuxue}}</td>
  			<td>{{entity.yuwen}}</td>
  		</tr>
  	</table>
  </body>
  </html>
  ```

  