<html>
<head>
	<title>轮播图</title>
	<meta charset="utf-8">
	<link rel="stylesheet" type="text/css" href="zuoye.css">
</head>
<body>
<div id="box">
<div class="pic">
	<ul>
	    <li><img src="4.jpg"></li>
		<li><img src="1.jpg"></li>
		<li><img src="2.jpg"></li>
		<li><img src="3.jpg"></li>
		<li><img src="4.jpg"></li>
		<li><img src="1.jpg"></li>
	</ul>
</div>
<div class="dian">
	<ul>
		<li class="ai"></li>
		<li></li>
		<li></li>
		<li></li>
	</ul>
</div>
<div class="button">
	<div class="leftbutton">&lt</div>
	<div class="rightbutton">&gt</div>
</div>
</div>
<script type="text/javascript" src="jquery-3.0.0.min.js"></script>
<script type="text/javascript">
	$(function(){
		var $dianli=$('#box .dian ul li');
		var $picul=$('#box .pic ul');
		var imgwidth=$('#box .pic ul li').width();
		var $butdiv=$('#box .button div');
		var index=0;
		var time=new Date();
		$('#box').hover(function(){
			clearInterval(biandong);
		},function(){
			biandong =setInterval(function(){
			index++;
			func();
		},3000);
		})
		$dianli.click(function(){
			index=$(this).index()
			$(this).addClass('ai').siblings().removeClass('ai');
			$picul.animate({marginLeft:-imgwidth*(index+1)+"px"},420);
		});
		    $butdiv.click(function(){
		    	if(new Date()-time>420){
		    		time=new Date();
			var i=$(this).index();
			if(i){
				index++;
			}
			else{
				index--;
			}
			func();
		}
		}).mousedown(function(){
			return false;
		});
		var biandong =setInterval(function(){
			index++;
			func();
		},3000);
		function func(){
			var liindex=index;
			if(liindex>=$dianli.length){
				liindex=0;
			}
			else if(liindex<0){
				liindex=$dianli.length-1;
			}
			$dianli.eq(liindex).addClass('ai').siblings().removeClass('ai');
			$picul.animate({marginLeft:-imgwidth*(index+1)+"px"},420,function(){
				if(index==$dianli.length){
					$picul.css('marginLeft',"-509px");
					index=0;
				}
				else if(index<0){
					$picul.css('marginLeft',-imgwidth*($dianli.length)+"px");
					index=$dianli.length-1;
				}
			});
		}
	});
</script>
</body>
</html>
