DeviceDetector
==============

The Universal Device Detection library, that parses User Agents and detects devices (desktop, tablet, mobile, tv, cars, console, etc.), and detects clients (browsers, feed readers, media players, PIMs, ...), operating systems, devices, brands and models.

## Usage

Using DeviceDetector with composer is quite easy. Just add piwik/device-detector to your projects requirements. And use some code like this one:


```php
require_once 'vendor/autoload.php'

use DeviceDetector\DeviceDetector;

$dd = new DeviceDetector($userAgent);

// OPTIONAL: If called, getBot() will only return true if a bot was detected  (speeds up detection a bit)
$dd->discardBotInformation();

$dd->parse();

if ($dd->isBot()) {
  // handle bots,spiders,crawlers,...
  $botInfo = $dd->getBot();
} else {
  $clientInfo = $dd->getClient(); // holds information about browser, feed reader, media player, ...
  $osInfo = $dd->getOs();
  $device = $dd->getDevice();
  $brand = $dd->getBrand();
  $model = $dd->getModel();
}
```

## Tests

Build status (master branch) [![Build Status](https://travis-ci.org/piwik/device-detector.png?branch=master)](https://travis-ci.org/piwik/device-detector)

See also: [QA at Piwik](http://piwik.org/qa/)

## Contributing


### Hacking the library

This is a free/libre library under license GPL v3 or later.

Your pull requests and/or feedback is very welcome!

### Listing all user agents from your logs
Sometimes it may be useful to generate the list of most used user agents on your website,
extracting this list from your access logs using the following command:

```
zcat ~/path/to/access/logs* | awk -F'"' '{print $6}' | sort | uniq -c | sort -rn | head -n20000 > /home/piwik/top-user-agents.txt
```

### Contributors
Created by the [Piwik team](http://piwik.org/team/), Stefan Giehl, Matthieu Aubry, Michał Gaździk,
Tomasz Majczak, Grzegorz Kaszuba, Piotr Banaszczyk and contributors.

Together we can build the best Device Detection library.

We are looking forward to your contributions and pull requests!