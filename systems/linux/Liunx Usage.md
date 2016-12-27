#Liunx Usage

> ubuntu 删除文件和文件夹命令--**rm**

```shell
#删除文件
rm filename

#删除文件夹
rm -r foldername
```

> ubuntu 解压缩命令--**tar**

```shell
#目标文件格式是*.tar.*

#操作命令参数
-c: 建立压缩档案
-x：解压
-t：查看内容
-r：向压缩归档文件末尾追加文件
-u：更新原压缩包中的文件
#文件属性命令参数
-z：有gzip属性的
-j：有bz2属性的
-Z：有compress属性的
-v：显示所有过程
-O：将文件解开到标准输出
#必要参数
-f： 使用档案名字，切记，这个参数是最后一个参数，后面只能接压缩名

#完整案例
##解压
tar –xvf 	file.tar  		#解压 tar包
tar -xzvf 	file.tar.gz 	#解压tar.gz
tar -xjvf 	file.tar.bz2   	#解压 tar.bz2
tar –xZvf 	file.tar.Z   	#解压tar.Z
###另外对rar,zip
unrar e file.rar 			#解压rar
unzip 	file.zip 			#解压zip

##压缩
tar –cvf jpg.tar 		*.jpg  		#将目录里所有jpg文件打包成tar.jpg
tar –czf jpg.tar.gz 	*.jpg   	#将目录里所有jpg文件打包成jpg.tar后，并且将其用gzip压缩，生成一个gzip压缩过的包，命名为jpg.tar.gz
tar –cjf jpg.tar.bz2 	*.jpg 		#将目录里所有jpg文件打包成jpg.tar后，并且将其用bzip2压缩，生成一个bzip2压缩过的包，命名为jpg.tar.bz2
tar –cZf jpg.tar.Z 		*.jpg   	#将目录里所有jpg文件打包成jpg.tar后，并且将其用compress压缩，生成一个umcompress压缩过的包，命名为jpg.tar.Z
```

> 进入与退出文件夹--**cd**

```shell
#进入文件夹
cd foldername | path

#退出当前文件夹
cd ..

#回到根目录
cd /
```

> 切换权限和用户--**su&sudo**

```shell
#提升做某事的权限
sudo xxxx
eg: sudo vim hello.conf #conf在一般user中只有only-read 权限，这时使用sudo

#切换root及切换回user态
su 				#切换root
su username 	#切换user
```

> window&linux文件上传下载--**pscp**

```shell
#上传文件到linux根目录
##usage：pscp   [options]   source   [source...]   [user@]host
pscp F:\employees_db-full-1.0.6.tar.bz2 ubuntu@123.207.120.226:		

#下载文件到windowsF盘
##usage：pscp [options] [user@]host:source target
pscp ubuntu@123.207.120.226:hello.cpp f:\
#查看主机指定目录的所有文件
##usage：pscp [options] -ls [user@]host:filespec
pscp -ls ubuntu@123.207.120.226:

```



