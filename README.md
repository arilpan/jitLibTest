# 手把手教程，一次成功！
- step1:
新建一个github仓库，https://github.com/new，输入Repository name、Description (optional)、Public,不用选择忽略文件和开源协议。
开源协议建议自己修改一份，然后慢慢改，最后Creating repository.

- step2:
android studio 建立新项目，成功后，新建Library（Module选择library）,Application的build.gradle文件加入：
<code>
dependencies {<br>
classpath 'com.android.tools.build:gradle:2.2.2'<br>
classpath 'com.github.dcendents:android-maven-gradle-plugin:1.5' //加入这行代码<br>
}<br>
allprojects {<br>
repositories {<br>
jcenter()<br>
maven { url "https://jitpack.io" }//加入这行代码<br>
}<br>
}<br>
</code>
Library的build.gradle文件加入：
<code>
apply plugin: 'com.android.library'<br>
apply plugin: 'com.github.dcendents.android-maven'//加入这行代码<br>
group='com.github.arilpan'//加入这行代码,arilpan是本人的github账号<br>
</code>
- step3:
将整体项目上传到github，注意不是lib项目，而是Application包含app、lib的整个项目。
使用如下命令：
<pre>
git init<br>
git add .<br>
git commit -m "init commit"<br>
git remote add origin https://github.com/arilpan/testJitPack.git<br>
git push -u origin master<br>
实例：https://github.com/arilpan/jitLibTest<br>
</pre>
发布该项目，项目链接后面加入/releases访问发布路径，如项目https://github.com/arilpan/jitLibTest 对应的release路径为：https://github.com/arilpan/jitLibTest/releases 。
点击“draft a new release”，输入Tag Version（版本号），如V1.0，title和write（标题和描述）任意，点击publish Release发布新版本。

- step4:
打开https://jitpack.io/ ，在页面唯一输入框输入你的项目在github上面的路径如：arilpan/jitLibTest，点击Lookup,然后可以看到你发布的开源库。
如：
arilpan / jitLibTest
Version Log Status
V1.0 Get it
选择你需要的版本，点击get it，即可以获得依赖库链接，鼠标下拉页面，可以看到依赖库使用方式：
<pre>
allprojects
{
repositories
{
...
maven { url "https://jitpack.io" }
}
}
dependencies
{
compile 'com.github.arilpan:jitLibTest:V1.0'
}
</pre>
其他人需要使用你的库时，只需要在仓库地址中加入jitpack的地址，然后在项目中添加库依赖即可。

截图： http://blog.ydxiaoyuan.com/wordpress/wp-content/uploads/2016/11/2.png