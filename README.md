# mouseevent
This is a mouse selection function
<!DOCTYPE html>
<html>
<head>
<meta http-equiv="Content-Type" content="text/html;charset=utf-8" />  
<meta name="viewport" content="width=device-width,initial-scale=1,maximum-scale=1,user-scalable=no">
	<title>选曲</title>
	<style type="text/css">
		body{margin:0; padding:0; position: relative;}
		span:hover{color: red;}
		a{pointer-events: none;}
		.move{position: absolute; background: rgba(5,254,222, .3); display: block;}
	</style>
</head>
<body>
<span>this is a text tag</span>
<a href="http://www.jiaotongshangcheng.com/"> this is a link</a>
<script type="text/javascript" src="http://apps.bdimg.com/libs/jquery/2.1.4/jquery.min.js"></script>
<script type="text/javascript">
	var startX = 0,
		startY = 0,
		width = 0,
		height = 0,
		bool = false;
		span = $('move');
	$(document).on({
		mousedown:function(e){
			$('body').find('.move').remove();
			span = document.createElement('span');
			span.className = 'move';
			startX = e.clientX,startY = e.clientY;
			$('.move').css({left:startX,top:startY})
			bool = true;
			console.log(span,startX,startY)
			$('body').append(span)
		},
		mousemove:function(e){
			if(bool){
				const left = Math.min(e.clientX , startX);
				const top = Math.min(e.clientY , startY);
				var width = Math.abs(startX - e.clientX);
				var height = Math.abs(startY - e.clientY);
				$('.move').css({left:left,top:top,width:width,height:height});
			}else return false;
		},
		mouseup:function(e){
			$('body').find('.move').remove();
			bool = false;
		}
	})
</script>
</body>
</html>
