---
title: Konfigurace balíčků npm pomocí souboru package.json
description: Zadejte verze balíčků npm pomocí souboru package.json
ms.date: 09/06/2018
ms.topic: conceptual
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 652ff7b0380fc03a3f9c8155a2f8696d9dfee5b9
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "67692373"
---
# <a name="packagejson-configuration"></a>Konfigurace package.json

Pokud vyvíjíte aplikaci Node.js s velkým množstvím balíčků npm, není neobvyklé spustit upozornění nebo chyby při vytváření projektu, pokud byl aktualizován jeden nebo více balíčků. Někdy výsledky konfliktu verze nebo verze balíčku byla zastaralá. Zde je několik rychlých tipů, které vám pomohou nakonfigurovat soubor [package.json](https://docs.npmjs.com/files/package.json) a pochopit, co se děje, když se zobrazí upozornění nebo chyby. Toto není kompletní průvodce *package.json* a je zaměřen pouze na npm balíček versioning.

Systém správy verzí balíčků npm má přísná pravidla. Formát verze následuje zde:

```
[major].[minor].[patch]
```

Řekněme, že máte balíček ve vaší aplikaci s verzí 5.2.1. Hlavní verze je 5, dílčí verze je 2 a oprava je 1.

* V hlavní verzi aktualizace balíček obsahuje nové funkce, které jsou zpětně nekompatibilní, to znamená, že narušují změny.
* V dílčí verzi aktualizace byly přidány nové funkce do balíčku, které jsou zpětně kompatibilní s předchozími verzemi balíčku.
* V aktualizaci opravy jsou zahrnuty jedny nebo více oprav chyb. Opravy chyb jsou vždy zpětně kompatibilní.

Stojí za zmínku, že některé npm balíček funkce mají závislosti. Chcete-li například použít novou funkci balíčku kompilátoru TypeScript (ts-loader) s webpackem, je možné, že budete muset také aktualizovat balíček webpack npm a balíček webpack-cli.

Chcete-li pomoci spravovat správu verzí balíčků, npm podporuje několik zápisů, které můžete použít v *package.json*. Tyto zápisy můžete použít k řízení typu aktualizací balíčků, které chcete ve své aplikaci přijmout.

Řekněme, že používáte React a je třeba zahrnout **reagovat** a **reagovat-dom** npm balíček. Můžete určit, že v souboru *package.json několika způsoby.* Můžete například určit použití přesné verze balíčku následujícím způsobem.

  ```json
  "dependencies": {
    "react": "16.4.2",
    "react-dom": "16.4.2",
  },
  ```

Pomocí předchozího zápisu npm vždy získá přesnou zadanou verzi 16.4.2.

Pomocí speciálního zápisu můžete omezit aktualizace aktualizací (opravy chyb). V tomto příkladu:

  ```json
  "dependencies": {
    "react": "~16.4.2",
    "react-dom": "~16.4.2",
  },
  ```

pomocí znaku tildy (~) řeknete npm, aby balíček aktualizoval pouze v případě, že je opraven. Takže npm může aktualizovat reagovat 16.4.2 na 16.4.3 (nebo 16.4.4, atd.), ale nebude akceptovat aktualizaci hlavní nebo dílčí verze. Takže 16.4.2 nebude aktualizován na 16.5.0.

Můžete také použít symbol stříšky (^) k určení, že npm může aktualizovat číslo dílčí verze.

  ```json
  "dependencies": {
    "react": "^16.4.2",
    "react-dom": "^16.4.2",
  },
  ```

Pomocí tohoto zápisu může npm aktualizovat reagovat 16.4.2 na 16.5.0 (nebo 16.5.1, 16.6.0, atd.), ale nebude akceptovat aktualizaci hlavní verze. Takže 16.4.2 nebude aktualizován na 17.0.0.

Když npm aktualizuje balíčky, generuje soubor *package-lock.json,* který obsahuje aktuální verze balíčků npm používané ve vaší aplikaci, včetně všech vnořených balíčků. Zatímco *package.json* řídí přímé závislosti pro vaši aplikaci, neřídí vnořené závislosti (jiné balíčky npm vyžadované konkrétním balíčkem npm). Soubor *package-lock.json* můžete použít ve vývojovém cyklu, pokud potřebujete zajistit, aby ostatní vývojáři a testeři používali přesné balíčky, které používáte, včetně vnořených balíčků. Další informace naleznete v [tématu package-lock.json](https://docs.npmjs.com/files/package-lock.json) v dokumentaci npm.

Pro Visual Studio soubor *package-lock.json* není přidán do projektu, ale najdete jej ve složce projektu.
