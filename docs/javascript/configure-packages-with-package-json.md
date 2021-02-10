---
title: Konfigurace balíčků npm pomocí package.js
description: Určení verzí balíčků npm pomocí package.js
ms.date: 09/06/2018
ms.topic: conceptual
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jmartens
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 891822d0b79cbfd53cf14229f11e003bf740c660
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99969487"
---
# <a name="packagejson-configuration"></a>Konfigurace package.json

Pokud vyvíjíte Node.js aplikaci s velkým počtem npm balíčků, není běžné spouštět upozornění nebo chyby při sestavování projektu, pokud byl aktualizován jeden nebo více balíčků. V některých případech je výsledkem konfliktu verze nebo verze balíčku je zastaralá. Tady je několik rychlých tipů, které vám pomůžou nakonfigurovat [package.jsv](https://docs.npmjs.com/files/package.json) souboru a pochopit, co se chystá, když se zobrazí upozornění nebo chyby. Nejedná se o kompletní průvodce *package.js* a zaměřuje se jenom na správu verzí balíčků npm.

Systém správy verzí balíčků npm má přísná pravidla. Formát verze je následující:

```
[major].[minor].[patch]
```

Řekněme, že máte v aplikaci balíček s verzí 5.2.1. Hlavní verze je 5, dílčí verze je 2 a oprava je 1.

* V případě aktualizace hlavní verze obsahuje balíček nové funkce, které jsou zpětně nekompatibilní, což znamená zásadní změny.
* V aktualizaci dílčí verze byly do balíčku přidány nové funkce, které jsou zpětně kompatibilní s dřívějšími verzemi balíčků.
* V aktualizaci opravy jsou součástí některé opravy chyb. Opravy chyb jsou vždy zpětně kompatibilní.

Je potřeba poznamenat, že některé funkce balíčku npm mají závislosti. Například chcete-li použít novou funkci balíčku kompilátoru TypeScript (TS-Loader) se sadou Webpack, je možné, že budete muset aktualizovat balíček npm a balíček Webpack pro rozhraní příkazového řádku.

Aby bylo možné spravovat správu verzí balíčků, npm podporuje několik zápisů, které můžete použít v *package.js*. Tyto zápisy můžete použít k řízení typu aktualizací balíčků, které chcete ve své aplikaci přijmout.

Řekněme, že používáte reakci a potřebujete zahrnout balíček **reagující** a **reagovat-DOM** npm. V *package.js* souboru můžete zadat několik způsobů. Například můžete zadat použití přesné verze balíčku následujícím způsobem.

  ```json
  "dependencies": {
    "react": "16.4.2",
    "react-dom": "16.4.2",
  },
  ```

Při použití předchozího zápisu bude npm vždycky mít přesně určenou verzi 16.4.2.

Pomocí zvláštního zápisu můžete omezit aktualizace aktualizací oprav (opravy chyb). V tomto příkladu:

  ```json
  "dependencies": {
    "react": "~16.4.2",
    "react-dom": "~16.4.2",
  },
  ```

použijete znak tilda (~) k tomu, aby nástroj npm při opravě balíčku aktualizoval pouze balíček. NPM může proto aktualizovat reakce 16.4.2 na 16.4.3 (nebo 16.4.4 atd.), ale nepřijme aktualizaci na hlavní nebo dílčí verzi. Proto se 16.4.2 nebude aktualizovat na 16.5.0.

Můžete také použít symbol stříšky (^), chcete-li určit, že npm může aktualizovat číslo dílčí verze.

  ```json
  "dependencies": {
    "react": "^16.4.2",
    "react-dom": "^16.4.2",
  },
  ```

Pomocí tohoto zápisu může npm aktualizovat reakce 16.4.2 na 16.5.0 (nebo 16.5.1, 16.6.0 atd.), ale nepřijme aktualizaci hlavní verze. Proto se 16.4.2 nebude aktualizovat na 17.0.0.

Když npm aktualizuje balíčky, vygeneruje *v souborupackage-lock.js* , ve kterém jsou uvedené skutečné verze balíčků npm používané ve vaší aplikaci, včetně všech vnořených balíčků. I když *package.jsk* řízení přímých závislostí vaší aplikace, neřídí vnořené závislosti (jiné balíčky npm vyžadované konkrétním balíčkem npm). Pokud potřebujete zajistit, aby jiní vývojáři a testeri používali přesné balíčky, které používáte, včetně vnořených balíčků, můžete použít *package-lock.jsv* souboru ve vývojovém cyklu. Další informace najdete v tématu [package-lock.js](https://docs.npmjs.com/files/package-lock.json) v dokumentaci k npm.

V případě sady Visual Studio se *package-lock.js* souboru do projektu nepřidá, ale můžete ho najít ve složce projektu.
