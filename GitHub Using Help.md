## GitHub/Git Using Help

---

1. 上传文件

   1. 在文件夹中打开Git Bash或者通过```cd ```进入目标目录（路径中的空格用```\```转义）

   2. 初始化文件夹，下面的指令会在文件夹中添加一个隐藏文件.git
      ```$ git init```

   3. 上传文件到缓存区（add）
      ```$ git add .//上传当前目录的所有文件```

   4. 提交注释（commit）

      ```$ git commit -m "注释内容"```

   5. 关联远程仓库（remote）
      ```$ git remote add origin http://XXX.XXX//后两个部分分别是命名的该临时的仓库名字，以及要上传的GitHub仓库的HTTP```

   6. 上传代码（push）
      
      ```$ git push <远程主机名> <本地分支名>:<远程分支名>```
      ```$ git push -u origin master:main//后面两个部分分别是远程仓库名，以及本地分支```
      
   7. 更新本地仓库（pull）
      
      ```$ git pull <远程主机名> <远程分支名>:<本地分支名>```
      
      一般使用fetch，较pull可以使用diff对比与该本地分支的不同：
      ```$ git remote -v//用于查看远程仓库的状态```
      ```$ git fetch origin main(远程仓库中的分支):temp //temp为新创建和命名的分支```
      ```$ git diff temp//比较temp分支与该分支的不同```
      ```$ git merge temp//将temp合并到当前分支上```
      ```$ git branch -d temp//用于删除临时分支```
      
   8. **Problem**
   
      1. GitHub error: "There isn’t anything to compare entirely different commit histories".
   
         1. 原因：如提示所说合并（merge）需要两个分支具有相同的histories，如果不是clone下来的文件，第一次上传自然没有与仓库分支共同的节点。
   
         2. 解决方法：
   
            ```bash
            $ git commit -m "message"
            $ git pull origin main(or whatever branch) --allow-unrelated-histories
            $ git push origin main
            ```
   
            From: [Link to GitHub issue](https://github.com/nss-evening-cohort-13/student-help/issues/76)
   
            通过上述第二行指令允许远程仓库与没有共同节点的分支合并（将打开一个Vim）
            
            退出vim的方式：先按Esc，然后直接输入“ : ”就会在最下面显示出一行，vim开始进入命令模式（而不是write模式）
            
            ```bash
            :q  
            //退出
            
            :q! 
            //退出且不保存（:quit!的缩写）
            
            :wq
            //保存并退出
            
            :wq!
            //保存并退出即使文件没有写入权限（强制保存退出）
            
            :x
            //保存并退出（类似:wq，但是只有在有更改的情况下才保存）
            
            :exit
            //保存并退出（和:x相同）
            
            :qa
            //退出所有(:quitall的缩写)
            
            :cq
            //退出且不保存（即便有错误）
            ```
            
   
      2. 同步更改时```OpenSSL SSL_connect: SSL_ERROR_SYSCALL in connection to github.com:443 ```
   
         1. 原因：
            网络代理导致的问题
         2. 解决方法：
            在终端输入：```git config --global --unset http.proxy```

