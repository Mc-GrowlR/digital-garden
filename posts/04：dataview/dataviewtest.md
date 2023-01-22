# 日记
```dataview
table file.cday as "文件创建日期"
from #日记 
```
# 英语
```dataview
list 
from #英语 
```

# 正在编辑
```dataview
table file.ctime as "文件创建时间",file.mtime as "文件修改时间",file.path as "文件路径"
where contains(editflag,0)
```
