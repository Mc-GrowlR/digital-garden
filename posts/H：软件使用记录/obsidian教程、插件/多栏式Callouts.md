该 CSS 片段能够使文档内容分段显示

仓库地址：
[MCL Multi Column.css](https://github.com/efemkay/obsidian-modular-css-layout/blob/main/MCL%20Multi%20Column.css)

教程摘录自：

[[Obs＃83] 多欄式Callouts! 直接套用CSS片段變身N欄～](http://jdev.tw/blog/7080)

MCL Multi Column.css是一個不到8KB大小的CSS檔，只要存入儲存庫**.obsidian/snippets**資料夾並在外觀裡啟用此CSS片段，就能以下列方法呈現更多變化：

1.  多欄式呈現筆記的Callouts內容
2.  指定Callouts的顯示大小與浮動位置(浮動位置在閱讀模式生效)
3.  將無序列表變成多欄顯示(在閱讀模式生效，Callouts裡也會生效)

> \[!info\] MCL?  
> MCL是「Modular CSS Layout」的縮寫

> \[!tip\] Callouts類型  
> 1\. 顯示標題列：> \[!multi-column\]  
> 2\. 隱藏標題列：> \[!blank-container\]
> 
> \[!tip\] 使用方法  
> 1\. 欄位間用一個 > 分隔  
> 2\. 每個Callout區塊多增加一個 >  
> 3\. 欄位數由2到N，只要螢幕寬度足夠，會自動分配欄寬  
> 4\. **可使用Style Settings外掛設定**

![01](https://raw.githubusercontent.com/emisjerry/upgit/master/2022/04/upgit-20220423_1650685342.png)

#### 1.1. 兩欄

```
> [!multi-column]
>
>> [!note]+ 待辦事項
>> your notes or lists here. using markdown formatting
>
>> [!warning|right-small]+ 進行中事項
>> your notes or lists here. using markdown formatting

```

```
> [!multi-column]
>
>> [!note]+ 待辦事項
>> your notes or lists here. using markdown formatting
>
>> [!warning]+ 進行中事項
>> your notes or lists here. using markdown formatting
>
>> [!success]+ 已完成事項
>> your notes or lists here. using markdown formatting

```

#### 1.3. 三欄

![01|700](https://raw.githubusercontent.com/emisjerry/upgit/master/2022/04/upgit-20220423_1650685415.png)

```
> [!multi-column]
>
>> [!note]+ 待辦事項
>> * Item 1
>>    * Item 1-1
>>    * Item 1-2
>>    * Item 1-3
>>
>>> [!EXAMPLE] 範例
>>> ```
>>> String msg = "Hello, world!";
>>> ```
>
>> [!warning]+ 進行中事項
>> 使用圖片：
>> ![[Obs＃83 多欄式Callouts! 直接套用CSS片段變身N欄～ image 1.png]]
>
>> [!success]+ 已完成事項
>> 使用影片：
>>
>> [用Obsidian學會Markdown|embded](https://youtu.be/lnsQsFCYhNc)

```

#### 1.4. 四欄

![01|700](https://raw.githubusercontent.com/emisjerry/upgit/master/2022/04/upgit-20220423_1650685499.png)

```
> [!multi-column]
>
>> [!note]+ 待辦事項
>> your notes or lists here. using markdown formatting
>
>> [!warning]+ 進行中事項
>> your notes or lists here. using markdown formatting
>
>> [!success]+ 已完成事項
>> your notes or lists here. using markdown formatting
>
>> [!info]+ 說明
>> your notes or lists here. using markdown formatting

```

#### 1.5. 五欄

```
> [!multi-column]
>
>> [!note]+ 待辦事項
>> your notes or lists here. using markdown formatting
>
>> [!warning]+ 進行中事項
>> your notes or lists here. using markdown formatting
>
>> [!success]+ 已完成事項
>> your notes or lists here. using markdown formatting
>
>> [!info]+ 說明
>> your notes or lists here. using markdown formatting
>
>> [!quote]+ 引用
>> your notes or lists here. using markdown formatting

```

#### 1.6. 六欄

```
> [!multi-column]
>
>> [!note]+ 待辦事項
>> your notes or lists here. using markdown formatting
>
>> [!warning]+ 進行中事項
>> your notes or lists here. using markdown formatting
>
>> [!success]+ 已完成事項
>> your notes or lists here. using markdown formatting
>
>> [!info]+ 說明
>> your notes or lists here. using markdown formatting
>
>> [!quote]+ 引用
>> your notes or lists here. using markdown formatting
>
>> [!error]+ Expired!
>> your notes or lists here. using markdown formatting

```

#### 1.7. 隱藏標題列

```
> [!multi-column]
>
>> [!blank-container]+ 待辦事項
>> * Item 1
>>    * Item 1-1
>>    * Item 1-2
>>    * Item 1-3
>> * Item 2
>>> [!EXAMPLE] 範例
>>> ```
>>> String msg = "Hello, world!";
>>> ```
>
>> [!blank-container]+ 進行中事項
>> 使用圖片：
>> ![[Obs＃83 多欄式Callouts! 直接套用CSS片段變身N欄～ image 1.png]]
>
>> [!blank-container]+ 已完成事項
>> 使用影片：
>>
>> [用Obsidian學會Markdown](https://youtu.be/lnsQsFCYhNc)

```

```
> [!error|right-small] 浮動到右側
> 小視窗，靠右

```

擴充Callouts的語法，在Callout類型後加上Pipe，再輸入下列設定：

> \[!tip\] 語法
> 
> > \[!Callout類型|left/right-small/medium/large\]  
> > \[!blank-container|left/right-small/medium/large\]

> \[!tip\] 使用說明  
> 1\. YAML區加入`cssClasses: 多欄CSS`即會自動顯示成指定的欄數  
> 2\. 多欄CSS有下列幾種：
> 
> > 1.  two-column-list: 垂直填充
> > 2.  three-column-list: 垂直填充
> > 3.  two-column-grid-list: 水平填充
> > 4.  three-column-grid-list: 水平填充

-   [efemkay/obsidian-modular-css-layout: CSS Layout hack for Obsidian.md](https://github.com/efemkay/obsidian-modular-css-layout)
-   [MCL Multi Column.css](https://github.com/efemkay/obsidian-modular-css-layout/blob/main/MCL%20Multi%20Column.css)

<iframe src="https://www.youtube.com/embed/sEogbW4UGYo" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen="" width="650" height="315" frameborder="0"></iframe>

＃＃

#### 您可能也會有興趣的類似文章

-   [\[Obs＃84\] 另一個更簡便的筆記分欄作法：使用Columns外掛](http://jdev.tw/blog/7088/obsidian-columns-plugin "2022/04/30") (0則留言, 2022/04/30)
-   [\[Obs＃82\] 用Obsidian學會Markdown–Markdown完整解析](http://jdev.tw/blog/7066/markdown-tutorial-with-obsidian "2022/04/09") (0則留言, 2022/04/09)
-   [\[Obs＃86\] 分享與編輯器相關的21個Obsidian外掛](http://jdev.tw/blog/7102/21-obsidian-plugins-for-editor "2022/05/08") (0則留言, 2022/05/08)
-   [\[Obs＃22\] 讓有效學習更簡單！Markdown匯出到Anki | 使用Flashcards外掛](http://jdev.tw/blog/6505/obsidian-plugin-flashcards-integrates-anki "2020/12/12") (0則留言, 2020/12/12)
-   [Obsidian(黑曜石) 每日筆記的運用與AutoHotkey腳本快捷按鍵](http://jdev.tw/blog/6337/obsidian-daily-notes-and-autohotkey-scripts "2020/07/04") (0則留言, 2020/07/04)
-   [\[Obs＃39\] 利用CSS變更文字顏色，侵入性小](http://jdev.tw/blog/6663/8%ef%bc%8b8-highlight-colors-css-change-text-colors "2021/05/10") (0則留言, 2021/05/10)
-   [\[Obs＃85\] 分享使用中與外觀有關的10個外掛](http://jdev.tw/blog/7095/obsidian-ui-related-10-plugins "2022/05/01") (0則留言, 2022/05/01)
-   [Obsidian(黑曜石) 高亮度顯示或變更文字顏色的3種方法](http://jdev.tw/blog/6329/obsidian-md-text-highlight "2020/07/01") (4則留言, 2020/07/01)
-   [快速產生HTML網頁格式的速記語法：Markdown](http://jdev.tw/blog/3504/all-about-markdown "2013/09/20") (0則留言, 2013/09/20)
-   [\[Obs＃79\] 有序列表自動重新編號的方法](http://jdev.tw/blog/7051/obsidian-ordered-list-auto-numbering "2022/03/27") (0則留言, 2022/03/27)
-   [\[Obs＃59\] Obsidian快速開啟常用筆記（2）：不使用外掛的簡單方法](http://jdev.tw/blog/6914/obsidian-create-hot-notes-rapidly "2021/10/27") (0則留言, 2021/10/27)
-   [超強筆記軟體Obsidian (黑曜石)介紹與Zettelkasten筆記系統簡述](http://jdev.tw/blog/6315/obsidian-and-zettelkasten-introduction "2020/06/21") (0則留言, 2020/06/21)
-   [\[Obs＃36\] Kanban：提升待辦事項成為專案管理任務](http://jdev.tw/blog/6653/obsidian-plugin-kanban-project-management "2021/04/26") (0則留言, 2021/04/26)
-   [「予豈好辯哉？」… Argdown用Markdown產生論證圖(Argument Map)─吵架必贏圖形工具](http://jdev.tw/blog/6334/argdown-markdown-to-argument-map "2020/07/03") (0則留言, 2020/07/03)
-   [Obsidian (黑曜石)筆記軟體的基本操作指引](http://jdev.tw/blog/6319/obsidian-users-guide "2020/06/23") (0則留言, 2020/06/23)

標籤: [Markdown](http://jdev.tw/blog/tag/markdown), [obsidian](http://jdev.tw/blog/tag/obsidian)