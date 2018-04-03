# Android基础

<details>
<summary>目录</summary>  

## 内容目录  

- [1.了解Fragment么,说说Fragmment的生命周期](#1.了解Fragment么,说说Fragmment的生命周期)
- [2.安卓的事件分发机制](#2.安卓的事件分发机制)

</details>  

## 知识点

### 1.了解Fragment么,说说Fragmment的生命周期  
<details>
<summary>展开查看答案</summary>  

一张图概括,详细请看博客链接[Fragment生命周期](http://pvphero.github.io/2018/03/13/20180313AndroidInterViewFragment/)  
![图片](https://dn-coding-net-production-pp.qbox.me/de6215bc-2e4d-43db-bc39-45526fe33a01.png)  
</details>  

### 2.安卓的事件分发机制  
<details>
<summary>展开查看答案</summary>  

   - Android事件的基础知识：  
   所有的Touch事件都封装到MotionEvent里面
   事件处理包括三种情况，分别为：`传递—-dispatchTouchEvent()函数`、`拦截—-
   onInterceptTouchEvent()函数`、`消费—-onTouchEvent()函数`和`OnTouchListener`  
   事件类型分为`ACTION_DOWN`, `ACTION_UP`, `ACTION_MOVE`, `ACTION_POINTER_DOWN`,
   `ACTION_POINTER_UP`, `ACTION_CANCEL`等  
   每个事件都是以`ACTION_DOWN`开始`ACTION_UP`结束 
   
   - Android事件传递流程：
     1. 事件都是从`Activity.dispatchTouchEvent()`开始传递  
     2. 事件由父View传递给子View，ViewGroup可以通过`onInterceptTouchEvent()`方法对事件拦截，
     停止其向子view传递  
     3. 如果事件从上往下传递过程中一直没有被停止，且最底层子View没有消费事件，**事件会反向往上传递
     **,这时父View(ViewGroup)可以进行消费，如果还是没有被消费的话，最后会
     `Activityon.TouchEvent()`函数。  
     4. 如果View没有对ACTION_DOWN进行消费，之后的其他事件不会传递过来，也就是说ACTION_DOWN必须
     返回true，之后的事件才会传递进来OnTouchListener优先于onTouchEvent()对事件进行消费
     
    - 三张效果图辅助理解  
    **View不处理事件流程图（View没有消费事件)**
    ![](https://ws4.sinaimg.cn/large/006tKfTcly1fpzlduduzzj31ga0y8jxd.jpg)
    
    **View处理事件**  
    ![](https://ws3.sinaimg.cn/large/006tKfTcly1fpzlek9w6cj31gs0xygrl.jpg)
    
    **事件拦截**  
    ![](https://ws1.sinaimg.cn/large/006tKfTcly1fpzlexpyxjj31ge0xkn31.jpg)
    
    > [Android-三张图搞定Touch事件传递机制](http://hanhailong.com/2015/09/24/Android-三张图搞定Touch事件传递机制/)
    </details>  



**[⬆ 回到顶部](#Android基础)**