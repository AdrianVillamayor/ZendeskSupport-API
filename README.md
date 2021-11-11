# ZendeskSupport-API

*By [Adrii](https://github.com/AdrianVillamayor)*

[![Latest Stable Version](https://img.shields.io/packagist/v/adrii/zendesk-api)](https://packagist.org/packages/adrii/zendesk-api)
[![Total Downloads](https://img.shields.io/packagist/dt/adrii/zendesk-api)](https://packagist.org/packages/adrii/zendesk-api)
[![License](https://img.shields.io/github/license/AdrianVillamayor/ZendeskAPI)](https://github.com/AdrianVillamayor/ZendeskAPI/blob/main/LICENSE)

Lightweight library that allows you to create, edit, delete and upload files to Zendesk Suppot. In a clean and standard way.

## Installation

Use [Composer](https://getcomposer.org/) to install the library.

```bash
composer require adrii/zendesk-api
```

### Composer
```php
use Adrii\ZendeskAPI;
```

### Manual

```php
require_once ROOT . 'ZendeskAPI.php';
```


## Usage

``` php
    
    $data = array(
        "username" => "1234qwer",
        "type" => "problem",
        "tags" => "ios,test",
        "subject" => "Test",
        "body" => "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Aenean tempor semper enim. Nam non semper ligula. Vestibulum sapien sapien, hendrerit pharetra elementum a, faucibus id nisl. Aenean ornare rhoncus ligula, eget efficitur augue suscipit vehicula. Fusce faucibus odio magna, sit amet aliquet ipsum sodales a.",
        "first_name" => "Adrii",
        "last_name" => "🍍",
        "email" => "adrian.villamayor@gmail.com",
    );
        
    for ($i = 0; $i < count($files); $i++) {
        $zendesk->upload($files[$i]['name'], $files[$i]['tmp_name']);
    }

    $comment = array(
        array(
            'type'          => $data['type'],
            'tags'          => explode(",", $data['tags']),
            'subject'       => $data['subject'],
            'comment'       => array(
                'body'      => $data['body'],
                'public'    => false,
                "uploads"   => $zendesk->getUpload()
            ),
            'requester'     => array(
                'locale_id' => '1',
                'name'      => $data['first_name'] . " " . $data['last_name'],
                'email'     => $data['email'],
            ),
            'priority'      => 'normal',
        )
    );

    $subdomain  = "{subdomain}";
    $user       = "{user}";
    $token      = "{token}";

    $zend = new ZendeskApi($subdomain, $user, $token);

    $zend->create($comment);

```


# Contributing
Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

Please make sure to update tests as appropriate.

# License
[MIT](https://github.com/AdrianVillamayor/ZendeskSupport-API/blob/main/LICENSE)

Thanks for your help! 🎉
