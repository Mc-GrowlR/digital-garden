---
title: 
created: 2022-09-05 12:39
uid: 202209051239
aliases: []
tags: [nvim]
from: 
editflag: 1
---

# 参考

相关插件的安装和配置都从 `TheCW` 的这个视频
[让你写代码快如飞！「Vim + Snippets」使用代码片段提高编程效率_哔哩哔哩_bilibili](https://www.bilibili.com/video/BV1XE411b7Du?spm_id_from=333.999.0.0&vd_source=8e43b8da5e07eef6f57edcd950d3b1d3)
学来的。

还有这篇文档介绍的也十分详细
[Site Unreachable](https://blog.csdn.net/keeliizhou/article/details/82260498)

# 安装插件
``` vim
Plug 'honza/vim-snippets'
Plug 'SirVer/ultisnips'
```


## 插件配置

将下列配置粘贴到`init.vim`中
``` vim
"6.=== 配置 snippts Begin
" se <C-l> for trigger snippet expand.
imap <C-l> <Plug>(coc-snippets-expand)

" Use <C-j> for select text for visual placeholder of snippet.
vmap <C-j> <Plug>(coc-snippets-select)

" Use <C-j> for jump to next placeholder, it's default of coc.nvim
let g:coc_snippet_next = '<c-j>'

" Use <C-k> for jump to previous placeholder, it's default of coc.nvim
let g:coc_snippet_prev = '<c-k>'

" Use <C-j> for both expand and jump (make expand higher priority.)
imap <C-j> <Plug>(coc-snippets-expand-jump)

" Use <leader>x for convert visual selected code to snippet
xmap <leader>x  <Plug>(coc-convert-snippet)U
"
inoremap <silent><expr> <C-e>
      \ coc#pum#visible() ? coc#_select_confirm() :
      \ coc#expandableOrJumpable() ? "\<C-r>=coc#rpc#request('doKeymap', ['snippets-expand-jump',''])\<CR>" :
      \ CheckBackSpace() ? "\<c-e>" :
      \ coc#refresh()

function! CheckBackSpace() abort
  let col = col('.') - 1
  return !col || getline('.')[col - 1]  =~# '\s'
endfunction

let g:coc_snippet_next = '<c-e>'

"6.=== 配置 snippts End
"
"7.=== 配置 ultinsnips Begin``
" Trigger configuration. You need to change this to something other than <tab>
" if you use one of the following:
" " - https://github.com/Valloric/YouCompleteMe
" " - https://github.com/nvim-lua/completion-nvim
" 快捷跳转下一个位置快捷键
let g:UltiSnipsExpandTrigger="<c-e>"
let g:UltiSnipsJumpForwardTrigger="<c-b>"
let g:UltiSnipsJumpBackwardTrigger="<c-z>"
" If you want :UltiSnipsEdit to split your window.
" 自定义代码片段配置
let g:UltiSnipsEditSplit="vertical"
"7.=== 配置 ultinsnips End
```

## 配置说明

更改此处双引号内的内容，改变跳转的快捷键
```
let g:UltiSnipsExpandTrigger="<c-e>"
```

# 创建自己的代码片段

用 `nvim` 打开你要使用代码片的代码文档，比如说想要在写 C++代码时使用特定的代码片段。

用 `nvim` 打开文件后缀为 `cpp` 的文档。

在 `nvim` 中输入下列命令：

``` 
:UltiSnipsEdit
```
（可以按 TAB 键补全）
 
按下回车就进入了对应的代码片段文档：

![](https://growlr-center-blog-image.oss-cn-beijing.aliyuncs.com/image/20220905130148.png)

如果文档非空，按下 `G` 跳转到文档末尾。

## Snippets 格式

```
snippet 触发字符 ["代码片段说明" [参数]]
代码片段内容
endsnippet
```
### Snippets 实例

```
snippet struct "结构体"
struct ${1:strcutName}
{
    ${2:structIn}
};
${0}
endsnippet 
```

#### 说明
1. `struct` 为触发字符。
2. `${1}` 为触发点，当代码片段内添加到文档内的时候光标所处的位置
   -  `${1}` 表示光标的第一个位置，以此类推 `${2}` 即为第二个位置
   - `${0}` 特殊占位符，表示光标跳转的最后一个位置。
3. `${1:strcutName}` 为触发点添加文字说明，strcutName为占位符。当代码片段内添加到文档中后，在文档中就会显示占位符的内容


这时，当在 cpp 文档中输入 `struct`，按下 `TAB` 选择补全内容再按回车，即可快速输入代码片段内容。
选择补全内容：
![](https://growlr-center-blog-image.oss-cn-beijing.aliyuncs.com/image/20220905130828.png)
效果：
![](https://growlr-center-blog-image.oss-cn-beijing.aliyuncs.com/image/20220905130849.png)
此时，可对选中内容做更改。
按下`<ctrl>+e`皆可切换到下一个占位符的位置。