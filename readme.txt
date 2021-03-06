插件效果：
    实现常见的盒子图片滚动效果（或称图片轮播）
    可修改后附加缓动函数，实现多种效果，详情见缓动函数表 http://easings.net/zh-cn#easeInOutQuad
    Github https://github.com/codetker/TokenFamily

html 结构(ZenCoding形式)
    -div.divClass
      -div.toLeft
      -div.toRight
      -ul.ulClass
        -li.liClass*n
    	
    -ul.controlUl
      -li*n
	
其中div.toLeft，div.toRight,ul.controlUl可选

调用方法(详情见demo)(按需设置参数)
A.divClass调用时style为1，采用scroll-left
    $(".divClass").boxScroll({   
        'liHover': 'liSelected',       //设置控制滚动的类名       
        'child': 'li',       //实际移动元素,默认为li元素
        'style': 1,          //默认为0,为margin-left，1则为scroll-left
        'stepTime': 1,       //每次运动经历的时间，单位s,默认为1s
        'direction': 'right',          //运动的方向，默认为right
        'toLeft': '.arrowLeft',        //向左运动按钮，默认为null
        'toRight': '.arrowRight',      //向右运动按钮，默认为null
        'ControlUl': '.picControl ul', //控制运动按钮，默认为null
        'circle': true,      //是否自动滚动，默认true
        'circleTime': 5      //自动滚动时间间隔，默认5s
    });

B.ulClass调用时style为0，采用margin-left
    $(".ulClass").boxScroll({
        'liHover': 'liSelected',       //设置控制滚动的类名            
        'child': 'li',       //实际移动元素,默认为li元素
        'style': 0,          //默认为0,为margin-left
        'stepTime': 1,       //每次运动经历的时间，单位s,默认为1s
        'direction': 'right',          //运动的方向，默认为right
        'toLeft': '.arrowLeft',        //向左运动按钮，默认为null
        'toRight': '.arrowRight',      //向右运动按钮，默认为null
        'ControlUl': '.picControl ul', //控制运动按钮，默认为null
        'circle': true,      //是否自动滚动，默认true
        'circleTime': 5      //自动滚动时间间隔，默认5s
    });

C.div.Class or Ul.Class调用时style为1，采用fadeIn and FadeOut
    $(".picInnerBox").boxScroll({
        'liHover': 'liSelected',       //设置控制滚动的类名
        'child': 'li',       //实际变化元素,默认为li元素
        'style': 2,          //2为fadeIn and fadeOut
        'direction': 'right',          //滚动方向
        'toLeft': '.arrowLeft',        //向左运动按钮，默认为null,为了避免快速多次点击，设置点击间隔时间至少0.8s
        'toRight': '.arrowRight',      //向右运动按钮，默认为null,为了避免快速多次点击，设置点击间隔时间至少0.8s
        'ControlUl': '.picControl ul', //控制运动按钮，默认为null
        'circle': true,      //是否自动变化，默认true
        'circleTime': 5,     //自动变化时间间隔，默认5s
        'fadeInTime': 300,   //fadeIn时间设置
        'fadeOutTime': 400   //fadeOut时间设置
    });

运行demo
    最简单的方法为改Default.html中jquery对应script元素的src为本地的jquery(离线)或CDN中的jquery(在线),然后双击Default.html即可
    或者配置myBoxScroll.jquery.json or package.json

PS:
    为了使插件总大小较小、代码复用，将A,B,C三种情况集中在一起，封装为一个原型上的方法，内部依据style控制选择。
    也可以改为多个方法在绑定到jquery原型上时用style判断对应执行，以减少多余变量和不必要的判断。