#Laravel

### Composer
[Composer website](http://getcomposer.org/)

## Server Requirements
PHP >= 5.4, PHP < 7

```javascript
//How display image in Laravel 5.x
{!! Html::image('img/logo.png') !!}
```


## How to check user is logged in Laravel
```html
<script>
	<?php
	if($user = Auth::user())
	{ 
	  echo 'jQuery("body").addClass("login");';
	}else{
	  echo 'jQuery("body").addClass("logout");';
	 }
	?> 
</script>
```

> **Note:** start up