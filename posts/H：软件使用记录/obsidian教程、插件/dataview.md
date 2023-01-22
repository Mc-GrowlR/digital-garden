
## 代码范例

```
list
from ""
where file.mday = date(2022-05-19)
```

**群内解答：**
![](https://growlr-center-blog-image.oss-cn-beijing.aliyuncs.com/image/MSCNFQK$BR%7DP3613AM%7D8_KW.jpg)
![](https://growlr-center-blog-image.oss-cn-beijing.aliyuncs.com/image/20220519232510.png)


## dataview

    定期笔记

假设您有一个格式为 YYYY-MM-DD 的每日笔记，您应该如此编写 md 链接，如下所示：

- `$= '[['+moment().format("YYYY-MM-DD")+'|今天]]'`

获取过去 24 小时内修改过的所有文件：

LIST WHERE file.mtime >= date(today) - dur(1 day)
查找所有未标记为已完成且已超过一个月的项目：

LIST FROM #projects
WHERE ! completed AND file. ctime <= date (today) - dur (1 month)

```

CALENDAR file.mtime
FROM #日记 
WHERE file.cday=date(today)

```

## 聚合标签
```
//dataviewjs
// 基于文件夹聚类所有的标签。
for (let group of dv.pages("").filter(p => p.file.folder != "").groupBy(p => p.file.folder.split("/")[0])) {
  let datas=dv.pages(`"${group.key}"`).file.tags.distinct().map(t => {return `[${t}](${t})`}).array()
  let lens=datas.length
dv.paragraph(`## ${group.key} (${lens})`);

  dv.paragraph(
    datas.sort().join(" | "));
}
```