# C++代码无法正常渲染的问题
我一开始想是不是主题的问题，但换了主题还是无法正常渲染。
在新版编辑器，源码和预览模式是能正常显示代码高亮的，但是在阅读里面无法正常显示。
后来在群里大佬的帮助下解决了。
原来是 ob 本身的问题，代码标记不能用 `C++` 而是用 `cpp`。
感谢两位大佬：咖啡豆和蚕子。

下面附上咖啡豆大佬找到的：如果遇到渲染无法显示可以查找此列表
```
这些是支持的语言列表，和正确的写法：

markup+css+clike+javascript+abap+abnf+actionscript+ada+agda+al+antlr4+apacheconf+apex+apl+applescript+aql+arduino+arff+asciidoc+aspnet+asm6502+asmatmel+autohotkey+autoit+avisynth+avro-idl+bash+basic+batch+bbcode+bicep+birb+bison+bnf+brainfuck+brightscript+bro+bsl+c+csharp+cpp+cfscript+chaiscript+cil+clojure+cmake+cobol+coffeescript+concurnas+csp+coq+crystal+css-extras+csv+cypher+d+dart+dataweave+dax+dhall+diff+django+dns-zone-file+docker+dot+ebnf+editorconfig+eiffel+ejs+elixir+elm+etlua+erb+erlang+excel-formula+fsharp+factor+false+firestore-security-rules+flow+fortran+ftl+gml+gap+gcode+gdscript+gedcom+gherkin+git+glsl+gn+go+graphql+groovy+haml+handlebars+haskell+haxe+hcl+hlsl+hoon+http+hpkp+hsts+ichigojam+icon+icu-message-format+idris+ignore+inform7+ini+io+j+java+javadoc+javadoclike+javastacktrace+jexl+jolie+jq+jsdoc+js-extras+json+json5+jsonp+jsstacktrace+js-templates+julia+keepalived+keyman+kotlin+kumir+kusto+latex+latte+less+lilypond+liquid+lisp+livescript+llvm+log+lolcode+lua+magma+makefile+markdown+markup-templating+matlab+maxscript+mel+mermaid+mizar+mongodb+monkey+moonscript+n1ql+n4js+nand2tetris-hdl+naniscript+nasm+neon+nevod+nginx+nim+nix+nsis+objectivec+ocaml+opencl+openqasm+oz+parigp+parser+pascal+pascaligo+psl+pcaxis+peoplecode+perl+php+phpdoc+php-extras+plsql+powerquery+powershell+processing+prolog+promql+properties+protobuf+pug+puppet+pure+purebasic+purescript+python+qsharp+q+qml+qore+r+racket+cshtml+jsx+tsx+reason+regex+rego+renpy+rest+rip+roboconf+robotframework+ruby+rust+sas+sass+scss+scala+scheme+shell-session+smali+smalltalk+smarty+sml+solidity+solution-file+soy+sparql+splunk-spl+sqf+sql+squirrel+stan+iecst+stylus+swift+systemd+t4-templating+t4-cs+t4-vb+tap+tcl+tt2+textile+toml+tremor+turtle+twig+typescript+typoscript+unrealscript+uri+v+vala+vbnet+velocity+verilog+vhdl+vim+visual-basic+warpscript+wasm+web-idl+wiki+wolfram+wren+xeora+xml-doc+xojo+xquery+yaml+yang+zig */

```
# Obsidian
。


# 插件：
## 插件问题描述：
![](https://growlr-center-blog-image.oss-cn-beijing.aliyuncs.com/image/20220516135912.png)


这个插件会导致 markdown 无法正常渲染：
![](https://growlr-center-blog-image.oss-cn-beijing.aliyuncs.com/image/20220516140045.png)

![](https://growlr-center-blog-image.oss-cn-beijing.aliyuncs.com/image/20220516140015.png)

在预览模式下无法正常渲染。
原因是在文档中存在 `html` 代码。
去掉 `HTML` 代码之后预览模式恢复正常。
联系代码高亮插件
## Wenti

![](https://growlr-center-blog-image.oss-cn-beijing.aliyuncs.com/image/20220517210751.png)
可以开启行模式
![](https://growlr-center-blog-image.oss-cn-beijing.aliyuncs.com/image/20220517185508.png)

该选项将会导致输入代码时，行首字母大写。
![](https://growlr-center-blog-image.oss-cn-beijing.aliyuncs.com/image/20220517210235.png)

注意要把这个关闭，不然会出问题，在中文打字的情况下，会出现问题。
