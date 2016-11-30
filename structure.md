##具体结构
###应用可拆分成以下几个模块：
        1.一个服务模块，用来做服务的声明。
        2.一个指令模块，用来做指令的声明。
        3.一个过滤器模块，用来做过滤器声明。
        ......
        一个依赖以上模块的应用级模块，它包含初始化代码。

        index.html

		<!DOCTYPE html>
		<html>
		  <head>
		    <meta charset="utf-8">
		    <meta name="viewport" content="initial-scale=1, maximum-scale=1, user-scalable=no, width=device-width">
		    <!-- 忽略数字变为电话号码-->
		    <meta content="telephone=no" name="format-detection"/>
		    <title></title>

		    <link href="lib/ionic/css/ionic.css" rel="stylesheet">
		    <link href="videojs/video-js.css" rel="stylesheet">
		    <link href="css/style.css" rel="stylesheet">
		    <link href="lib/timepicer/timePicker.css" rel="stylesheet">
		    <script type="text/javascript" src="http://api.map.baidu.com/api?v=2.0&ak=5VmexbeKzGE9wNx0IqG5vS5t30r4TeHa"></script>
		    <script src="lib/ionic/js/ionic.bundle.js"></script>
		    <script src="lib/timepicer/timePicker.js"></script>
		    <script src="lib/ngCordova/dist/ng-cordova.js"></script>
		    <!-- cordova script (this will be a 404 during development) -->

		    <script src="cordova.js"></script>
		    <script src="js/moment.min.js"></script>
		    <script type="text/javascript" src="js/lib/jquery.min.js"></script>

		    <script src="videojs/video.js"></script>
		    <script src="videojs/videojs-contrib-hls.js"></script>
		    <!-- IF using Sass (run gulp sass first), then uncomment below and remove the CSS includes above
		    <link href="css/ionic.app.css" rel="stylesheet">
		    -->
		    <script src="js/app.js"></script>

		    <script src="js/ionic-citypicker-service.js"></script>
		    <script src="js/directives.js"></script>
		    <script src="js/controllers.js"></script>
		    <script src="js/routes.js"></script>
		    <script src="js/services.js"></script>
		    <script src="js/cfg.js"></script>
		    <script src="js/validate.min.js"></script>

		    <!-- Only required for Tab projects w/ pages in multiple tabs
		    <script src="lib/ionicuirouter/ionicUIRouter.js"></script>
		    -->

		  </head>
		  <body ng-app="app" animation="slide-left-right-ios7">
		    <div>
		        <div>
		          <ion-nav-bar class="bar-stable">
		            <ion-nav-back-button class="button-icon icon ion-ios-arrow-back">返回</ion-nav-back-button>
		          </ion-nav-bar>
		          <ion-nav-view></ion-nav-view>
		        </div>
		    </div>
		  </body>
		</html>
###app.js (初始化代码)
		angular.module('app', ['ionic', 'app.controllers', 'ngCordova', 'app.routes', 'app.directives', 'app.services', 'ionic-citypicker.service', 'CoderYuan'])
		.run(function($window, $ionicPlatform, $ionicPopup, $state, $rootScope, $cordovaStatusbar, $cordovaKeyboard, $cordovaSQLite, 	$ionicPopup, $location, $ionicHistory, $cordovaAppVersion) {  运行代码块
		 })
###route.js(路由配置)
		angular.module('app.routes', [])

		.config(function($stateProvider, $urlRouterProvider, $ionicConfigProvider, $httpProvider) {    配置代码块

		  delete $httpProvider.defaults.headers.common['X-Requested-With'];
		  $httpProvider.defaults.headers.post['Content-Type'] = 'application/x-www-form-urlencoded';
		  $httpProvider.interceptors.push('tokenInterceptor');

		  $ionicConfigProvider.platform.ios.tabs.style('standard');
		  $ionicConfigProvider.views.maxCache(0);
		  $stateProvider

		  .state('start', {
		    url: '/start',
		    templateUrl: 'templates/start.html',
		    controller: 'startCtrl'
		  })

		  .state('guide', {
		    url: '/guide',
		    templateUrl: 'templates/exercitation/guide.html',
		    controller: 'guideCtrl'
		  })

		  $urlRouterProvider.otherwise('/start')

		});
###service.js
		angular.module('app.services', [])

		.factory('tokenInterceptor', function ($rootScope, $q, $window) {
		  return {
		    request: function (config) {
		      config.auth = config.auth || {};
		      // 设置你的header
		      if ($window.localStorage.token) {
		        config.headers.token = $window.localStorage.token;
		        // config.headers.Authorization = 'Bearer ' + $window.sessionStorage.token;
		      }
		      return config;
		    },
		    responseError: function (rejection) {
		      if (rejection.status === 401) {
		        // handle the case where the user is not authenticated
		      }
		      return $q.reject(rejection);
		    }
		  };
		})

		.factory('BlankFactory', [function(){

		}])

		.service('BlankService', [function(){

		}]);
###controller.js
		angular.module('app.controllers', ['ionic', 'ngAnimate'])
		.controller('startCtrl', function($scope, $window, $rootScope, $state, $ionicLoading, $timeout, $interval, $http, $cordovaSQLite, $ionicHistory) {
		})