# 技术栈

   + spark 2.4.4
   + hadoop 3.1.x
   + hive > 2.3.3
   + kafka 1.x,2.x
   + scala 2.11.12
   + java 1.8
   
# 项目介绍

    数据采集ETL处理,通过spark 平台抽取数据,并根据etl 相关函数,做数据处理
    新增数据源需要继承ZdhDataSources 公共接口,重载部分函数即可
 
# 项目编译打包
    项目采用gradle 管理
    打包命令,在当前项目目录下执行
    window: gradlew.bat release -x test
    linux : ./gradlew release -x test
    
    项目需要的jar 会自动生成到relase/libs 目录下
    
    如果想单独打包项目代码
    window: gradlew.bat jar
    linux : ./gradlew jar
    
# 部署
    1 先编译项目--参见上方项目编译打包
    2 下载release 目录修改启动脚本
    3 需要将release/copy_spark_jars 目录下的jar 拷贝到spark home 目录下的jars 目录
    4 启动脚本 start_server.sh
    
# 启动脚本
    注意项目需要用到log4j.properties 需要单独放到driver 机器上,启动采用client 模式
    在release/bin 目录下 修改start_server.sh 脚本中的BASE_RUN_PATH 变量为当前所在路径
    运行start_server.sh 脚本即可
      
    
# 停止脚本
     kill `ps -ef |grep SparkSubmit |grep zdh_server |awk -F ' ' '{print $2}'`

# 个人联系方式
    邮件：1209687056@qq.com