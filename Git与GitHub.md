### Git常用命令

> git的复制粘贴 快捷键分別是 ctrl+ins  shift+ins

#### 1.设置用户签名

```
git config --global user.name wdp
git config --global user.email 2047808789@qq.com
```

> 说明：
>
> 签名的作用是区分不同操作者身份。用户的签名信息在每一个版本的提交信息中可以看到，以此确定本次提交是谁做的。<font color="red">git首次安装必须设置一下用户签名，否则无法提交代码</font>

#### 2.初始化本地库

##### 2.1	``git init``

- 会在要操作的文件夹下自动新建一个.git文件夹的隐藏文件

> 查看文件目录和详情：``ll``
>
> 查看隐藏文件目录和详情：``ll -a

#### 3.查看本地库状态

``git status``

##### 3.1查看状态（首次查看，工作区没有任何文件）

<img src="C:\Users\DuMer\AppData\Roaming\Typora\typora-user-images\image-20220915093933715.png" alt="image-20220915093933715" style="zoom:80%;" />

> On branch master：当前所在分支是master
>
> No commits yet：未提交过任何文件
>
> nothing to commit：没有可以提交的文件

##### 3.2新增文件（vim 文件名）

`vim hello.txt`

![image-20220915094143882](C:\Users\DuMer\AppData\Roaming\Typora\typora-user-images\image-20220915094143882.png)

> 新建hello.txt后，进入文件编写页
>
> 按下a：表示开始编写内容，yy表复制，p表粘贴
>
> 按下Esc：切换模式
>
> 输入:q ：不保存文件直接退出
>
> 输入:wq ：保存文件并退出
>
> 输入:wq! ：保存文件并强制退出
>
> 按下Esc切换模式，将光标定在要复制的区域，按下yy，则可复制该行；按下a键切换输入模式，将光标定在需要粘贴的位置，按下Esc切换模式，输入p，则复制的文本就会被粘贴

##### 3.3 查看文件（cat 文件名）

``cat hello.txt``

##### 3.4查看文件末尾第一行（tail -n l 文件名）

`tail -n l hello.txt`

##### 3.5工作区有文件时查看状态

<img src="C:\Users\DuMer\AppData\Roaming\Typora\typora-user-images\image-20220915101243014.png" alt="image-20220915101243014" style="zoom:80%;" />

> Untracked files：未被追踪的文件
>
> hello.txt标红表示该文件虽然已经存在，但是只是存在工作区，git还没有追踪该文件

#### 4.添加暂存区

- ##### 将文件添加到暂存区（git add 文件名）

<img src="C:\Users\DuMer\AppData\Roaming\Typora\typora-user-images\image-20220915101746236.png" alt="image-20220915101746236" style="zoom:80%;" />

- ##### 添加暂存区后查看本地库状态

  <img src="C:\Users\DuMer\AppData\Roaming\Typora\typora-user-images\image-20220915101933905.png" alt="image-20220915101933905" style="zoom:80%;" />

  > 添加暂存区后，hello.txt不在标红，即已提交至暂存区

- ##### 删除暂存区文件（`git rm --cached 文件名`）

  <img src="C:\Users\DuMer\AppData\Roaming\Typora\typora-user-images\image-20220915102241753.png" alt="image-20220915102241753" style="zoom:80%;" />

  > 删除了暂存区的文件，但是工作区的文件仍然存在，所以hello.txt继续显示未被追踪

#### 5.提交本地库

将暂存区的文件交到本地库（==可形成历史版本==）

基本语法：

`git commit-m "日志信息" 文件名`

<img src="C:\Users\DuMer\AppData\Roaming\Typora\typora-user-images\image-20220915103025804.png" alt="image-20220915103025804" style="zoom:80%;" />

- ##### 提交至本地库后，查看本地库信息

  <img src="C:\Users\DuMer\AppData\Roaming\Typora\typora-user-images\image-20220915103213221.png" alt="image-20220915103213221" style="zoom:80%;" />

  > nothing to commit,working tree clean：已提交，并且该文件既没有新增也没有修改，工作树是干净的，没有东西需要提交

