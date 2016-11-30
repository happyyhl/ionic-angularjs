# ionic-angularjs
ionic+angularjs

###Jdk安装同时配置环境变量

        JAVA_HOME= C:\Program Files\Java\jdk1.8.0_60
        CLASSPATH= .;%JAVA_HOME%\lib;%JAVA_HOME%\lib\tools.jar
        Path= %JAVA_HOME%\bin;%JAVA_HOME%\jre\bin;
###安装ant ，配置ant环境变量
        ANT_HOME= D:\soft\apache-ant-1.9.7
        Path= %ANT_HOME%\bin;
###安装node ，注意安装路径不要带空格。
###配置淘宝镜像
        npm install -g cnpm --registry=https://registry.npm.taobao.org
###安装cordova
        cnpm install -g cordova
   
###安装 ionic
        cnpm install -g ionic
        可以同时安装
        cnpm install -g cordova ionic（安装cordova ionic） 
        cnpm update -g cordova ionic（更新cordova ionic） 
###启动 
        ionic start myApp blank（空项目） 
        ionic start myApp tabs（带导航条） //创建带有top栏和bottom栏的示例项目
        ionic start myApp sidemenu（带侧滑菜单）

        ionic serve 启动项目
###安装android-studio 
###配置android home环境变量
        ANDROID_HOME= D:\soft\Android\sdk
        Path=%ANDROID_HOME%\platform-tools;%ANDROID_HOME%\tools;
###打包命令
        ionic platform add android（添加android平台） 
        ionic platform remove android（移除android平台） 

        ionic build android（编译项目apk）ionic emulate android（运行项目apk 手机连接在手机运行 模拟器连接在模拟器运行） 
        ionic run android （相当于build + emulate） 

        ionic serve （开启服务调试） 

        ionic build iOS（编译项目ipk）ionic emulate ios（运行项目ipk） 

###ngcordova 插件使用方法
        <http://ngcordova.com/docs/>
####cordova 安装
        $ bower install ngCordova
####引入
        <script src="lib/ngCordova/dist/ng-cordova.js"></script>
        <script src="cordova.js"></script>

        angular.module('myApp', ['ngCordova'])
        举例 $cordovaFileTransfer
        cordova plugin add cordova-plugin-file-transfer