需要启动三个独立的服务1、后台管理服务 2、对客户端提供api的服务 3、需要另外部署一个用于下载补丁文件的静态服务

1、下载部署所需要的文件(war包、配置文件、建库sql文件)  [war包下载](https://pan.baidu.com/s/1minrdgO#list/path=%2Ftinker-manager).

2、在mysql里面建一个数据库,建表sql在patchserver-manager/import.sql中

3、把hotfix-apis.properties和hotfix-console.properties两个配置文件放到/opt/config(*如果是windows部署，放置在tomcat对应的盘符下，假如tomcat在d://tomcat  配置文件放在d://opt/config下})目录下，并且修改里面对应的配置(数据源配置、访问路径配置、补丁存放目录)

4、把hotfix-apis.war hotfix-console.war放到tomcat下面的webapps目录下

等服务启动完毕就可以在浏览器上访问http://localhost:8080/hotfix-console

注意事项：

1. 注册问题，注册不成功(如果是直接使用的编译好的war包的话，需要再放入tomcat运行后，修改配置文件的值)
2. 上传补丁，也得注意下
3. 下载问题，本地路径映射，导致下载补丁出现问题，需要注意
4. tomcat虚拟路径映射 补丁文件存储路径file_storage_path=/Users/xiongxingxing/javaLearning/.tinker-manager  下载补丁文件静态服务器地址 patch-static-url=http://127.0.0.1/patch(命令行运行方式) (还须知道springBoot终端运行时如何配置虚拟路径)  war包下运行配置为`<Context path="/patch" docBase="/Users/xiongxingxing/javaLearning/.tinker-manager"/>`  file_storage_path=/Users/xiongxingxing/javaLearning/.tinker-manager patch-static-url=http://127.0.0.1:8080/patch