- ##### 查看版本信息（`git reflog `/` git log`）

  ​						<img src="C:\Users\DuMer\AppData\Roaming\Typora\typora-user-images\image-20220915103913991.png" alt="image-20220915103913991" style="zoom:80%;" />

  > ceac7fd:版本号
  >
  > HEAD -> master：指针指向master分支
  >
  > my first commit：日志信息

- ##### git log ：查看详细日志

<img src="C:\Users\DuMer\AppData\Roaming\Typora\typora-user-images\image-20220915104405233.png" alt="image-20220915104405233" style="zoom:80%;" />

#### 6.修改文件

- 当修改了一个提交至本地库的文件，且修改后没有添加至暂存区

   <img src="C:\Users\DuMer\AppData\Roaming\Typora\typora-user-images\image-20220915105037115.png" alt="image-20220915105037115" style="zoom:80%;" />

  提示：hello.txt被修改，且没有添加至暂存区

  > 修改后的文件可重新上传至本地库

- 修改后的文件提交至本地库后，查看版本

  <img src="C:\Users\DuMer\AppData\Roaming\Typora\typora-user-images\image-20220915105535018.png" alt="image-20220915105535018" style="zoom:80%;" />

  > 显示有两个版本，指针指向新提交的版本，那么便可以查看这个新版本的文件

#### 7.历史版本

##### 7.1查看历史版本

- ##### 基本语法

  - git reflog 	查看版本信息
  - git log     查看版本详细信息

#### 7.2版本穿梭

<img src="C:\Users\DuMer\AppData\Roaming\Typora\typora-user-images\image-20220915112438346.png" alt="image-20220915112438346" style="zoom:80%;" />

由图可知：已经提交三个版本的文件，且指针指向第三个版本

**要求**：将指针从第三个版本的文件切换到第二个版本的文件

- 复制要回退的版本的版本号
- 输入`git reset --hard  版本号`

<img src="C:\Users\DuMer\AppData\Roaming\Typora\typora-user-images\image-20220915113925307.png" alt="image-20220915113925307" style="zoom:80%;" />

如图：指针指向了第二个版本，此时就可以通过`vim 文件名`查看并修改这个版本的文件内容



### Git分支操作

#### 1.什么是分支

在版本控制过程中，同时推进多个任务，为每个任务，我们可以创建每个任务的单独分支。使用分支意味着程序员可以把自己的工作从主线上分离开，开发自己的分支的时候，不会影响主线分支的运行。（分支的底层其实就是指针的引用）

#### 2.分支好处

同时并行推进多个功能开发，提高开发效率

各个分支在开发过程中，如果某一个分支开发失败，不会对其他分支有任何影响。失败的分支删除重新开始即可

#### 3.分支的操作

- `git branch 分支名`：创建分支
- `git branch -v`：查看分支
- `git checkout 分支名`：切换分支
- `git merge 分支名`：把指定的分支合并到当前分支

##### 创建分支：

<img src="C:\Users\DuMer\AppData\Roaming\Typora\typora-user-images\image-20220915133822920.png" alt="image-20220915133822920" style="zoom:80%;" />

##### 查看分支：

​											<img src="C:\Users\DuMer\AppData\Roaming\Typora\typora-user-images\image-20220915133902723.png" alt="image-20220915133902723" style="zoom:80%;" />

> 由第一行末尾可知，当前所在的分支是<font color="skyblue">master</font>

##### 切换分支:

<img src="C:\Users\DuMer\AppData\Roaming\Typora\typora-user-images\image-20220915134350906.png" alt="image-20220915134350906" style="zoom:80%;" />

> 如图，当前分支被切换到了<font color="skyblue">hot-fix</font>分支

==切换分支后，即可在该分支下对文件进行修改，修改后的文件处于工作区，仍然需要添加至暂存区，并提交；此时git文件夹内的head指针指向的是hot-fix分支==

