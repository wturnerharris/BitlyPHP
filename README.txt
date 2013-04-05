
This is a very simple PHP library for interacting with the v3 bit.ly api (only deals with JSON format, but supports new OAuth endpoints)

==============
REQUIREMENTS:
==============

PHP, Curl, JSON

======
USAGE:
======

1. Simply download the bitly.php file and include it in your project directory

2. Instantiate the class with arguments for api keys, secrets, and login info
```php
$bitly = new Bitly( array(
	'bitlyKey' => 'YOUR_BITLY_ASSIGNED_KEY',
	'bitlyLogin' => 'YOUR_BITLY_LOGIN',
	'bitlyClientId' => 'YOUR_BITLY_ASSIGNED_CLIENT_ID_FOR_OAUTH',
	'bitlySecret' => 'YOUR_BITLY_ASSIGNED_CLIENT_SECRET_FOR_OAUTH'
) );
```

3. Make sure to include the file whenever you want to access the bitly api functionality... include_once('bitly.php');

4. Use any of the available public class methods as such:
```php
$results = $bitly->bitly_v3_shorten('http://knowabout.it', 'j.mp');

$results = $bitly->bitly_v3_expand('dYhyia');

$results = $bitly->bitly_v3_expand(array('http://bit.ly/dYhyia','http://j.mp/dYhyia'));

$result = $bitly->bitly_v3_validate('USERS_LOGIN','USERS_APIKEY');

$results = $bitly->bitly_v3_clicks('dYhyia');

$results = $bitly->bitly_v3_clicks(array('dYhyia','http://bit.ly/dYhyia'));

$results = $bitly->bitly_v3_referrers('grqSlY');

$results = $bitly->bitly_v3_countries('grqSlY');

$results = $bitly->bitly_v3_clicks_by_minute(array('grqSlY','dYhyia'));

$results = $bitly->bitly_v3_clicks_by_day(array('grqSlY','dYhyia'));

$results = $bitly->bitly_v3_bitly_pro_domain('nyti.ms');

$results = $bitly->bitly_v3_lookup('http://knowabout.it');

$results = $bitly->bitly_v3_lookup(array('http://knowabout.it','http://blog.botfu.com'));

$results = $bitly->bitly_v3_authenticate('USERS_LOGIN','USERS_PASSWORD');

$results = $bitly->bitly_v3_info(array('grqSlY','dYhyia'));

$results = $bitly->bitly_oauth_access_token('CODE_ASSIGNED_BY_BITLY', 'THE_URL_YOU_WANT_BITLY_TO_REDIRECT_TO_WHEN_APP_IS_APPROVED_BY_USER');

$results = $bitly->bitly_v3_user_clicks('USERS_ACCESS_TOKEN');

$results = $bitly->bitly_v3_user_referrers('USERS_ACCESS_TOKEN');

$results = $bitly->bitly_v3_user_countries('USERS_ACCESS_TOKEN');

$results = $bitly->bitly_v3_user_realtime_links('USERS_ACCESS_TOKEN');

$results = $bitly->bitly_v3_highvalue('USERS_ACCESS_TOKEN');

$results = $bitly->bitly_v3_search('USERS_ACCESS_TOKEN', 'awesome');

$results = $bitly->bitly_v3_realtime_bursting_phrases('USERS_ACCESS_TOKEN');

$results = $bitly->bitly_v3_realtime_hot_phrases('USERS_ACCESS_TOKEN');

$results = $bitly->bitly_v3_realtime_clickrate('USERS_ACCESS_TOKEN', 'awesome');

$results = $bitly->bitly_v3_link_info('USERS_ACCESS_TOKEN', 'http://bit.ly/S4qgbT');

$results = $bitly->bitly_v3_link_content('USERS_ACCESS_TOKEN', 'http://bit.ly/S4qgbT');

$results = $bitly->bitly_v3_link_category('USERS_ACCESS_TOKEN', 'http://bit.ly/S4qgbT');

$results = $bitly->bitly_v3_link_social('USERS_ACCESS_TOKEN', 'http://bit.ly/S4qgbT');

$results = $bitly->bitly_v3_link_location('USERS_ACCESS_TOKEN', 'http://bit.ly/S4qgbT');

$results = $bitly->bitly_v3_link_language('USERS_ACCESS_TOKEN', 'http://bit.ly/S4qgbT');
```

=============
SPECIAL NOTE:
=============

To use the new OAuth endpoints, you must first obtain an access token for a user. You do this by passing the user off to bit.ly to approve your apps access to their account...and then you use the return code along with the bitly_oauth_access_token method to obtain the actual bitly access token:

1. Present the user with a link as such <a href=" https://bit.ly/oauth/authorize?client_id=<?= bitly_clientid ?>&redirect_uri=THE_URL_YOU_WANT_BITLY_TO_REDIRECT_TO_WHEN_APP_IS_APPROVED_BY_USER">Authorize giftabit</a>

2. a code ($_REQUEST['code']) will be supplied as a param to the url Bit.ly redirects to...so you can then execute $results = bitly_oauth_access_token($_REQUEST['code'], 'THE_URL_YOU_WANT_BITLY_TO_REDIRECT_TO_WHEN_APP_IS_APPROVED_BY_USER');

3. If everything goes correctly, you should now have a $results['access_token'] value that you can use with the oauth requests for that user.

==============
SPECIAL THANKS:
==============

Kevin Marshall (https://github.com/Falicon) - for original code base.
Robin Monks (https://github.com/mozillamonks) - for great additional documentation and general suggestions/improvements.

=======
CONTACT:
=======

As always, if you've got any questions, comments, or concerns about
anything you find here, please feel free to submit issues via github: https://github/wturnerharris

=======
License:
=======

Copyright 2013 Wes Turner.

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program.  If not, see <http://www.gnu.org/licenses/>.

