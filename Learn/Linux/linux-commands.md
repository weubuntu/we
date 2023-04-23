# commands
```bash
# 文件权限备份与恢复
getfacl -R /directoryOrFile > permis.facl #备份目录或文件的权限到permis.facl
setfacl --restore=permis.facl #从permis.facl文件恢复文件中记录的权限信息

```
`grep -r [PATTERN] ./* ` _查找当前文件夹下文件内字符_  
`find ./ -type f -name "*.txt"` _查找当前目录下文件类型为txt的文件_
`netstat -tunlp |grep [port] ` _查看对应端口占用情况_  
`netstat -anp |grep [port] ` _查看对应端口占用情况_  
`mysqldump -u root -p --databases dbname1 dbname2 > dumpmysql.sql ` _备份多个数据库_  
`mysql -u username -P  dbname < dumpmysql.sql` _恢复单个数据库_  
`mysqldump -u root -p --all-databases > all.sql` _备份全部数据库_  
`mysql -u root -p < all.sql ` _恢复全部数据库_  

