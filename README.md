#Laravel

### Composer
[Composer website](http://getcomposer.org/)

## Server Requirements
PHP >= 5.4, PHP < 7

```javascript
//How display image in Laravel 5.x
{!! Html::image('img/logo.png') !!}

<img src="{{ asset('images/ImageName.jpg')}}" alt=""/>

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

## How to display content line break in laravel
```
	<?php echo nl2br($row->message); ?>
```



##Getting a data from mySQL in Laravel
```
//File: xyzController.php
    public function vendorsList() 
    {
		//$model = xyzVendors::where('id', '=', $id)->get();
		//$result = DB::table('xyz_vendors')->paginate(15);
		$result = DB::table('xyz_vendors')->simplePaginate(5);
		
        $page_title = "xyz Vendors";
        
        return view('front.association.xyz.vendorlist', compact('result', 'page_title'));
    }
```

```
//routes.php
Route::get('rfp/vendors/list','RFPController@vendorsList');
```


```
//File: xyzview.blade.php
    <table class="table table-bordered">
		<tbody>
       @foreach($result as $data)
			
			<tr>
			
				<td>{{ $data->id }}</td> 
				<td>{{ $data->rfp_id }}</td> 
				<td>{{ $data->created_at }}</td> 
			</tr>
	   
	   @endforeach
	</tbody>
	</table>
```




## How to get Laravel 5 controller name in view
```javascript
	{{ dd(request()->route()->getAction()) }}
```







## Xampp Warning: Module 'openssl' already loaded in line 0
```
* Open xampp -> PHP -> php.ini
* Open the file php.ini in any text editor
* Press <code>CTRL + F</code> and Search for openssl
* Comment the line <code>extension=php_openssl.dll</code> by placing a semi-colon at the beginning: <code>;extension=php_openssl.dll</code>

Note : If you want to enable it again remove the semicolon
```








## How to migrate database in Laravel ?

Go to Laravel folder and run these commands
```javascript
php artisan migrate
```

rollback migration first which will destroy last migration tables with all data
```javascript
php artisan migrate:rollback
```



> **Note:** start up