提交之后，查看版本信息

<img src="C:\Users\DuMer\AppData\Roaming\Typora\typora-user-images\image-20220915135355053.png" alt="image-20220915135355053" style="zoom:80%;" />

##### 合并分支（正常合并）：

切换目前所在的分支为master，输入`git merge hot-fix`

> 首先比如要将b分支合并到a分支，则需要切换当前分支为a，再进行命令行操作，将b分支合并到当前的a分支

##### 合并分支（冲突合并）：

冲突产生的原因：

​		合并分支时，两个分支在<font color="red">同一个文件的同一个位置</font>有两套完全不同的修改。Git无法帮我们决定使用哪一个。必须<font color="red">人为决定</font>新代码内容。

**演示：**

1.我们在master分支中修改hello.txt文件如图，并添加暂存区，提交本地库：

<img src="C:\Users\DuMer\AppData\Roaming\Typora\typora-user-images\image-20220915143408772.png" alt="image-20220915143408772" style="zoom:80%;" />

2.在hot-fix分支中修改hello.txt文件如下图，并添加暂存区，提交本地库：

<img src="C:\Users\DuMer\AppData\Roaming\Typora\typora-user-images\image-20220915143551048.png" alt="image-20220915143551048" style="zoom:80%;" />

3.回到master分支，将hot-fix分支合并到master分支中

<img src="C:\Users\DuMer\AppData\Roaming\Typora\typora-user-images\image-20220915143712775.png" alt="image-20220915143712775" style="zoom:80%;" />![image-20220915143937533](C:\Users\DuMer\AppData\Roaming\Typora\typora-user-images\image-20220915143937533.png)

![image-20220915143937533](C:\Users\DuMer\AppData\Roaming\Typora\typora-user-images\image-20220915143937533.png)

> 如图显示出现错误，正是因为在两个分支中修改同一文件内的内容，使得git无法决定使用哪个分支的内容，这时就要开发者手动合并

**手动合并代码**

- 打开文件

  <img src="C:\Users\DuMer\AppData\Roaming\Typora\typora-user-images\image-20220915144143578.png" alt="image-20220915144143578" style="zoom:80%;" />

- 删除多余的内容和特殊符号，得到我们想要的内容

  <img src="C:\Users\DuMer\AppData\Roaming\Typora\typora-user-images\image-20220915144720834.png" alt="image-20220915144720834" style="zoom:80%;" />

- 把手动修改的文件添加到暂存区，提交到本地库

  > <font color="red">注意：此时使用git commit命令时不能带文件名</font>
  >
  > 正确写法：<img src="C:\Users\DuMer\AppData\Roaming\Typora\typora-user-images\image-20220915145147180.png" alt="image-20220915145147180" style="zoom:80%;" />

> 创建分支的本质就是多创建一个指针



### 团队协作机制

- #### 团队内协作

<img src="C:\Users\DuMer\AppData\Roaming\Typora\typora-user-images\image-20220915150228038.png" alt="image-20220915150228038" style="zoom: 50%;" />

- #### 跨团队协作

<img src="C:\Users\DuMer\AppData\Roaming\Typora\typora-user-images\image-20220915150719219.png" alt="image-20220915150719219" style="zoom: 50%;" />



### GitHub操作

#### 创建远程仓库

- 点击右上角 New repository

  <img src="C:\Users\DuMer\AppData\Roaming\Typora\typora-user-images\image-20220915151203182.png" alt="image-20220915151203182" style="zoom: 80%;" />

- 创建之后显示

<img src="C:\Users\DuMer\AppData\Roaming\Typora\typora-user-images\image-20220915152400515.png" alt="image-20220915152400515" style="zoom:50%;" />

> ​	选中区域是远程库的两种链接

#### 远程仓库操作

<img src="C:\Users\DuMer\AppData\Roaming\Typora\typora-user-images\image-20220915153207971.png" alt="image-20220915153207971" style="zoom: 80%;" />

