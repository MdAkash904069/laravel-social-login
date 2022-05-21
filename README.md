
<p align="center"><a href="https://laravel.com" target="_blank"><img src="https://raw.githubusercontent.com/laravel/art/master/logo-lockup/5%20SVG/2%20CMYK/1%20Full%20Color/laravel-logolockup-cmyk-red.svg" width="400"></a></p>

<p align="center">
<a href="https://travis-ci.org/laravel/framework"><img src="https://travis-ci.org/laravel/framework.svg" alt="Build Status"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/dt/laravel/framework" alt="Total Downloads"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/v/laravel/framework" alt="Latest Stable Version"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/l/laravel/framework" alt="License"></a>
</p>

<h2>Laravel Social Login Setup :</h2><br>
<b>If You want to setup if follow the below description</b> <br>
1.create laravel project<br>
2.create laravel authentication<br>
3.create login social button<br>

4.Install laravel socialite packege->composer require laravel/socialite<br>
5.config->service=><br>
example:-<br>

'github' => [<br>
    'client_id' => env('GITHUB_CLIENT_ID'),<br>
    'client_secret' => env('GITHUB_CLIENT_SECRET'),<br>
    'redirect' => 'http://example.com/callback-url',<br>
],<br>
<br>
5.routing-><br>
Route::get('login/google', [App\Http\Controllers\Auth\LoginController::class, 'redirectToGoogle'])->name('login.google');<br>
Route::get('login/google/callback', [App\Http\Controllers\Auth\LoginController::class, 'handleGoogleCallback']);<br>
<br>
6.put url login button<br>
7.put id and secret key of app in env file<br>
8.change service url<br>
9.Time to create app google,facebook, linedin<br>
10.user extra field (provider_id,avatar)<br>
11.create user extra field<br>
<br>
protected function _registerOrloginUser($data){<br>
        $user = User::where('email','=',$data->email)->first();<br>
        if(!$user){<br>
            $user = new User;<br>
            $user->name = $data->name;<br>
            $user->email = $data->email;<br>
            $user->provider_id = $data->id;<br>
            $user->avatar = $data->avatar;<br>
            $user->save();<br>
        }<br>

        Auth::login($user);
    }


$this->_registerOrloginUser($user);<br>
        // redirect home <br>
        return redirect()->route('home');<br>





