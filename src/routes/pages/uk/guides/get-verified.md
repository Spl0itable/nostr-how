---
title: Отримати перевірку NIP-05
description: Як підтвердити свою особу на Nostr, щоб отримати знак перевірки та в зручніший спосіб поділитися своїм обліковим записом.
---

## [§](#what-youll-learn) Що ви дізнаєтесь у цьому посібнику

Ви могли помітити на багатьох різних клієнтах, що деякі користувачі мають знаки верифікації, як у Twitter.

NIP-05 визначає, як користувачі Nostr можуть підтвердити свою особу. Різні клієнти показують верифікацію трохи по-різному, але це важливий спосіб показати спільноті Nostr, що ви справжній користувач.

![Snort Verified](/images/snort-verified.webp)

Процес верифікації на Nostr задокументовано в Nostr Implementation Possibilities (NIP) під назвою [NIP-05](https://github.com/nostr-protocol/nips/blob/master/05.md).

NIP-05 дозволяє користувачеві Nostr зіставити свій публічний ключ з ідентифікатором в інтернеті, що базується на DNS. Механізм перевірки схожий на те, як Google вимагає від вас підтвердити володіння доменом за допомогою DNS-запису.

Основною перевагою верифікації є те, що це дозволяє користувачеві Nostr бути ідентифікованим за зручним для читання іменем, замість довгого, складного для запам'ятовування публічного ключа. Це дозволяє верифікованим користувачам Nostr легко ділитися своїм профілем з іншими.

Щоб використовувати NIP-05, користувачі Nostr додають nip05 url до свого профілю (більшість клієнтів підтримують це). URL NIP-05 виглядають як електронні листи – bob@example.com. Розглянемо частини:

1. Все, що знаходиться перед символом `@` ("bob" у нашому прикладі). Це має збігатися зі значенням поля name у вашому профілі Nostr.
2. Все, що знаходиться після символу `@` ("example.com" у нашому прикладі). Це домен, де клієнт може знайти файл `/.well-known/nostr.json`, що містить ім'я користувача та публічний ключ.

Коли клієнти бачать nip05 url, вони шукають файл `/.well-known/nostr.json` на вказаному домені. Цей файл повинен містити публічний ключ Nostr для вказаного користувача. Детальніше читайте в специфікації NIP-05.

Отримати верифікацію досить легко. Давайте розглянемо, як це зробити.

## [§](#free-verification) Отримайте верифікацію через безкоштовний сервіс

На даний момент є кілька постачальників, які допомагають користувачам отримати верифікацію безкоштовно. Це чудовий варіант, якщо у вас ще немає sats у вашому lightning гаманці. Якщо можливо, підтримайте ці проекти через донати. ⚡🤙

-   [Bitcoin Nostr](https://bitcoinnostr.com/)
-   [Nostrcheck.me](https://nostrcheck.me)
-   [zaps.lol](https://zaps.lol/)
-   [NIP05.social](https://nip05.social)
-   [Nostr-Check.com](https://nostr-check.com/)
-   [Verified Nostr](https://verified-nostr.com/)
-   [Cosa Nostr](https://cosanostr.com)

## [§](#paid-verification) Оплатіть верифікацію у постачальника

Якщо у вас немає власного домену або ви не хочете налаштовувати його самостійно, ви можете скористатися безкоштовною або платною (зазвичай лише кілька [sats](https://coinmarketcap.com/alexandria/glossary/satoshi-sats)) послугою NIP-05. Ось декілька з них:

-   [Nostrplebs](https://nostrplebs.com)
-   [Nostr Verified](https://nostrverified.com)
-   [Alby](https://getalby.com)
-   [Nostr Directory](https://nostr.directory)
-   [Nostr.band](https://nip05.nostr.band)
-   [Nostr.com.au](https://nostr.com.au)
-   [Vida](https://Vida.page)
-   [Stacker News](https://stacker.news)
-   [Nostrich House](https://nostrich.house)

## [§](#self-hosted) Самостійна верифікація

Якщо ви вже маєте власний домен, це безкоштовний варіант. Вам просто потрібно додати файл `.well-known/nostr.json` до вашого домену. Вміст файлу повинен бути наступним:

```json
{
    "names": {
        "YOUR_NOSTR_NAME": "YOUR_NOSTR_PUBLIC_KEY"
    }
}
```

За бажанням ви також можете додати розділ, щоб повідомити клієнтам, на яких ретрансляторах вас, ймовірно, можна знайти:

```json
{
  "names": {
    "YOUR_NOSTR_NAME": "YOUR_NOSTR_PUBLIC_KEY_IN_HEX_FORMAT"
  },
  "relays": {
    "YOUR_NOSTR_PUBLIC_KEY_IN_HEX_FORMAT": [
      "wss://relay.one",
      "wss://relay.two",
      ...
    ]
  }
}
```

Переконайтеся, що ви використовуєте hex версію вашого публічного ключа у вашому файлі `nostr.json`. Це версія ключа, яка **не** починається з `npub`.

Ви можете конвертувати свій ключ на [Nostr.band](https://nostr.band)

![Отримайте свій hex ключ](/images/get-hex-key.webp)

Нарешті, переконайтеся, що цей файл обслуговується з заголовком `Access-Control-Allow-Origin`, встановленим на `*`, оскільки він повинен бути доступним для клієнтів.