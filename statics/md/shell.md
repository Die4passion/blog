> 有用的技巧

- `!$`  上一个命令的最后一个字符串

- `sudo !!` 以管理员身份执行上一个命令

- `pstree -p` 显示进程树

- `date -d@时间戳` 时间戳转时间

- `mtr xxxxx.com` 测试网络连接

- `echo "ls -l" | at midnight`  在某个时间运行某个命令

- `ps aux | sort -nk +4 | tail`  列出头十个最耗内存的进程

- `ascii` 查看ascii码表

- **`netstat –tlnp`** 列出本机进程监听的端口号

- **`lsof –i`** 实时查看本机网络服务的活动状态。

- **`python -m SimpleHTTPServer`** 一句话实现http服务

- 使用 nohup 或  disown 如果你要让某个进程运行在后台。

- `awk '{ x += $3 } END { print x }'` 第三列之和 

- `iconv` 文本文件转码

- ```bash
  # 彻底删除 xxxxx  rpm系统
  [root@test ~]# rpm -qa|grep xxxxx|xargs rpm -ev --allmatches --nodeps
  [root@test ~]# whereis xxxxx|xargs rm -frv
  ```

- ```bash
  # pandoc 用来转换文件 支持格式 
  
  
  Input formats:  docbook, haddock, html, json, latex, markdown, markdown_github,
                  markdown_mmd, markdown_phpextra, markdown_strict, mediawiki,
                  native, opml, rst, textile
  Output formats: asciidoc, beamer, context, docbook, docx, dzslides, epub, epub3,
                  fb2, html, html5, json, latex, man, markdown, markdown_github,
                  markdown_mmd, markdown_phpextra, markdown_strict, mediawiki,
                  native, odt, opendocument, opml, org, pdf*, plain, revealjs,
                  rst, rtf, s5, slideous, slidy, texinfo, textile
                  [*for pdf output, use latex or beamer and -o FILENAME.pdf]
  
  
  # 将rst文件转为md 并输出到新建文件 
  pandoc -f 111.rst -o 111.md   
  
  # 将网页转为markdown
  pandoc -s -r html http://www.gnu.org/software/make/ -o example12.text
  
  # 将 LaTeX 文档转换为 mathMathML.html：
  pandoc math.tex -s --mathml  -o mathMathML.html
  
  # 置顶代码高亮主题
  pandoc code.md -s --highlight-style monochrome -o example18c.html
  ```

- 



> bash快捷键

- **`ctrl - w`** 删除最后一个单词

- `Ctrl - U` 删除一行 

- `ctrl - a`  光标移到开头

- `ctrl - e` 光标移到结尾

- `alt - f` 向后移动一个单词

- `alt - b` 向前移动一个单词

- `alt - u/l` 大小写转换

- `ctrl - -` 撤消

> 语法

```bash
# 将前面make的stderr(2)合并到stdout(1)   tee命令写入到build.log
$ make –f build_example.mk 2>&1 | tee build.log

# tr -d(删除) -s(替换)
# 将windows文件换行转为linux格式
$ tr -d '\r' < dosfile.txt > unixfile.txt
# 也可用sed
$ sed -i 's/\r//' filename1 filename2 filename3 ...
$ cat dosfile.txt | sed 's/^M//' > unixfile.txt
$ sed -i 's/^M//' filename1 filename2 filename3 ...
```
