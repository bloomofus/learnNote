# git基础使用

## 新建一个新本地仓库

1. 先创建一个新的文件夹newfolder，再在这个文件夹下面打开git命令行，使用`git init`进行初始化，这个步骤会生成一个`.git`文件夹，这个是git进行版本管理的文件夹，不用管。

   也可以使用`git init newfolder`命令这样可以自动生成一个文件夹。

2. 任何一个文件夹里面有`.git`就是初始化好了之后，就可以使用`pull`命令拉取远程仓库
   如：`git pull origin main`或者`git pull origin emg_classify`，前者是拉取main分支，后者是拉取emg_classify分支，origin为远程仓库别名。

   > **注意**：clone不需要秘钥，但是pull需要ssh秘钥，需要事先配置！而且首次配置和第二次配置步骤不同！！
   >
   > ```bash
   > # 首次密钥的命令
   > ssh-keygen
   > ```
   
3. 使用`clone`命令会克隆一个仓库到本地
   如：`git clone git@github.com:bloomofus/smalTestPOJ.git`或者`git clone git@github.com:bloomofus/smalTestPOJ.git newfolder`，两者区别在于后者会将克隆好的代码放在newfolder文件夹里面。

4. 在别的全新的平台使用git管理你的仓库，建议直接克隆你的远程仓库（这一步不需要你创建一个新的仓库，并且初始化，直接克隆到指定文件夹即可），再pull你需要的branch。

## 基础文件操作、提交命令

1. 查看状态`git status`
2. 将文件加载到缓存区`git add .`或`git add *.txt`等
3. 提交`git commit -m "提交的描述" `或者`git commit`，区别在于后者会自动打开一个vim界面让你输入提交描述
4. 删除`rm test.txt`然后再用`git add test.txt`这两条语句删除工作区和缓存区的test.txt文件。你也可以使用``git rm test.txt`取代这两个语句。
   接着使用`git commit -m “提交描述”`进行确认更改。

## 远程仓库的创建

1. 建立连接：命令`git remote add origin git@github.com:bloomofus/smalTestPOJ.git`，这样就根据我的github远程仓库smalTestPOJ创建了一个连接，远程仓库别名为origin。
   注意仓库结尾时`.git`。
2. 查看建立的连接：`git remote -v`
3. 重命名连接：`git remote rename origin new-origin`
4. 更新远程仓库url：`git remote set-url new-origin https://new.url/for/your/repo.git`

## 分支命令

1. 查看分支`git branch`，分支的存在是为了多种特性并行研发的关键，一般主分支命名为main，子分支随意，子分支里面的独特内容不会被主分支和其他分支看到（**注意 **：空文件夹不被git认可，因此在子分支中存在空文件夹，任何分支都能看到。）
2. 创建分支`git branch newBranch`，创建后使用`git branch`检查，然后使用`git switch newBranch`切换到新创建的分支。
3. 切换分支`git switch emg_classify`，切换到我的emg_classify分支。
4. 分支重命名`git branch -m newName`，必须有`-m`参数。

## pull与push命令

1. **更新代码**：每天开始工作时，先打开初始化的仓库，再进行`pull`操作，获取最新仓库代码。如：`git pull origin main`或者`git pull origin emg_classify`，前者是拉取main分支，后者是拉取emg_classify分支，origin为远程仓库别名。
   当然也可以直接克隆整个仓库，当然这种做法肯定更加费时。
2. 拉取之后，本地仓库所选的分支就已经是最新的了，可以进行本地操作。
3. **确认更新**：本地操作完了之后，需要push到远程仓库，命令`git push -u origin main:main`，`-u`的意思是upstream上游的意思，这个参数不能少。`main:main`第一个main指的是本地仓库的main分支，第二个就是远程仓库的main分支，意思是将本地的main分支覆盖远程仓库的main分支，如果本地所选的分支和远程所选的分支名字一样，那么可以只写一个main，如果远程的分支不存在，git会自动创建分支。

## 进阶命令

1. 打印已经跟踪的文件

   ```shell
   git ls-files	# 这个命令会列出当前 Git 仓库中已跟踪的所有文件。
   git ls-files -t	# 这会显示每个已跟踪文件的状态，包括普通文件、修改过的文件、以及删除的文件等。
   ```

2. 查看文件改变了什么
   由于`git status`只能告诉你哪些文件改变了，要想知道到底改变什么了，需要`git diff`命令
>    `git diff filename`能够查看`filename`改变的历史
> - `diff --git a/<旧文件路径> b/<新文件路径>`：这表示比较的是旧文件和新文件。
> - `index <旧文件哈希>..<新文件哈希> <文件模式>`：这显示了文件变化前后的哈希值和文件模式。
> - `--- a/<旧文件路径>`：这表示旧文件的路径。
> - `+++ b/<新文件路径>`：这表示新文件的路径。
> - `@@ -<旧文件行号>,<旧文件行数> +<新文件行号>,<新文件行数> @@`：这表示变化的范围，旧文件的行号和行数与新文件的行号和行数。

