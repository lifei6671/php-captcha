# php-captcha

简单的php验证码库。

## PHP生成验证码图片

PHP生成验证码的原理：使用PHP的GD库，生成一张带验证码的图片，并将验证码保存在Session中。PHP生成验证码的大致流程有：

1、产生一张png的图片；

2、为图片设置背景色；

3、设置字体颜色和样式；

4、产生指定位数的随机的验证码；

5、把产生的每个字符调整旋转角度和位置画到png图片上；

6、加入噪点和干扰线防止注册机器分析原图片来恶意破解验证码；

7、输出图片；

8、释放图片所占内存。

## 图片实例

![1](https://raw.githubusercontent.com/lifei6671/php-captcha/master/examples/image/1.png)
![2](https://raw.githubusercontent.com/lifei6671/php-captcha/master/examples/image/2.png)
![3](https://raw.githubusercontent.com/lifei6671/php-captcha/master/examples/image/3.png)
![4](https://raw.githubusercontent.com/lifei6671/php-captcha/master/examples/image/4.png)
![5](https://raw.githubusercontent.com/lifei6671/php-captcha/master/examples/image/5.png)
![6](https://raw.githubusercontent.com/lifei6671/php-captcha/master/examples/image/6.png)


## 安装

使用 Composer

```json
{
    "require": {
            "lifei6671/php-captcha": "0.1.*"
    }
}
```

## 用法

```php
<?php
use Minho\Captcha\CaptchaBuilder;

$captch = new CaptchaBuilder();

$captch->initialize([
    'width' => 150,     // 宽度
    'height' => 50,     // 高度
    'line' => false,    // 直线
    'curve' => true,    // 曲线
    'noise' => 1,       // 噪点背景
    'fonts' => []       // 字体
]);

$captch->create();
```

直接输出图片：

```php
<?php
$captch->output(1);
```

保存图片到硬盘：

```php
<?php

$captch->save('1.png',1);
```

获取验证码文字：

```php
<?php

$_SESSION['captch'] = $captch->getText();
```
## 正在使用

[SmartWiki文档管理系统](https://www.iminho.me)
