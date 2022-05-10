# Potrans

Potrans it's PHP command line tool for automatic translation of [Gettext](https://www.gnu.org/software/gettext/) PO file with

* [Google Translator](https://cloud.google.com/translate)
* [DeepL Translator](https://www.deepl.com/)

```text
Description:
  Translate PO file with Google Translator

Usage:
  google [options] [--] <input> [<output>]

Arguments:
  input                          Input PO file path
  output                         Output PO, MO files directory [default: "~/Downloads"]

Options:
      --from=FROM                Source language (default: en) [default: "en"]
      --to=TO                    Target language (default: cs) [default: "cs"]
      --all                      Re-translate including translated sentences
      --wait=WAIT                Wait between translations in milliseconds [default: false]
      --credentials=CREDENTIALS  Path to Google Credentials file [default: "./credentials.json"]
      --project=PROJECT          Google Cloud Project ID (default: project_id from credentials.json)
      --location=LOCATION        Google Cloud Location [default: "global"]
      --cache|--no-cache         Load from cache or not
  -h, --help                     Display help for the given command. When no command is given display help for the list command
  -q, --quiet                    Do not output any message
  -V, --version                  Display this application version
      --ansi|--no-ansi           Force (or disable --no-ansi) ANSI output
  -n, --no-interaction           Do not ask any interactive question
  -v|vv|vvv, --verbose           Increase the verbosity of messages: 1 for normal output, 2 for more verbose output and 3 for debug
```

Follow command will translate whole content of `tests/example-cs_CZ.po` from English (default) to Czech language (default) with Deepl translator

```bash
bin/potrans google tests/example-cs_CZ.po ~/Downloads --credentials=your-credentials-file.json
```

Another example it's about output.

```bash
bin/potrans google tests/example-cs_CZ.po ~/Downloads --credentials=your-credentials-file.json --from=ru --to=en
```

## DeepL translator API

DeepL translator [API pricing](https://www.deepl.com/pro-api) is based on monthly subscription. There is max. 500,000 characters/month for free.

For more information visit https://www.deepl.com/pro-api

## Google Translator API

Google Translate API pricing is based on usage. Translation usage is calculated in millions of
characters (M), where 1 M = 10^6 characters. For more information, see the [Pricing FAQ](https://cloud.google.com/translate/pricing).

For more information about Google Translate API visit https://developers.google.com/translate/

See supported languages: https://developers.google.com/translate/v2/using_rest#language-params

### Getting Google Translation Credentials

1. Go to the [Google Cloud Console](https://console.developers.google.com/).
2. Create a new Project or open existing one
3. Search for [translate API](https://cloud.google.com/translate/docs/apis) and enable it then
4. Go to [IAM & Admin](https://console.cloud.google.com/iam-admin/iam) > *Service Accounts* and click to **+ Create service account**

* Chose *Service account name* and *Service account ID* and click to Create and continue
* Grant this service account access to project and add follow roles **Cloud Translation API Editor**, **AutoML Editor**

5. Create new Keys and download credentials JSON file

More information here: https://www.youtube.com/watch?v=A3knNbGfXh4

* [Translaton AI](https://cloud.google.com/translate)
* [Quick Starts](https://cloud.google.com/translate/docs/quickstarts)

## Install

```
composer require --dev om/potrans
```

## Development

1. Install composer `curl -s http://getcomposer.org/installer | php`
2. Run `composer install` for install all dependencies
3. Install PHP Curl extension (curl and json PHP extensions)

For more information about Composer visit: [https://getcomposer.org](https://getcomposer.org)

If you had `"command not found: potrans"` return, just run the command like this: `php bin/potrans` and will run without problems.

## Links

* [GNU gettext utilities](https://www.gnu.org/software/gettext/manual/html_node/)
* [PHP Gettext](https://github.com/php-gettext/Gettext)


