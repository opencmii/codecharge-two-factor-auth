[![Build Status](https://img.shields.io/travis/andrej-griniuk/cakephp-two-factor-auth/master.svg?style=flat-square)](https://travis-ci.org/andrej-griniuk/cakephp-two-factor-auth)
[![Coverage Status](https://img.shields.io/coveralls/andrej-griniuk/cakephp-two-factor-auth.svg?style=flat-square)](https://coveralls.io/r/andrej-griniuk/cakephp-two-factor-auth?branch=master)
[![License](https://img.shields.io/badge/license-MIT-blue.svg?style=flat-square)](LICENSE)

# TwoFactorAuth plugin for Codecharge Studio

This plugin (work-in-progress) provides two factor authentication functionality using [RobThree/TwoFactorAuth](https://github.com/RobThree/TwoFactorAuth) library. It is based on the cakePHP plugin project from Andrej Griniuk (thanks both).

When using the Login Form, after submitting correct username/password, if the user has `secret` field set, he will be asked to enter a one-time code.

**Attention:** it only provides authenticate provider and component and does not take care of users signup, management etc.

## Requirements

- Codecharge Studio 5.1+ 

## Installation

TBD

```bash
composer require andrej-griniuk/cakephp-two-factor-auth
```

## Usage (Apache/MySQL/PHP)

1. Add a VARCHAR field named 'TwoFactorAuth' in your user authentification table (ex: users)
```sql
ALTER TABLE `users` ADD `TwoFactorAuth` VARCHAR(255) NULL;
```
2. Add the plugin in Common.php (TBV)
Second, you need to load the plugin in your bootstrap.php

```php
Plugin::load('TwoFactorAuth', ['bootstrap' => true, 'routes' => true]);
```

You can see the default config values [here](https://github.com/andrej-griniuk/cakephp-two-factor-auth/blob/master/config/two_factor_auth.php) and find out what do they mean [here](https://github.com/RobThree/TwoFactorAuth#usage). To overwrite them, create two_factor_auth.php file in your `config` directory.

Then you need to set up authentication in your controller as you would normally do, but using `TwoFactorAuth.Auth` component and `TwoFactorAuth.Form` authenticator, e.g.:

See the library page for full documentation: https://github.com/RobThree/TwoFactorAuth

## Bugs & Feedback

https://github.com/andrej-griniuk/cakephp-two-factor-auth/issues
https://github.com/opencmii/codecharge-two-factor-auth/issues


## Credits
https://github.com/andrej-griniuk/cakephp-two-factor-auth
https://github.com/RobThree/TwoFactorAuth

## License

Copyright (c) 2018, [Apex Sciences][opencmii] and licensed under [The MIT License][mit].
Copyright (c) 2016, [Andrej Griniuk][andrej-griniuk] and licensed under [The MIT License][mit].

[composer]:http://getcomposer.org
[mit]:http://www.opensource.org/licenses/mit-license.php
[opencmii]:https://github.com/opencmii
