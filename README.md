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





### Failed opening required ../vendor/autoload.php
```
Warning: require(D:\xampp\htdocs\projects\your-project-name\backend/laravel/vendor/autoload.php): failed to open stream: No such file or directory in D:\xampp\htdocs\projects\your-project-name\backend\index.php on line 24

Fatal error: require(): Failed opening required 'D:\xampp\htdocs\projects\your-project-name\backend/laravel/vendor/autoload.php' (include_path='D:\xampp\php\PEAR') in D:\xampp\htdocs\projects\your-project-name\backend\index.php on line 24
```



1. ```composer install``` run this command


2. ```composer dump-autoload``` This command will clean up all compiled files and their paths.



### Composer Update Laravel, Update or install my vendors after clone project repo

Open commandline and type
```composer install```

Note: check ```storage``` folder has following folders
```
framework
  cache
  sessions
  testing
  views
logs
```




### laravel\vendor/symfony/polyfill-mbstring/bootstrap.php): failed to open stream: No such file or directory in 

Open command line and run
```
composer update --no-scripts  
```
this issue will fix.




### SQLSTATE[HY000] [1045] Access denied for user 'root'@'localhost' (using password: YES) (SQL: select * from `users` where `email` = user@domain.com limit 1)

Check yout ```.env`` file, make sure you have enter correct values for SQL database

```javascript
// ...
  DB_DATABASE=portfolio
  DB_USERNAME=root
  DB_PASSWORD=
// ...
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





## Counter / Incrementing variable for loop in Laravel blade template
```html
@foreach($categories as $key => $category)
  <li @if ($key === 0) class="active" @endif>
    <a href="#tab_c{{$key+1}}" role="tab" data-toggle="tab">
      {{$category->name}}
    </a>
  </li>
@endforeach
```


## Compiling SASS/SCSS with Laravel Mix

### Browsersync with Laravel Mix

1: Install npm dependencies:
```
$ npm install browser-sync browser-sync-webpack-plugin webpack-dev-ser
```

2: Open webpack.mix.js and append following code:
```
const BrowserSyncPlugin = require('browser-sync-webpack-plugin')
mix.webpackConfig({
  plugins: [
    new BrowserSyncPlugin({
      open: 'external',
      host: 'projectname.local',
      proxy: 'projectname.local',
      files: ['resources/views/**/*.php', 'app/**/*.php', 'routes/**/*.php']
    })
```

That’s it for the configuration!
<b>Note</b>: see Virtual Host configuration details(#xampp-virtual-host-for-sub-directory)

3: To Webpack and then Browsersync your app:
```
$ npm run watch
```








### How to create custom route or new page in laravel 5.0

1. Open ```routes.php``` file ```app/Http/routes.php```


```php
...
Route::get('/new-page', 'NewPageController@NewPage');
...
```

2. Open ```app\Http\Controllers``` and create file with same name of routes ```ProductQouteController.php```

2.1 Add following code

```php
<?php

namespace App\Http\Controllers;

use Illuminate\Http\Request;
use App\Http\Requests;
use Auth,
    Config;
use App\Cart;
use App\CartQuote;
use App\General;
use View;
use DB;

class NewPageController extends Controller {

    private $sessionId;

    /**
     * Create a new controller instance.
     *
     * @return void
     */
    public function __construct() {

	}

    public function NewPage() {
        return view('front.newpage.index');
    }
}
```


3. Open ```resources\views\front\newpage``` Create ```index.blade.php``` file
3.1 
	```html
		// Write your code or markup etc..
	```
	
4. Open this url on your browser ```http://localhost/project-name/new-page```































### XAMPP Virtual Host for sub directory
Point all domains to root folder and one/specific domain to a subfolder in the root folder

1. Open this file.
<code>I:\xampp\apache\conf\extra\httpd-vhosts.conf</code>

2. Paste this code
```html
<VirtualHost *:80>
    DocumentRoot "I:/xampp/htdocs/projects"
    ServerName _default_
</VirtualHost>

<VirtualHost *:80>
    ServerAdmin webmaster@doamin.com
    DocumentRoot "I:/xampp/htdocs/projects/myProjectName/"
    ServerName student.breakoutedu.com
    ErrorLog "logs/sub.domin.com-error.log"
    CustomLog "logs/sub.domin.com-common.log" common
</VirtualHost>
```

3. Open this file.
<code>C:\Windows\System32\drivers\etc\hosts</code>

4. Paste this code <code>127.0.0.1 sub.domin.com</code>




### Variable value split into two variables

```php
list($one, $two) = explode("-", "59-l<3veR!f@t", 2);
```





### How to migrate Laravel database
First make sure you have created migration file under

```
{project-name}/database
 =====================/factories
 =====================/migrations
 =====================/seeds
```

Open cmd and run this line.
```
 php artisan migrate
```



#### Syntax error or access violation: 1071 Specified key was too long;

We have to do is edit ```{Project-name}/App/Providers/AppServiceProvider.php``` file.


```
use Illuminate\Support\Facades\Schema; // <-- add this  line

public function boot()
{
    Schema::defaultStringLength(191); // <-- add this  line
}
```





#### Base table or view already exists: 1050 Table 'password_resets' already exists

It will happend when migrate and it broke half way.

Run this command
```
php artisan migrate:fresh
```
 It will drop all the existing tables without rolling back or calling down method of migrations.
 
 
 
 
 
#### import dummy data

```
  php artisan db:seed
```




#### The only supported ciphers are AES-128-CBC and AES-256-CBC with the correct key lengths.

The key will be written automatically in your ```.env``` file.
APP_KEY=YOUR_GENERATED_KEY

```
php artisan key:generate
```