- **创建远程仓库别名**

  `git remote -v`	查看当前所有远程地址的别名

  `git remote add 别名 远程地址`	

  <img src="C:\Users\DuMer\AppData\Roaming\Typora\typora-user-images\image-20220915225816259.png" alt="image-20220915225816259" style="zoom:80%;" />

- **推送本地库到远程库**

  **基本语法：**

  `git push 别名 分支`

  <img src="C:\Users\DuMer\AppData\Roaming\Typora\typora-user-images\image-20220915231711543.png" alt="image-20220915231711543" style="zoom:80%;" />

   推送成功后显示如下命令：

  <img src="C:\Users\DuMer\AppData\Roaming\Typora\typora-user-images\image-20220915231747929.png" alt="image-20220915231747929" style="zoom:80%;" />

  浏览器的github内显示本地库的分支成功登录到远程仓库中：

  <img src="C:\Users\DuMer\AppData\Roaming\Typora\typora-user-images\image-20220915231914048.png" alt="image-20220915231914048" style="zoom:80%;" />

- **拉取远程库到本地库**

  语法：

  `git pull 远程库地址别名 远程库分支名`

  <img src="C:\Users\DuMer\AppData\Roaming\Typora\typora-user-images\image-20220915233720799.png" alt="image-20220915233720799" style="zoom:80%;" />

  如图：显示拉取成功；如果远程库中的代码被手动修改了，这时本地库的代码和远程库的代码会同步

  > 如果ssl失败，先加：$ git config --global http.sslVerify "false"

  > 拉取的分支代码会自动提交到本地库

- **克隆远程仓库到本地库**

  语法：

  `git clone 远程地址`

  > 小结：
  >
  > clone会做如下操作：1.拉取代码	2.初始化本地仓库	3.创建别名
  >
  > ![image-20220916112447428](C:\Users\DuMer\AppData\Roaming\Typora\typora-user-images\image-20220916112447428.png)
  >
  > 公共库克隆代码时不需要登录帐号
  >
  > <font color="red">对于一个人使用多个github帐号对同一台电脑中进行克隆操作时，因为windows一次只能记住一个帐号，所以要在 控制面板\用户帐户\凭据管理器 中删除上一个用户的普通凭据才可以下一个帐号使用</font>

#### 团队内协作

- **邀请加入团队**

  **选择邀请合作者**

  假设有三个程序员（岳不群、令狐冲、东方）

  ==在令狐冲后端：令狐冲从岳不群远程仓库中拉取了代码，并进行了修改；那么就要添加暂存区，提交本地库；之后要将代码推送到远程库中，但是此时令狐冲还没有权限推送，因为要先加入岳不群的团队。==

  **获得推送权限操作（加入团队）：**

  - 在岳不群的github中，进入该git-demo远程仓库，点击设置

    ![image-20220916091020596](C:\Users\DuMer\AppData\Roaming\Typora\typora-user-images\image-20220916091020596.png)

  

  - 进入设置后点击Collaborators，再点击添加成员

    ![image-20220916091508714](C:\Users\DuMer\AppData\Roaming\Typora\typora-user-images\image-20220916091508714.png)

  - 找到要邀请的对象，发送邀请

    ![image-20220916091815512](C:\Users\DuMer\AppData\Roaming\Typora\typora-user-images\image-20220916091815512.png)

  - 点击pending invite会自动复制一个邀请函链接地址，岳不群只需将该链接地址发给令狐冲，令狐冲在自己的github中收到邀请函后只需通过邀请即可加入团队

  <img src="C:\Users\DuMer\AppData\Roaming\Typora\typora-user-images\image-20220916092605054.png" alt="image-20220916092605054" style="zoom:80%;" />

  > 令狐冲一旦加入岳不群的团队后，即可在自己的github中看到岳不群的git-demo；而也可以将代码推送到远程库了，如图：即推送成功
  >
  > ![image-20220916114007450](C:\Users\DuMer\AppData\Roaming\Typora\typora-user-images\image-20220916114007450.png)

