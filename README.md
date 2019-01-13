# 一个轻量级的仿微信未读消息提示

大家好，我是接触安卓不久的小菜鸟，今天花了一晚上封装了一个类似微信未读消息提示的安卓控件。由于技术问题，所以功能不是很强大，没有动画，但是满足基本需求还是可以的。下面是示例图：

![在这里插入图片描述](https://img-blog.csdnimg.cn/2019010410510099.png)

接下来给大家说一下怎样使用这个未读消息提示。

## 第一步

在你的build.gradle文件下加入 maven {url 'https://jitpack.io'}

```javascript
allprojects {
	repositories {
		google()
		jcenter()
		maven {url "https://jitpack.io"}
	}
}
```

注意：一定是要在allprojects下加入 maven {url 'https://jitpack.io'}，如果在builgsript下加则会构建失败。

## 第二步

在dependencies下加入 implementation 'com.github.EHENJOOM:RedSpot:1.0.2'

```javascript
implementation 'com.github.EHENJOOM:RedSpot:1.0.2'
```

## 第三步

直接在你的xml布局文件里使用RedSpot控件就可以了

~~~xml
<com.ehenjoom.redspot.RedSpot
    android:layout_width="20dp"
    android:layout_height="20dp" />
~~~

一般宽高设置成20dp左右大小比较合适。
当然，你也可以在布局文件里使用我封装好的属性，但是要先加入这句：

~~~xml
xmlns:app="http://schemas.android.com/apk/res-auto"
~~~

接着就可以使用定义好的属性了：

~~~xml
app:textSize="50"
app:textColor="@color/white"
app:backgroundColor="@color/red"
app:text="99+"
~~~

宽高为30dp时，textSize为50比较合适；宽高为20dp时，textSize为25比较合适。
字体颜色默认为白色，背景颜色默认为红色。
你也可以在java代码里设置这些属性:

~~~java
RedSpot redSpot=findViewById(R.id.myRedSpot);
redSpot.setText(12)
       .setTextColor("#000000")   // 白色
       .setTextSize(50)
       .setBackColor("#ff0000");  // 红色
~~~

另外，让这些小红圈消失的方法也很简单:

~~~java
redSpot.setVisibility(View.VISIBLE)    // 可见
redSpot.setVisibility(View.INVISIBLE)  // 不可见
~~~

源码点击[项目地址](https://github.com/EHENJOOM/RedSpot.git)下载即可，可以进行二次封装。

好了，以上就是全部介绍了，有什么错误请大家指正。

后续会更新更加方便好用的版本，敬请期待。
