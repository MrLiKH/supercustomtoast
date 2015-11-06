# supercustomtoast
自定义Toast,带来不一样的效果。
##简介
最近项目需要，有些地方的提示信息需要用到Toast，但是系统的Toast样式有点丑，位置单一，并且只能接受两个显示时间长度。因此有些时候系统的Toast有点显得很弱了。   

当然系统的Taost,也暴露了部分的方法，
 见下图：
![](http://ww2.sinaimg.cn/large/74311666jw1exr0g3jhygj20ey08uab1.jpg)   
可以借助这些方法设置直接替换视图、设置显示时长、设置边距属性、设置显示位置、设置显示文字内容。  

不过，这些远远不够，比如时间的设置。还有最重要的，是系统原生的Toast是呈队列显示，必须要等到前一条Toast消失才会显示下一条。明明是状态已经改变，可是上一状态的Toast还迟迟没有消失。  

#####于是，为了满足项目需要，搜查资料，阅读源码，完成了这个Demo 
##效果图
![](http://ww3.sinaimg.cn/large/74311666jw1exr0cd245sg20dc0nqtr1.gif)





## 方法
* 默认Toast 

	    /**
	     * 显示一条Toast
	     *
	     * @param msg 消息内容
	     */
	    public void show(String msg) {
	        show(getTextView(msg), null, null, null);
	    }
* 自定义Toast,5秒  
        	  
        /**
        * 显示一条Toast
        *
        * @param msg      消息内容
        * @param duration 持续时间，单位为毫秒
        */
        public void show(String msg, long duration) {
           show(getTextView(msg), duration, null, null);
        }
* 设置背景颜色的Toast+文字

                toast.setDefaultBackgroundColor(Color.RED, 200);
                toast.setDefaultTextColor(Color.BLUE);
                toast.show("带有背景色Toast");	   
* 自定义Toast的入场和出场动画


        /**
        * 显示一条Toast
        *
        * @param msg       消息内容
        * @param duration  持续时间，单位为毫秒
        * @param startAnim 入场动画
        * @param endAnim   离场动画
        */
        public void show(String msg, Long duration, Animation startAnim, Animation      endAnim) {
        show(getTextView(msg), duration, startAnim, endAnim);
        }

* 利用Toast显示应用Logo
	
		 ImageView iv = new ImageView(MainActivity.this);
		                iv.setLayoutParams(new ViewGroup.LayoutParams(ViewGroup.LayoutParams.WRAP_CONTENT, ViewGroup.LayoutParams.WRAP_CONTENT));
		                iv.setImageResource(R.mipmap.logo1);
		                toast.show(iv);
	 
* 自定义Toast布局
 
	    /**
	     * 显示一条Toast
	     * @param msg 消息内容
	     */
	    public void show(String msg,int layoutId,int rootId,Activity activity){
	        LayoutInflater inflater = activity.getLayoutInflater();
	        layout = inflater.inflate(layoutId,
	                (ViewGroup)activity.findViewById(rootId));
	        layout.setLayoutParams(lp_WW);
	        TextView title = (TextView) layout.findViewById(R.id.title);
	        title.setText(msg);
	        title.setTextColor(defaultTextColor);
	        show(layout, null, null, null);
	    }


##联系方式：
* [我的微博](http://www.weibo.com/3217119443 "鼠标悬停")
* [我的博客](http://www.github.io "鼠标悬停")
