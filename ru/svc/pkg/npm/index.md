---
title: npmjs.org
---

Реестр npmjs.org отличается от любого другого реестра NPM только 
наличием веб-интерфейса и правилами обработки scoped-пакетов. Основную
документацию по взаимодействию с реестром NPM можно прочитать на 
[соответствующей странице]({{ 'ru/dev/js/npm/registry-modifications' | relative_url }}).

# Публикация scoped-пакета

Публикация приватных scoped-пакетов (e.g. `@ama-team/scoped-package`) в
npmjs.org разрешена только владельцам платных аккаунтов, поэтому при 
выполнении `npm publish` от имени бесплатного аккаунта можно увидеть 
следующую ошибку:
 
```
npm ERR! publish Failed PUT 402
npm ERR! Linux 3.19.0-32-generic
npm ERR! argv "/usr/bin/nodejs" "/usr/bin/npm" "publish"
npm ERR! node v6.9.5
npm ERR! npm  v3.10.10
npm ERR! code E402

npm ERR! You need a paid account to perform this action. For more info, visit: https://www.npmjs.com/private-modules : { package name }
npm ERR! 
npm ERR! If you need help, you may report this error at:
npm ERR!     <https://github.com/npm/npm/issues>

npm ERR! Please include the following file with any support request:
npm ERR!     { current directory }/npm-debug.log
```

Для того, чтобы опубликовать публичный scoped-пакет, необходимо 
указать, что он является публичным:

```
npm publish --access public
```

После этого загрузка должна пройти без проблем.