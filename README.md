# winston-csv-format
**winston-csv-format** writes winston logs in csv format.

[![Version][badge-vers]][npm]
[![Dependencies][badge-deps]][npm]
[![Vulnerabilities][badge-vuln]](https://snyk.io/)
[![Build Status][badge-tests]][travis]
[![Coverage Status][badge-coverage]](https://coveralls.io/github/pustovitDmytro/winston-csv-format?branch=master)
[![License][badge-lic]][github]

## Table of Contents
  - [Requirements](#requirements)
  - [Installation](#installation)
  - [Usage](#usage)
  - [Contribute](#contribute)

## Motivation
If you're struggling to format your logs/reports as [.csv](https://en.wikipedia.org/wiki/Comma-separated_values) files (or prepare import to Excel or Google Spreadsheet), this package can be a cure. Now you can use all power of winston logger, formating your data as comma-separated values.

## Requirements
To use library you need to have [node](https://nodejs.org) and [npm](https://www.npmjs.com) installed in your machine:

* node `6.0+`
* npm `3.0+`

## Installation

To install the library run following command

```bash
  npm i --save winston-csv-format
```

## Usage
The package can be used as formatter alongside any [winston](https://github.com/winstonjs/winston) transport. Default export is a constructor function, which has 2 arguments: array of fields, and [options object](#contribute). Note that fields must match keys of logged objects:

```javascript
import CSV from 'winston-csv-format';
import { createLogger, transports } from 'winston';

const csvHeaders = {
    created    : 'Creation Date',
    size       : 'Size',
    status     : 'Status',
};

const logger = createLogger({
    level      : 'info',
    format     : CSV(['created', 'status' ], { delimiter: ',' }),
    transports : [ new transports.Console() ]
});

logger.log('info', csvHeaders); // write headers

```
## Configuration
Next values can be configured as options:
* **delimiter** - delimeter between fields (```';'``` by default)
* **missed** - value, used when original value is missed in logged object (```empty string``` by default)

## Contribute

Make the changes to the code and tests and then commit to your branch. Be sure to follow the commit message conventions.

Commit message summaries must follow this basic format:
```
  Tag: Message (fixes #1234)
```

The Tag is one of the following:
* **Fix** - for a bug fix.
* **Update** - for a backwards-compatible enhancement.
* **Breaking** - for a backwards-incompatible enhancement.
* **Docs** - changes to documentation only.
* **Build** - changes to build process only.
* **New** - implemented a new feature.
* **Upgrade** - for a dependency upgrade.
* **Chore** - for tests, refactor, style, etc.

The message summary should be a one-sentence description of the change. The issue number should be mentioned at the end.


[npm]: https://www.npmjs.com/package/winston-csv-format
[github]: https://github.com/pustovitDmytro/winston-csv-format
[travis]: https://travis-ci.org/pustovitDmytro/winston-csv-format
[coveralls]: https://coveralls.io/github/pustovitDmytro/winston-csv-format?branch=master
[badge-deps]: https://img.shields.io/david/pustovitDmytro/winston-csv-format.svg
[badge-tests]: https://img.shields.io/travis/pustovitDmytro/winston-csv-format.svg
[badge-vuln]: https://img.shields.io/snyk/vulnerabilities/npm/winston-csv-format.svg?style=popout
[badge-vers]: https://img.shields.io/npm/v/winston-csv-format.svg
[badge-lic]: https://img.shields.io/github/license/pustovitDmytro/winston-csv-format.svg
[badge-coverage]: https://coveralls.io/repos/github/pustovitDmytro/winston-csv-format/badge.svg?branch=master