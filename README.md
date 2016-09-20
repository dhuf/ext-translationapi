# Translation API

This extension lets you fetch localized labels from TYPO3. It will automatically
export labels as JSON from any `locallang.xlf` file, given its extension key.

## Routing

Please add following rewrite rules to your `.htaccess`:

```
RewriteRule ^t3api/translation/de/(.*)$ /index.php?eID=routing&route=translationapi/$1&L=0 [QSA,L]
RewriteRule ^t3api/translation/en/(.*)$ /index.php?eID=routing&route=translationapi/$1&L=1 [QSA,L]
RewriteRule ^t3api/translation/fr/(.*)$ /index.php?eID=routing&route=translationapi/$1&L=2 [QSA,L]
```

## How-To Use

In order to fetch labels from extension `xyz`, call:

```
/t3api/translation/en/xyz
```

If you want to only return labels whose key is prefixed by, say, "module", then call:

```
/t3api/translation/en/xyz/module
```

This will effectively filter XLIFF keys and keep those starting with "module." (mind
the period). You may of course use a longer prefix, such as "module.foo", which would
filter keys starting with "module.foo.".
