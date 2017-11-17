<html>
<head>
	<title>IFE Javascript Task 01</title>
</head>
<body>
<h3>污染城市列表</h3>
<ul id="aqi-list">
</ul>
<script type="text/javascript">
	var aqiData=[
	["北京",90],
	["上海",50],
	["福州",10],
	["广州",50],
	["成都",90],
	["西安",100]
	];
	var a=aqiData.filter(function(x){
		return x[1]>60;
	});
	var b=a.sort(function(x,y){
		return y[1]-x[1];
	});
	var c="";
	for(i=0;i<a.length;i++){
			c+="<li>"+a[i]+"</li>";
	}
	document.getElementById("aqi-list").innerHTML=c;
</script>
</body>
</html>
