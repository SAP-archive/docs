---
layout: concept
title: Gold Entities List
permalink: /concepts/gold-entities
---

This is the list of current entities that we detect, with examples and formatted information for each.
Keep an eye on it, as we're always improving the detection for current entities, adding new entities, or improving the information we extract from them.

| a - d | e - j | h - n | n - p | p - s | t - x |
| --- | --- | --- | --- | --- | --- |
| [`cardinal`](https://cai.tools.sap/docs/concepts/gold-entities#cardinal) | [`email`](https://cai.tools.sap/docs/concepts/gold-entities#email) | [`language`](https://cai.tools.sap/docs/concepts/gold-entities#language) | [`number`](https://cai.tools.sap/docs/concepts/gold-entities#number) | [`percent`](https://cai.tools.sap/docs/concepts/gold-entities#percent) | [`temperature`](https://cai.tools.sap/docs/concepts/gold-entities#temperature) |
| [`color`](https://cai.tools.sap/docs/concepts/gold-entities#color) | [`emoji`](https://cai.tools.sap/docs/concepts/gold-entities#emoji) | [`location`](https://cai.tools.sap/docs/concepts/gold-entities#location) | [`ordinal`](https://cai.tools.sap/docs/concepts/gold-entities#ordinal) | [`person`](https://cai.tools.sap/docs/concepts/gold-entities#person) |[`url`](https://cai.tools.sap/docs/concepts/gold-entities#url) |
| [`datetime`](https://cai.tools.sap/docs/concepts/gold-entities#datetime) | [`ip`](https://cai.tools.sap/docs/concepts/gold-entities#ip) | [`mass`](https://cai.tools.sap/docs/concepts/gold-entities#mass) | [`organization`](https://cai.tools.sap/docs/concepts/gold-entities#organization) | [`set`](https://cai.tools.sap/docs/concepts/gold-entities#set) | [`volume`](https://cai.tools.sap/docs/concepts/gold-entities#volume) |
| [`distance`](https://cai.tools.sap/docs/concepts/gold-entities#distance) | [`interval`](https://cai.tools.sap/docs/concepts/gold-entities#interval) | [`money`](https://cai.tools.sap/docs/concepts/gold-entities#money) | [`phone`](https://cai.tools.sap/docs/concepts/gold-entities#phone) | [`sort`](https://cai.tools.sap/docs/concepts/gold-entities#sort) | 
| [`duration`](https://cai.tools.sap/docs/concepts/gold-entities#duration) | [`job`](https://cai.tools.sap/docs/concepts/gold-entities#job) | [`nationality`](https://cai.tools.sap/docs/concepts/gold-entities#nationality) | [`pronoun`](https://cai.tools.sap/docs/concepts/gold-entities#pronoun) | [`speed`](https://cai.tools.sap/docs/concepts/gold-entities#speed) |


## The 28 Gold Entities

### Cardinal

```json
{
  "bearing": 45.0,
  "raw": "northeast",
  "confidence": 0.99
}
```

| Entity | Examples |
| ------ | -------- |
| `cardinal` | north, southeast, north-west, south south east |
| **Key** | **Comments** |
| `bearing` | Float, the cardinal point bearing in degrees |
| `raw` | The raw value extracted from the sentence |
| `confidence` | The confidence score between 0 and 1 for the detection |

### Color

```json
{
  "rgb": "rgb(0,0,255)",
  "hex": "#0000ff",
  "raw": "blue",
  "confidence": 0.99
}
```

| Entity | Examples |
| ------ | -------- |
| `color` | blue, red, orange, dark blue, light green |
| **Key** | **Comments** |
| `rgb` | String, the rgb code of the color |
| `hex` | String, the hexadecimal value of the color |
| `raw` | The raw value extracted from the sentence |
| `confidence` | The confidence score between 0 and 1 for the detection |

### Datetime

```json
{
  "formatted": "Thursday, 06 October 2016 at 09:00:00 AM",
  "iso": "2016-10-06T09:00:00Z",
  "accuracy": "day",
  "chronology": "future",
  "state": "relative",
  "raw": "next Thursday",
  "confidence": 0.92
}
```

| Entity | Examples |
| ------ | -------- |
| `datetime` | the next friday, today, September 7 2016, 12/12/1992, this evening, mid-november, eoy |
| **Key** | **Comments** |
| `formatted` | String, the written format of the datetime |
| `iso` | String, the <a target="_blank" href="http://www.iso.org/iso/home/standards/iso8601.htm">ISO-8601</a> standard of the datetime in UTC |
| `accuracy` | String, the accuracy of the explicitly given datetime |
|| Can be composed of one or more of `year`, `month`, `week`, `day`, `halfday`, `hour`, `min`, `sec`, `now` separated by a coma (`,`) |
| `chronology` | String, the point in time referenced by the datetime |
|| Can be `past`, `present`, or `future` |
| `state` | String, the type of the datetime |
|| Can be `relative`, or `absolute` |
| `raw` | The raw value extracted from the sentence |
| `confidence` | The confidence score between 0 and 1 for the detection |

### Distance

```json
{
  "scalar": 24.0,
  "unit": "mi",
  "meters": 38624.159999999996,
  "raw": "twenty-four miles",
  "confidence": 0.97
}
```

| Entity | Examples |
| ------ | -------- |
| `distance` | 20 meters, seven miles, ten kms, 156 centimeters, .8 foot |
| **Key** | **Comments** |
| `scalar` | Float, the countable |
| `unit` | String, the quantifier |
|| Can be `km` (kilometers), `m` (meters), `mi` (miles), `ft` (feet), `in` (inches), etc. |
| `meters` | Float, the distance in meters |
| `raw` | The raw value extracted from the sentence |
| `confidence` | The confidence score between 0 and 1 for the detection |

### Duration

```json
{
  "chrono": "02:00:00:00",
  "years": 0.005478757133798352,
  "months": 0.06575342465753424,
  "days": 2.0,
  "hours": 48.0,
  "minutes": 2880.0,
  "seconds": 172800.0,
  "raw": "two days",
  "confidence": 0.99
}
```

| Entity | Examples |
| ------ | -------- |
| `duration` | five days, one year, 27 seconds, two days and 3 hours, 72 weeks |
| **Key** | **Comments** |
| `chrono` | String, a formatted representation of the duration in the form of `:xx:xx:` |
| `years` | Float, the number of years in this duration |
| `months` | Float, the number of months in this duration |
| `days` | Float, the number of days in this duration |
| `hours` | Float, the number of hours in this duration |
| `minutes` | Float, the number of minutes in this duration |
| `seconds` | Float, the number of seconds in this duration |
| `raw` | The raw value extracted from the sentence |
| `confidence` | The confidence score between 0 and 1 for the detection |

### Email

```json
{
  "local": "paul",
  "tag": null,
  "domain": "cai.tools.sap",
  "raw": "paul@cai.tools.sap",
  "confidence": 0.99
}
```

| Entity | Examples |
| ------ | -------- |
| `email` | hello@cai.tools.sap, hello+devs@cai.tools.sap, hello.you+devs@sap.co.uk |
| **Key** | **Comments** |
| `local` | String, the local part of the email |
| `tag` | String, the tag part of the email |
| `domain` | String, the domain of the email |
| `raw` | The raw value extracted from the sentence |
| `confidence` | The confidence score between 0 and 1 for the detection |

### Emoji

```json
{
	"formatted": "happy",
	"feeling": "happy",
	"tags": [
		"eye",
		"face",
		"mouth",
		"open",
		"smile"
	],
	"unicode": "U+1F604",
	"description": "smiling face with open mouth & smiling eyes",
	"raw": ":)",
	"confidence": 0.99
}
```

| Entity | Examples |
| ------ | -------- |
| `emoji` | :), :heart:,	🙂 |
| **Key** | **Comments** |
| `formatted` | String, the localized feeling of the emoji |
| `feeling` | String, the expressed sentiment of the emoji |
| `tags` | Array of String, a list of word related to the emoji |
| `unicode` | String, the unicode codepoint of the emoji |
| `description` | String, a fully-written sentence describing the emoji |
| `raw` | The raw value extracted from the sentence |
| `confidence` | The confidence score between 0 and 1 for the detection |

### IP

```json
{
  "formatted": "Fontenay-sous-Bois, Île-de-France, FR",
  "lat": 48.8544,
  "lng": 2.4827,
  "raw": "82.121.114.213",
  "confidence": 0.99
}
```

| Entity | Examples |
| ------ | -------- |
| `ip` | 127.0.0.1, 192.157.0.54, 153.34.43.0 |
| **Key** | **Comments** |
| `formatted` | String, the full denomination of the ip's location |
| `lat` | Float, the latitude of the ip's location |
| `lng` | Float, the longitude of the ip's location |
| `raw` | The raw value extracted from the sentence |
| `confidence` | The confidence score between 0 and 1 for the detection |

### Interval

```json
{
  "begin": "2016-10-31T09:00:00Z",
  "end": "2016-11-06T09:00:00Z",
  "begin_accuracy": "day",
  "end_accuracy": "day",
  "begin_chronology": "future",
  "end_chronology": "future",
  "timespan": 518400.0,
  "raw": "from monday to sunday",
  "confidence": 0.96
}
```

| Entity | Examples |
| ------ | -------- |
| `interval` | between today and tomorrow, from now to next week, wednesday the 3rd between 2pm and 3pm, starting sunday ending monday |
| **Key** | **Comments** |
| `begin` | String, the <a target="_blank" href="http://www.iso.org/iso/home/standards/iso8601.htm">ISO-8601</a> standard of the start point in UTC |
| `end` | String, the <a target="_blank" href="http://www.iso.org/iso/home/standards/iso8601.htm">ISO-8601</a> standard of the end point in UTC |
| `begin_chronology` | String, comma separated points in time referenced by the begin field |
|| Can be `past`, `present`, or `future` |
| `end_chronology` | String, comma separated points in time referenced by the end field |
|| Can be `past`, `present`, or `future` |
| `begin_accuracy` | String, the accuracy of the explicitly given begin datetime |
|| Can be composed of one or more of `year`, `month`, `week`, `day`, `halfday`, `hour`, `min`, `sec`, `now` separated by a coma (`,`) |
| `end_accuracy` | String, the accuracy of the explicitly given end datetime |
|| Can be composed of one or more of `year`, `month`, `week`, `day`, `halfday`, `hour`, `min`, `sec`, `now` separated by a coma (`,`) |
| `timespan` | Float, the duration of the interval |
| `raw` | The raw value extracted from the sentence |
| `confidence` | The confidence score between 0 and 1 for the detection |

### Job

```json
{
	"raw": "web designer",
  "confidence": 0.85
}
```

| Entity | Examples |
| ------ | -------- |
| `job` | CTO, farmer, financial accoutant, chief operator, actress |
| **Key** | **Comments** |
| `raw` | The raw value extracted from the sentence |
| `confidence` | The confidence score between 0 and 1 for the detection |

### Language

```json
{
  "short": "NL",
  "long": "NLD",
  "raw": "Dutch",
  "confidence": 0.76
}
```

| Entity | Examples |
| ------ | -------- |
| `language` | French, Hindi, Russian,  |
| **Key** | **Comments** |
| `short` | String, the <a target="_blank" href="https://www.iso.org/iso/home/standards/language_codes.htm">ISO 639-1</a> standard language code |
| `long` | String, the <a target="_blank" href="https://www.iso.org/iso/home/standards/language_codes.htm">ISO 639-2</a> standard language code |
| `raw` | The raw value extracted from the sentence |
| `confidence` | The confidence score between 0 and 1 for the detection |

### Location

```json
{
  "formatted": "41000 Blois, France",
  "lat": 47.58609209999999,
  "lng": 1.3359475,
  "place": "ChIJXdLII5VX40cRsCk4BdfIDQQ",
  "type": "locality",
  "country": "fr",
  "raw": "Blois",
  "confidence": 0.84
}
```

| Entity | Examples |
| ------ | -------- |
| `location` | San Francisco, Paris, East London, 123 Abbey Road |
| **Key** | **Comments** |
| `formatted` | String, the full denomination of the location |
| `lat` | Float, the latitude of the location |
| `lng` | Float, the longitude of the location |
| `place` | String, the Google Places id of the location |
| `type` | Float, the precision type of the location |
|| Can be one of `country`, `locality`, `sublocality`, `postal_code`, `route`, `intersection`, `political`, `neighborhood`, `premise`, `airport`, `park`, ... |
| `country` | String, the <a target="_blank" href="https://www.iso.org/iso-3166-country-codes.html">ISO 3166-2</a> code for the country in which the location is |
| `raw` | The raw value extracted from the sentence |
| `confidence` | The confidence score between 0 and 1 for the detection |

### Mass

```json
{
  "value": 28.0,
  "unit": "lbs",
  "grams": 12700.576,
  "raw": "28 lbs",
  "confidence": 0.99
}
```

| Entity | Examples |
| ------ | -------- |
| `mass` | 45 pounds, twenty-one grams, thirty seven kgs, 0.98 mg, 23 kilograms |
| **Key** | **Comments** |
| `scalar` | Float, the countable |
| `unit` | String, the quantifier |
|| Can be `lbs` (pounds), `kg` (kilograms), `g` (grams), `oz` (ounces), etc. |
| `grams` | Float, the mass in grams |
| `raw` | The raw value extracted from the sentence |
| `confidence` | The confidence score between 0 and 1 for the detection |

### Money

```json
{
  "amount": 16.0,
  "currency": "EUR",
  "dollars": 17.92,
  "raw": "sixteen euros",
  "confidence": 0.98
}
```

| Entity | Examples |
| ------ | -------- |
| `money` | 3.14 euros, eight millions dollars, $6, 56 ₩, seventy-eight zlotys |
| **Key** | **Comments** |
| `amount` | Float, the countable |
| `currency` | String, the <a target="_blank" href="https://www.iso.org/iso/home/standards/currency_codes.htm">ISO 4217</a> standard currency code |
| `dollars` | Float, the amount of money in dollars |
| `raw` | The raw value extracted from the sentence |
| `confidence` | The confidence score between 0 and 1 for the detection |

### Nationality

```json
{
  "short": "PT",
  "long": "PRT",
  "country": "Portugal",
  "raw": "Portuguese",
  "confidence": 0.97
}
```

| Entity | Examples |
| ------ | -------- |
| `nationality` | French, Spanish, Australian |
| **Key** | **Comments** |
| `short` | String, the <a target="_blank" href="https://www.iso.org/iso/country_codes">ISO 3166-1 alpha2</a> standard country code |
| `long` | String, the <a target="_blank" href="https://www.iso.org/iso/country_codes">ISO 3166-1 alpha3</a> standard country code |
| `country` | String, the name of the country for which the nationality refers to |
| `raw` | The raw value extracted from the sentence |
| `confidence` | The confidence score between 0 and 1 for the detection |

### Number

```json
{
  "scalar": 27000,
  "raw": "twenty-seven thousand",
  "confidence": 0.83
}
```

| Entity | Examples |
| ------ | -------- |
| `number` | one thousand, 3, 9,000, seven million |
| **Key** | **Comments** |
| `scalar` | Integer, the number |
| `raw` | The raw value extracted from the sentence |
| `confidence` | The confidence score between 0 and 1 for the detection |

### Ordinal

```json
{
  "rank": -1,
  "raw": "last",
  "confidence": 0.98
}
```

| Entity | Examples |
| ------ | -------- |
| `ordinal` | 3rd, 158th, last, seventh |
| **Key** | **Comments** |
| `rank` | Integer, the number behind the ordinal |
| `raw` | The raw value extracted from the sentence |
| `confidence` | The confidence score between 0 and 1 for the detection |

### Organization

```json
{
  "raw": "Apple",
  "confidence": 0.99
}
```

| Entity | Examples |
| ------ | -------- |
| `organization` | Lehman Brothers, NASA, Apple |
| **Key** | **Comments** |
| `raw` | The raw value extracted from the sentence |
| `confidence` | The confidence score between 0 and 1 for the detection |

### Percent

```json
{
  "scalar": 86.0,
  "unit": "%",
  "percent": 86.0,
  "raw": "86 percent",
  "confidence": 0.99
}
```

| Entity | Examples |
| ------ | -------- |
| `percent` | 99%, 2 percent, seventy-seven percents, 12 permyriad |
| **Key** | **Comments** |
| `scalar` | Float, the countable |
| `unit` | String, the quantifier|
|| Can be `%` (percent), `‰` (permil), `‱` (permyriad), `ppb` (part per billion), etc. |
| `raw` | The raw value extracted from the sentence |
| `confidence` | The confidence score between 0 and 1 for the detection |

### Person

```json
{
  "fullname": "Dave Pitterson",
  "raw": "Dave Pitterson",
  "confidence": 0.97
}
```

| Entity | Examples |
| ------ | -------- |
| `person` | John Smith, David H. Doe, Dave |
| **Key** | **Comments** |
| `fullname` | String, the full name of the person |
| `raw` | The raw value extracted from the sentence |
| `confidence` | The confidence score between 0 and 1 for the detection |

### Phone

```json
{
  "number": "3612374040",
  "raw": "(361) 237 4040",
  "confidence": 0.88
}
```

| Entity | Examples |
| ------ | -------- |
| `phone` | +91-22-265 9000, 64 4 437-4746, 0682753582, (123) 123 1234 |
| **Key** | **Comments** |
| `number` | String, the normalized phone extracted |
| `raw` | The raw value extracted from the sentence |
| `confidence` | The confidence score between 0 and 1 for the detection |

### Pronoun

```json
{
  "person": 1,
  "number": "singular",
  "gender": "unkown",
  "raw": "I",
  "confidence": 0.99
}
```

| Entity | Examples |
| ------ | -------- |
| `pronoun` | I, we, it, you, us |
| **Key** | **Comments** |
| `person` | Integer, the person of the pronoun  |
| | Can be 1, 2 or 3 |
| `number` | String, the number of the pronoun  |
| | Can be singular or plural |
| `gender` | String, the gender of the pronoun |
| | Can be unknown, neutral, male of female |
| `raw` | The raw value extracted from the sentence |
| `confidence` | The confidence score between 0 and 1 for the detection |


### Set

```json
{
  "next": "2016-12-02T18:18:02Z",
  "frequency": "monthly",
  "interval": 2,
  "rrule": "RRULE:FREQ=MONTHLY;INTERVAL=2",
  "raw": "every two months",
  "confidence": 0.99
}
```

| Entity | Examples |
| ------ | -------- |
| `set` | every Sunday, each day, monthly, every 2 weeks |
| **Key** | **Comments** |
| `next` | String, the <a target="_blank" href="http://www.iso.org/iso/home/standards/iso8601.htm">ISO-8601</a> representation of the next occurence in UTC |
| `frequencey` | String, the frequency this event is repeating |
| | Can be `yearly`, `monthly`, `weekly`, `daily`, `hourly`, `minutely`, `secondly` |
| `interval` | Integer, the interval between two occurences relative to the frequency |
| `rrule` | String, the <a target="_blank" href="https://tools.ietf.org/html/rfc5545#section-3.3.10">RFC 5545</a> compliant recurence rule |
| `raw` | The raw value extracted from the sentence |
| `confidence` | The confidence score between 0 and 1 for the detection |

### Sort

```json
{
  "order": "DESC",
  "criterion": "expensive",
  "raw": "least expensive",
  "confidence": 0.96
}
```

| Entity | Examples |
| ------ | -------- |
| `sort` | most valuable, best, least affordable, cheapest |
| **Key** | **Comments** |
| `order` | String, the order to sort (MySQL inspired) |
| `criterion` | String, the criterion to sort |
| `raw` | The raw value extracted from the sentence |
| `confidence` | The confidence score between 0 and 1 for the detection |

### Speed

```json
{
  "scalar": 37.0,
  "unit": "km/h",
  "mps": 10.277777777777779,
  "raw": "thirty-seven kilometers per hour",
  "confidence": 0.57
}
```

| Entity | Examples |
| ------ | -------- |
| `speed` | 7 mph, 10 km/h, seven meters per second |
| **Key** | **Comments** |
| `scalar` | Float, the countable |
| `unit` | String, the quantifier |
|| Can be `km/h` (kilometer per hour), `mi/s` (miles per second), `kt` (knots), etc. |
| `mps` | Float, the speed in meters per second |
| `raw` | The raw value extracted from the sentence |
| `confidence` | The confidence score between 0 and 1 for the detection |

### Temperature

```json
{
  "scalar": 9.0,
  "unit": "F",
  "celsius": -12.777777777777777,
  "raw": "9 degree Farhenheit",
  "confidence": 0.97
}
```

| Entity | Examples |
| ------ | -------- |
| `temperature` | 25 degrees Celcius, 70° F, seven degC, 5 rankines |
| **Key** | **Comments** |
| `scalar` | Float, the countable |
| `unit` | String, the quantifier |
|| Can be `C` (Celsius), `K` (Kelvin), `F` (Fahrenheit), `R` (Rankine), etc. |
| `celsius` | Float, the temperature in celsius |
| `raw` | The raw value extracted from the sentence |
| `confidence` | The confidence score between 0 and 1 for the detection |

### Url

```json
{
  "scheme": "https",
  "host": "pokebot.cai.tools.sap",
  "path": "/register",
  "params": null,
  "query": null,
  "fragment": null,
  "raw": "https://pokebot.cai.tools.sap/register",
  "confidence": 0.99
}
```

| Entity | Examples |
| ------ | -------- |
| `url` | https://cai.tools.sap, localhost:9000, api.cai.tools.sap/v2/request |
| **Key** | **Comments** |
| `scheme` | String, the URL scheme |
|| Can be `http`, `https`, `mailto`, `ssh`, `git`, etc. |
| `host` | String, the host of the URL|
| `path` | String, the URL path|
| `params` | String, the parameters of the URL|
| `query` | String, the query parameters of the URL|
| `fragment` | String, the anchor of the URL|
| `raw` | The raw value extracted from the sentence |
| `confidence` | The confidence score between 0 and 1 for the detection |

### Volume

```json
{
  "scalar": 90.0,
  "unit": "hl",
  "liters": 9000.0,
  "raw": "90 hectoliters",
  "confidence": 0.96
}
```

| Entity | Examples |
| ------ | -------- |
| `volume` | 30 liters, two barrels, 1/2 tbsp |
| **Key** | **Comments** |
| `scalar` | Float, the countable |
| `unit` | String, the quantifier |
|| Can be `l` (liters), `tsp` (teaspoons), `pt` (pints), etc. |
| `liters` | Float, the volume in liters |
| `raw` | The raw value extracted from the sentence |
| `confidence` | The confidence score between 0 and 1 for the detection |