​				此时，在岳不群的远程库中就可以看到令狐冲提交的代码了

#### 跨团队协作

假如东方不败是团队外的人员，想要参与岳不群项目的编写，需要将岳不群团队的项目fork（插入）到自己的帐号中

- 东方不败点击右上角的fork

  ![](C:\Users\DuMer\AppData\Roaming\Typora\typora-user-images\image-20220916120113424.png)

  > 东方不败fork到自己帐号的项目也可以进行克隆，或者在自己的远程仓库中修改代码，但是只有在他自己的远程库中才可以看到修改的内容，而岳不群看不到；这时东方不败就需要点击Pull request ，告诉岳不群，他已经发送对岳不群拉取的请求

- 东方不败发送 pull request

  <img src="C:\Users\DuMer\AppData\Roaming\Typora\typora-user-images\image-20220916121125090.png" alt="image-20220916121125090" style="zoom:50%;" />

​						<img src="C:\Users\DuMer\AppData\Roaming\Typora\typora-user-images\image-20220916121257382.png" alt="image-20220916121257382" style="zoom:50%;" />

​								<img src="C:\Users\DuMer\AppData\Roaming\Typora\typora-user-images\image-20220916121411421.png" alt="image-20220916121411421" style="zoom: 50%;" />

- 此时岳不群的帐号就可以收到拉取请求

  <img src="C:\Users\DuMer\AppData\Roaming\Typora\typora-user-images\image-20220916121649433.png" alt="image-20220916121649433" style="zoom: 50%;" />

  > 岳不群觉得代码可行后，则可以将东方不败的代码并到自己的仓库中

- 同意拉取请求，合并团队外人员的代码到自己的本地库

  <img src="C:\Users\DuMer\AppData\Roaming\Typora\typora-user-images\image-20220916122105056.png" alt="image-20220916122105056" style="zoom: 50%;" />

#### SSH免密登录

github中还有一个SSH的链接地址，因此我们也可以使用SSH进行访问

<img src="C:\Users\DuMer\AppData\Roaming\Typora\typora-user-images\image-20220916122551664.png" alt="image-20220916122551664" style="zoom: 67%;" />

但是此时要添加SSH免密的公钥

- 打开本地电脑找到C:\Users\DuMer\.ssh，将.ssh文件夹之前的内容删除，并删除.ssh文件夹

- 在改目录中右键打开git命令行窗口，在这里面可以重新生成SSH文件

  - 输入`ssh-keygen -t rsa -C 2047808789@qq.com`

  - 点击三次回车，这时在本地文件夹原先目录中重新生成了一个.ssh文件

    <img src="C:\Users\DuMer\AppData\Roaming\Typora\typora-user-images\image-20220916123803203.png" alt="image-20220916123803203" style="zoom: 80%;" />

  - 其中.ssh文件夹内有两个文件，公钥和私钥，并且复制公钥内的全部内容

    <img src="C:\Users\DuMer\AppData\Roaming\Typora\typora-user-images\image-20220916123944260.png" alt="image-20220916123944260" style="zoom:80%;" />

  - 打开github右上角内的Settings-->SSH and GPGS keys --> new SSH key	

    <img src="C:\Users\DuMer\AppData\Roaming\Typora\typora-user-images\image-20220916143642886.png" alt="image-20220916143642886" style="zoom:80%;" />

  - ​		将复制的公钥内容粘贴到新建的SSH内

- 这时，我们也可以通过输入`git pull SSH地址 分支名`拉取代码

  <img src="C:\Users\DuMer\AppData\Roaming\Typora\typora-user-images\image-20220916143844886.png" alt="image-20220916143844886" style="zoom:80%;" />

> ​	如果报了fatal: not a git repository (or any of the parent directories): .git错误
>
> 可输入一下 `git init`后重新拉取 ，之后也可以看到拉取的代码

- 同样拉取后的代码也可以进行修改，然后再添加暂存区，提交本地库，并且推送远程库
