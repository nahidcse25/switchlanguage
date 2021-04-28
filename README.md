1.first install laravel
2.create a middleware then modify the method by below code 
 public function handle(Request $request, Closure $next)
    {
		
		if(\Session::has('locale')){
			\App::setLocale(\Session::get('locale'));
		}
        return $next($request);
    }
3.add route  web.php
	Route::get('locale/{locale}',function($lang){
       Session::put('locale',$lang);
       return redirect()->back(); 
	//echo $lang; 	   
	});
4.add middleware class on kernel.php
5.create bn,hn etc folder on resorce/lang as like en
6.create file home.php each folder bn,hn,en modify by blow code
	<?php

	return [
		'home_menu'=> 'hjghjgjhg(EN)',
		'about_menu'=> 'About(EN)',
		'contact_menu'=> 'Contact(EN)',
		'message'=> 'Welcome(En)',
	];
7.modify welcome.php by 
	<!doctype html>
<html lang="en">
  <head>
    <!-- Required meta tags -->
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">

    <!-- Bootstrap CSS -->
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.0.0-beta3/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-eOJMYsd53ii+scO/bJGFsiCZc+5NDVN2yr8+0RDqr0Ql0h+rP48ckxlpbzKgwra6" crossorigin="anonymous">

    <title>Hello, world!</title>
  </head>
  <body>
    <div class="container">
		<nav class="navbar navbar-expand-lg navbar-light bg-light">
		  <div class="container-fluid">
			<a class="navbar-brand" href="#">Navbar</a>
			<button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
			  <span class="navbar-toggler-icon"></span>
			</button>
			<div class="collapse navbar-collapse" id="navbarSupportedContent">
			  <ul class="navbar-nav me-auto mb-2 mb-lg-0">
				<li class="nav-item">
				  <a class="nav-link active" aria-current="page" href="#">@lang('home.home_menu')</a>
				</li>
				<li class="nav-item">
				  <a class="nav-link active" aria-current="page" href="#">@lang('home.about_menu')</a>
				</li>
				<li class="nav-item">
				  <a class="nav-link active" aria-current="page" href="#">@lang('home.contact_menu')</a>
				</li>
			  </ul>
			  <div class="d-flex">
				<ul class="navbar-nav me-auto mb-2 mb-lg-0">
				<li class="nav-item">
				  <a class="nav-link active" aria-current="page" href="locale/en">English</a>
				</li>
				<li class="nav-item">
				  <a class="nav-link active" aria-current="page" href="locale/bn">Bangla</a>
				</li>
			  </ul>
			  </div>
			</div>
		  </div>
		</nav>
	</div>
	<div class="row">
		<h2> @lang('home.message')</h2>
	</div>

    <!-- Optional JavaScript; choose one of the two! -->

    <!-- Option 1: Bootstrap Bundle with Popper -->
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.0.0-beta3/dist/js/bootstrap.bundle.min.js" integrity="sha384-JEW9xMcG8R+pH31jmWH6WWP0WintQrMb4s7ZOdauHnUtxwoG2vI5DkLtS3qm9Ekf" crossorigin="anonymous"></script>

    <!-- Option 2: Separate Popper and Bootstrap JS -->
    <!--
    <script src="https://cdn.jsdelivr.net/npm/@popperjs/core@2.9.1/dist/umd/popper.min.js" integrity="sha384-SR1sx49pcuLnqZUnnPwx6FCym0wLsk5JZuNx2bPPENzswTNFaQU1RDvt3wT4gWFG" crossorigin="anonymous"></script>
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.0.0-beta3/dist/js/bootstrap.min.js" integrity="sha384-j0CNLUeiqtyaRmlzUHCPZ+Gy5fQu0dQ6eZ/xAww941Ai1SxSY+0EQqNXNE6DZiVc" crossorigin="anonymous"></script>
    -->
  </body>
</html>
