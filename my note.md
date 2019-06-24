cd到指定路径下：
mkdir <文件夹名>
touch <文件名>

rm -rf <文件夹名>
rm -f <文件名>
rm <文件名>
git rm <文件名>

pwd命令用于显示当前目录。

安装完成后，还需要最后一步设置，在命令行输入：
$ git config --global user.name "Your Name"
$ git config --global user.email "email@example.com"

git init命令把这个目录变成Git可以管理的仓库。

git remote
git remote -v

git add <文件名>
git commit -m "本次提交的说明"

git status命令可以让我们时刻掌握仓库当前的状态，用git diff可以查看修改内容。

git log命令显示从最近到最远的提交日志，可以试试加上--pretty=oneline参数。
直接键盘按q，退出log

git reset --hard HEAD
用HEAD表示当前版本，上一个版本就是HEAD^，上上一个版本就是HEAD^^，或写成HEAD~100。
git reset --hard <cinnut id>


回到过去前，用git log可以查看提交历史，以便确定要回退到哪个版本。
要重返未来，用git reflog查看命令历史，以便确定要回到未来的哪个版本。

git checkout -- readme.txt
把readme.txt文件在工作区的修改全部撤销，这里有两种情况：
一种是readme.txt自修改后还没有被放到暂存区，现在，撤销修改就回到和版本库一模一样的状态；
一种是readme.txt已经添加到暂存区后，又作了修改，现在，撤销修改就回到添加到暂存区后的状态。

场景1：当你改乱了工作区某个文件的内容，想直接丢弃工作区的修改时，用命令git checkout -- file。
场景2：当你不但改乱了工作区某个文件的内容，还添加到了暂存区时，想丢弃修改，分两步，第一步用命令git reset HEAD <file>，就回到了场景1，第二步按场景1操作。
场景3：已经提交了不合适的修改到版本库时，想要撤销本次提交，参考版本回退一节，不过前提是没有推送到远程库。



创建SSH Key：
$ ssh-keygen -t rsa -C "email@example.com"
然后一路回车，使用默认值即可，由于这个Key也不是用于军事目的，所以也无需设置密码。
在用户主目录里找到.ssh目录，里面有id_rsa和id_rsa.pub两个文件，这两个就是SSH Key的秘钥对，id_rsa是私钥，不能泄露出去，id_rsa.pub是公钥，可以放心地告诉任何人。

登陆GitHub，打开“Account settings”，“SSH Keys”页面;
然后，点“Add SSH Key”，填上任意Title，在Key文本框里粘贴id_rsa.pub文件的内容


仓库路径查询查询：
git remote -v
删除指定的远程：
git remote rm origin
已有的本地仓库与远程仓库关联：
$ git remote add origin git@github.com:michaelliao/learngit.git

git push -u origin master
第一次推送master分支时，加上了-u参数，会把本地master分支和远程master分支关联

git clone <远程仓库地址>


git checkout -b <branch name>

git branch <branch name>
git checkout <branch name>

git branch列出所有分支，当前分支前面会标一个*号。

git merge <branch name>用于合并指定分支到当前分支。

git branch -d <branch name>
git branch -D <branch name>

Git用<<<<<<<，=======，>>>>>>>标记出不同分支的内容，便于我们解决冲突。

git log --graph命令可以看到分支合并图
git log --graph --pretty=oneline --abbrev-commit查看分支的合并情况。

git merge --no-ff -m "创建新commit信息" <被合并的分支名>

git stash
git stash list
git stash apply
git stash apply stash@{0}
git stash drop
git stash drop stash@{0}
git stash pop
git stash pop stash@{0}

git pull
建立本地分支和远程分支的关联:
git branch --set-upstream-to <branch-name> origin/<branch-name>
在本地创建和远程分支对应的分支，本地和远程分支的名称最好一致:
git checkout -b branch-name origin/branch-name

git tag
git tag <tag name>
给指定commit打标签：
git tag <tab name> <commit id>
git show <tag name>
git tag -a <tag name> -m "tag说明"
git tag -a <tag name> -m "tag说明" <commit id>


命令git push origin <tagname>可以推送一个本地标签；
命令git push origin --tags可以推送全部未推送过的本地标签；
命令git tag -d <tagname>可以删除一个本地标签；
命令git push origin :refs/tags/<tagname>可以删除一个远程标签。


让Git显示颜色，会让命令输出看起来更醒目：
git config --global color.ui true

