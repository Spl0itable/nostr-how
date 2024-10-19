---
title: Децентралізоване публікування для вебу
description: Nostr - це простий, відкритий протокол, який дозволяє дійсно стійке до цензури та глобальне публікування з цінністю за цінність у вебі.
---

## Що таке Nostr?

Nostr розшифровується як "Notes and Other Stuff Transmitted by Relays" (Нотатки та інші речі, передані ретрансляторами). Як і HTTP або TCP-IP, Nostr є протоколом; відкритим стандартом, на основі якого будь-хто може створювати. Сам Nostr не є додатком або сервісом, на який ви підписуєтесь.

Nostr розроблений для простоти та дозволяє стійке до цензури та глобально децентралізоване публікування у вебі. Давайте розберемо це трохи детальніше:

### Простий

Протокол базується на дуже простих і гнучких об'єктах `Event` (які передаються у вигляді звичайного JSON) і використовує стандартну криптографію з відкритим ключем для ключів і підписів. Це робить його легким для запуску ретрансляторів і створення клієнтів, а також забезпечує можливість розширення протоколу з часом.

### Стійкий

Оскільки Nostr не залежить від невеликої кількості довірених серверів для передачі або зберігання даних, він дуже стійкий. Протокол передбачає, що ретранслятори можуть зникати, і дозволяє користувачам підключатися та публікувати на довільну кількість ретрансляторів, які вони можуть змінювати з часом.

### Перевіряється

Оскільки облікові записи Nostr базуються на [криптографії з відкритим ключем](https://uk.wikipedia.org/wiki/Криптографія_з_відкритим_ключем), легко перевірити, що повідомлення дійсно було надіслано користувачем.

## Як я можу взяти участь?

Перегляньте наш [посібник](/uk/get-started), щоб почати!