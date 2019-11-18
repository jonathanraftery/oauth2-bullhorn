# Bullhorn Provider for OAuth 2.0 Client

This package provides Bullhorn OAuth 2.0 support for the PHP League's [OAuth 2.0 Client](https://github.com/thephpleague/oauth2-client).

## Installation

To install, use composer:

```
composer require jonathanraftery/oauth2-bullhorn
```

## Usage

Usage is the same as The League's OAuth client, using `\JonathanRaftery\OAuth2\Client\Provider\Bullhorn` as the provider.

### Authorization Code Flow

```php
$provider = new JonathanRaftery\OAuth2\Client\Provider\Bullhorn([
    'clientId'          => '{bullhorn-client-id}',
    'clientSecret'      => '{bullhorn-client-secret}',
    'redirectUri'       => 'https://example.com/callback-url'
]);
```

For further usage of this package please refer to the [core package documentation on "Authorization Code Grant"](https://github.com/thephpleague/oauth2-client#usage).

### Refreshing a Token

Once your application is authorized, you can refresh an expired token using a refresh token rather than going through the entire process of obtaining a brand new token. To do so, simply reuse this refresh token from your data store to request a refresh.

```php
$existingAccessToken = getAccessTokenFromYourDataStore();

if ($existingAccessToken->hasExpired()) {
    $newAccessToken = $provider->getAccessToken('refresh_token', [
        'refresh_token' => $existingAccessToken->getRefreshToken()
    ]);

    // Purge old access token and store new access token to your data store.
}
```

For further usage of this package please refer to the [core package documentation on "Refreshing a Token"](https://github.com/thephpleague/oauth2-client#refreshing-a-token).

## Testing

``` bash
$ ./vendor/bin/phpunit
```

## Credits

- [Jonathan Raftery](https://github.com/jonathanraftery)
- [All Contributors](https://github.com/jonathanraftery/oauth2-bullhorn/contributors)


## License

The MIT License (MIT). Please see [License File](https://github.com/jonathanraftery/oauth2-bullhorn/blob/master/LICENSE) for more information.
