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

## How to get id or class in Laravel 
```html
@foreach($shippings as $shipping)
	<li>
    {!! Form::radio('shipping_id', $shipping->id, true, ['class' => '', 'id' => 'selectyourshipping_'.$shipping->id ]) !!} 
	<label for="selectyourshipping_<?php echo $shipping->id; ?>">
    <?php echo $shipping->name; ?> + {{ $currency[Config::get('params.currency_default')]['symbol']}} <?php echo $shipping->price; ?> 
    </label>
	</li>
@endforeach
```

> **Note:** start up