# Sri Lankan name stemming rules

Sri Lankan names are written in English in various formats. For example, the Sinhalese name "කරුණාරත්න" is written as "Karunaratne", "Karunarathne", "Karunarathna", or "Karunaratna". This makes string searches not so easy when you want to look up a database. 

This repository contains a list of perl-compatible (and this compatible in PHP, JS, et al) regular expression replacement patterns. 

## Data format

The `rules.json` file contains an object with keys `rules` and `descriptions`. 

`rules` object  contains key:value pairs in with key being the search pattern, and the value being the replacement pattern. 

## How to use

Using your programming language, load (and decode if necessary) the contents of the `rules.json` file. Then, load the object `rules`, and run each key:value pair as a regex replacement. 

```php
$contents = file_get_contents('rules.json');
$contents = json_decode($contents, true);
$values = $contents->rules;

$name = "Karunaratne";

foreach ($values as $search => $replace) {
	$name = preg_replace($search, $replace, $name);
}

echo $name; // "Karunarathna"
```

