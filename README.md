TIP：
1.slimScroll在使用的时候要依赖JQ，所以首次使用的时候要引入JQ再引入simScroll插件
2.不支持resize的时候重新调用插件，不过已经修改过源码，这是修改过的版本

resize重新调用插件增加的代码部分：
	function setScroll(){
		$(".box-list").slimScroll({
			height: boxHeight,
			alwaysVisible: true,
		});
	}

	setScroll();

	$(window).on("resize",setScroll);

	
插件的调用以及参数设置：
$(function() {
    $(".slimscroll").slimScroll({
        width: 'auto', //可滚动区域宽度
        height: '100%', //可滚动区域高度
        size: '10px', //组件宽度
        color: '#000', //滚动条颜色
        position: 'right', //组件位置：left/right
        distance: '0px', //组件与侧边之间的距离
        start: 'top', //默认滚动位置：top/bottom
        opacity: .4, //滚动条透明度
        alwaysVisible: true, //是否 始终显示组件
        disableFadeOut: false, //是否 鼠标经过可滚动区域时显示组件，离开时隐藏组件
        railVisible: true, //是否 显示轨道
        railColor: '#333', //轨道颜色
        railOpacity: .2, //轨道透明度
        railDraggable: true, //是否 滚动条可拖动
        railClass: 'slimScrollRail', //轨道div类名 
        barClass: 'slimScrollBar', //滚动条div类名
        wrapperClass: 'slimScrollDiv', //外包div类名
        allowPageScroll: true, //是否 使用滚轮到达顶端/底端时，滚动窗口
        wheelStep: 20, //滚轮滚动量
        touchScrollStep: 200, //滚动量当用户使用手势
        borderRadius: '7px', //滚动条圆角
        railBorderRadius: '7px' //轨道圆角
    });
});


slimScroll事件——当滚动条达到父容器的顶部或底部触发事件：

$(selector).slimScroll().bind('slimscroll', function(e, pos){
    console.log("Reached " + pos");
});

完整例子：
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>slimScroll插件使用例子</title>
</head>
<body>
	
    <div class="superDiv">  
        <div id="innerDiv">  
            <p>xxxxxxxxxxxxxx</p>
			<p>xxxxxxxxxxxxxx</p>
			<p>xxxxxxxxxxxxxx</p>
			<p>xxxxxxxxxxxxxx</p>
			<p>xxxxxxxxxxxxxx</p>			
        </div>  
    </div>  
	
	
	<script src="jquery.min.js"></script>
    <script src="jquery.slimscroll.js"></script>
    <script>
    
        $(function(){  
            $('#innerDiv').slimScroll({  
                height: '250px',
				railVisible: false, //是否 显示轨道
                opacity:0
            });
            
            $('#innerDiv').slimScroll().bind('slimscroll', function(e, pos){  
                if(pos=='bottom'){
                   // 执行其他逻辑
                }
            });  
        });  
        
    </script>
</body>
</html>