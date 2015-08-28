# Silverstripe - Google Tag Manager
Tag Manager integration for Silverstripe

Author: Andrew Mc Cormack

- Populate the Tag Manger data layer easily
- Generate ecommerce transaction data layer values
- Makes setting up user ID tracking much easier

## Installation
Add the following to your composer.json file

    {  
        "require": {  
            "Cyber-Duck/Silverstripe-Google-Tag-Manager": "master"  
        },  
        "repositories": [  
            {  
                "type": "vcs",  
                "url": "https://github.com/Cyber-Duck/Silverstripe-Google-Tag-Manager"  
            }  
        ]  
    }

Run composer install and composer update to download the module  

Add the following function to the Page_Controller in your Page.php file located in your code folder. Replace XXXXX with the ID of your container which you can get from the Tag Manager interface. It takes the format GTM-XXXXX, however you don't need to include the GTM part.

```php  
<?php
public function TagManager()
{
	return GTM::snippet('XXXXX');
}
```

In your Page.ss template add $TagManager just after the opening body tag

```php  
<body>
$TagManager
```

If you wish to load it depending on environemnt you can do something like below. Generally you will only want tag manager to load in a production environemnt unless you are debugging in a local development envuronment.

```php  
<% if IsLive %>
$TagManager
<% end_if %>
```

Append the following to your app URL  
**/dev/build?flush=all**  
This rebuilds your database and clears your cache.

## About

Author: Andrew Mc Cormack

## License

The MIT License (MIT)

Copyright (c) 2015 Andrew Mc Cormack

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.