# blinds
一个多种样式的百叶窗
通过获取随机数的方式：
  var i=parseInt(Math.random()*10%3);//i=2;
	eval("createDom"+(i+1)+"()");创建元素
	eval("execBlinds"+(i+1)+"()");来决定需要执行的函数
创建元素：

function createDom1(){
	var _div = null;
	var _body = document.body;
	for(var i=0;i<20;i++){
		_div = document.createElement("div");
		_div.className = "blinds";
		_div.style.backgroundPosition="0px "+(-i*30)+"px";
		_div.style.left = "0";
		_div.style.top=i*30+"px";
		_div.style.width="800px";
		_div.style.height = "0px";
		_body.appendChild(_div);
	}
}

函数1：
function execBlinds1(){
	var _timer = 0;
	var _h = 0;
	var _blinds = document.body.getElementsByTagName("div");
	function exec(){
		//window.clearTimeout(_timer);
		_h+=3;
		if(_h>30){
			clearInterval(_timer);
			return ;
		}
		for(var i=0;i<_blinds.length;i++){
			_blinds[i].style.height = _h+"px";
		}
		_timer = window.setInterval(exec,300);
	}
	exec();
}为纵向百叶窗


创建元素：

function createDom2(){
	var _div = null;
	var _body = document.body;
	for(var i=0;i<20;i++){
		_div = document.createElement("div");
		_div.className = "blinds";
		_div.style.backgroundPosition=(-i*40)+"px 0px";
		if(i%2==0){
			_div.style.top="-300px";
		}else{
			_div.style.top="300px";
		}
		_div.style.left=i*40+"px";
		_div.style.width="40px";
		_div.style.height="600px";
		_body.appendChild(_div);
	}
}
函数2：

function execBlinds2(){
	var _timer = 0;
	var _w = 0;
	var flag=false;
	var _blinds = document.body.getElementsByTagName("div");
	function exec(){
		if(flag){
			clearInterval(_timer);
			return ;
		}
		var _arr=[],_brr=[];
		for(var i=0;i<_blinds.length;i++){
			_w = parseInt(_blinds[i].style.top);_arr.push(_w);
			if(i%2==0){
				_blinds[i].style.top=_w+10+"px";
			}else{
				_blinds[i].style.top=_w-10+"px";
			}_brr.push(_blinds[i].style.top);
			if(parseInt(_blinds[i].style.top)==0){
				flag=true;
			}
		}console.log(_arr);console.log(_brr);
		_timer = window.setInterval(exec,200);
	}
	exec();
}交叉百叶窗


创建元素：

function createDom3(){
	var _div = null;
	var _body = document.body;
	for(var i=0;i<20;i++){
		_div = document.createElement("div");
		_div.className = "blinds";
		_div.style.backgroundPosition=(-i*40)+"px 0px";
		_div.style.left=i*40+"px";
		//_div.style.top="0px";
		_div.style.top=-660+(-i*60)+"px";
		_div.style.width="40px";
		//_div.style.height=-(i*4)+"px";
		_div.style.height="600px";
		_body.appendChild(_div);
	}
}

函数3：

function execBlinds3(){
	var _timer = 0;
	var _blinds = document.body.getElementsByTagName("div");
	function exec(){
		var _top;
		if(parseInt(_blinds[_blinds.length-1].style.top)==0){
			clearInterval(_timer);
			return;
		}
		var _arr = [],_brr=[];
		for(var i=0;i<_blinds.length;i++){
			_top = parseInt(_blinds[i].style.top);_arr.push(_top);
			if(_top<0){
				_blinds[i].style.top = _top+60+"px";
			}
			_brr.push(parseInt(_blinds[i].style.top));
		}console.log(_arr);console.log(_brr);
		_timer = window.setInterval(exec,200);
	}
	exec();
}阶梯百叶窗

