# country-name-with-flag-and-iso-code
click on the country name and display that flag

<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<meta name="viewport" content="width=device-width, initial-scale=1.0">
	<title>country flags</title>
	<style>
	.flex-box {
		display: flex;
		justify-content: start;
		align-items: center;
	}

	.flags_img {

		background-image: url(flag-icons.png);
		background-repeat: no-repeat;
		display: inline-block;
		width: 24%;
		height: 242px;
		position: fixed;
		background-size: 11338px, 11459px;
		background-color: transparent;
		vertical-align: middle;
		background-position: 64px 44px;
		margin: 8px;
		right: 0;
	}

	#full_flags {
		background-image: url(flag-icons.png);
		background-repeat: no-repeat;
		height: 133vh;
		background-color: transparent;
		background-position: 64px 44px;
		margin: 8px; 
	}
</style>
<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.6.4/jquery.min.js"></script>
<script src="country.js"></script>
</head>

<body>
<!-- <div id="full_flags"></div> -->
<div id="flags_img"><div class="flags_img" data-icon="k"></div></div>
<div id="list"></div> 
</body>
<script>
	$(document).ready(function(){
		var $css = '';
		var $list = '<ul>';
		var col = -25;
		var row = -25;
		$.each(countries, function(i , l) {
 
			$list += ' <li data-code="iso_'+  l.code +'">' +l.name+ '  - ' + l.code +'</li>';
			if (i % 30 == 0 && i > 0) {
				
				col = -25;
				row -= 252;
			}
			$css += '[data-code="iso_'+  l.code +'"] {background-position: ' + col +'px ' + row+ 'px}';
			col -= 378;
		});
		$('style').append($css);
		$list += '</ul>';
		$('#list').append($list);
		$('#list').on('click', 'ul li', function(){
			$('#flags_img').find('div').attr('data-code', $(this).data('code'));
		});
	});
</script>
</html>
