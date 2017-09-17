### 弹射小球
>  [链接地址]( https://hsiangleev.github.io/vue-moveBall/ )
> 1. 定义每个弹射的小球组件( ocicle )
> 2. 组件message自定义属性存放小球初始信息(可修改)<br>
> ```javascript
> 	{
> 	　　　top: "0px",        //小球距离上方坐标
> 	　　　left: "0px",        //小球距离左边坐标
> 	　　　speedX: 12,      //小球每次水平移动距离
> 	　　　speedY: 6         //小球每次垂直移动距离
> 	}
> ```
> 3. 思路
> 	* 定时器设置小球每一帧移动
> 	*  初始方向：isXtrue为true则小球为横坐标正方向；<br>
> 　　　　　　　　　isYtrue为true则小球为纵坐标正方向
> 	* 每次移动之前获取小球当前坐标(oleft,otop)，当前坐标加上移动距离为下一帧坐标
> 	* 边界判断：横轴坐标范围超过最大值则加号变减号
> 4. vue知识点
> 	* 父子组件传递信息使用props
> 	* 模板编译之前获取el宽高 <br>
> ```javascript
> beforeMount: function (){
>   this.elWidth=this.$el.clientWidth;
>   this.elHeight=this.$el.clientHeight;
> }
> ```
> 	* 子组件获取el宽高 ( this.$root.elWidth,this.$root.elHeight )
> 	* 模板编译完成后更新子组件信息<br>
> ```javascript
> 	mounted: function (){
> 	//根据父组件信息更新小球数据
> 	  this.addStyle.top=this.message.top;
> 	  this.addStyle.left=this.message.left;
> 	  this.speedX=this.message.speedX;
> 	  this.speedY=this.message.speedY;
> 	  //小球初始坐标
> 	  this.oleft=parseInt(this.addStyle.left);
> 	  this.otop=parseInt(this.addStyle.top);
> 	  this.move();
> 	}
> ```

***
