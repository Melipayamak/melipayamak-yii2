# Melipayamak Yii2


<div dir='rtl'>

### معرفی وب سرویس ملی پیامک
ملی پیامک یک وب سرویس کامل برای ارسال و دریافت پیامک و پیامک صوتی و مدیریت کامل خدمات دیگر است که براحتی میتوانید از آن استفاده کنید.

<hr>

### نصب

<p>قبل از نصب نیاز به ثبت نام در سایت ملی پیامک دارید.</p>

[**ثبت نام به همراه دریافت 200 پیامک هدیه جهت تست وبسرویس**](http://www.melipayamak.com/)

<p>پس ازثبت نام  برای نصب از راههای زیر میتوانید اقدام کنید.</p>



</div>


```php
composer require melipayamak/yii2 
```


<div dir='rtl'>

یا از طریق اضافه کردن خط زیر به فایل 
composer.json



</div>


```json
"melipayamak/yii2": "*"
```


<div dir='rtl'>


و سپس اجرای دستور 



</div>

    composer update


	
<div dir='rtl'>


### کانفیگ
	
به فایل کانفیگ کد زیر را اضافه کنید

</div>

```php
'Melipayamak' => [
            'class' => 'Melipayamak\Yii2\Melipayamak',
            'username' => 'Your username',
            'password' => 'Your password'
        ]

```

<div dir='rtl'>
	
#### نحوه استفاده
نمونه کد برای ارسال پیامک در Yii2



</div>



```php
try{
    $api = Yii::$app->Melipayamak->Api();
    $sms = $api->sms();
    $to = '09123456789';
    $from = '5000...';
    $text = 'تست وب سرویس ملی پیامک';
    $response = $sms->send($to,$from,$text);
    $json = json_decode($response);
    return $json->Value; //RecId or Error Number 
}catch(Exception $e){
    return $e->getMessage();
}
```


<div dir='rtl'>

از آنجا که وب سرویس ملی پیامک تنها محدود به ارسال پیامک نیست  شما از طریق  زیر میتوانید به وب سرویس ها دسترسی کامل داشته باشید:


</div>

```php
// وب سرویس پیامک
$smsRest = $api->sms();
$smsSoap = $api->sms('soap');
// وب سرویس تیکت پشتیبانی
$ticket = $api->ticket();
// وب سرویس برای مدیریت کامل  ارسال انبوه پیامک
$branch = $api->branch();
//وب سرویس کاربران
$users = $api->users();
//وب سرویس دفترچه تلفن
$contacts = $api->contacts()

```


<div dir='rtl'>


### دریافت لیست کامل متد ها

برای دریافت لیست کامل متد ها به آدرس زیر مراجعه کنید


[Melipayamak/melipayamak-php](https://github.com/Melipayamak/melipayamak-php)



</div>


<div dir='rtl'>

###  اطلاعات بیشتر
برای مطالعه بیشتر به صفحه معرفی [وب سرویس ملی پیامک](https://github.com/Melipayamak/Webservices) مراجعه نمایید .

</div>
