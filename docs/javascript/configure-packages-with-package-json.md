---
title: Nakonfigurovat balíčky npm pro package.json
description: Zadejte soubor package.json pomocí verze balíčku npm
ms.custom: ''
ms.date: 09/06/2018
ms.technology: vs-nodejs
ms.topic: conceptual
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: douge
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 711d7b65eb329e844fedb0148006cacb1c7a0ebf
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2018
ms.locfileid: "50219092"
---
# <a name="packagejson-configuration"></a>Konfigurace package.json

Pokud vyvíjíte aplikace v Node.js s velkým množstvím balíčky npm, není nic neobvyklého, když dojde k upozornění a chyby při sestavení projektu, pokud jeden nebo více balíčků se aktualizovala. V některých případech se už nepoužívá výsledky konfliktu verze nebo verze balíčku. Tady je několik tipů, které vám pomohou nakonfigurovat vaše [package.json](https://docs.npmjs.com/files/package.json) souboru a pochopit, co se děje při zobrazení upozornění a chyby. Toto není kompletní pokyny k *package.json* a se zaměřuje pouze na Správa verzí balíčků npm.

Systém správy verzí balíčků npm se přísná pravidla. Formát verze následující tady:

    [major].[minor].[patch]

Řekněme, že máte ve své aplikaci s verzí 5.2.1 balíček. Hlavní verze je 5, dílčí verze je 2 a opravy je 1.

* V hlavní verze aktualizace balíček obsahuje nové funkce, které jsou zpětně nekompatibilní, který je, rozbíjející změny.
* Vedlejší verze aktualizace, byly přidány nové funkce do balíčku, které jsou zpětně kompatibilní se staršími verzemi balíčku.
* V aktualizaci opravu jsou zahrnuty jeden nebo více oprav chyb. Opravy chyb jsou vždycky zpětně kompatibilní.

Je vhodné poznamenat, že některé funkce balíček npm závislostmi. Například webpacku používat nové funkce balíčku kompilátor TypeScript (ts zaváděcího programu), je možné že také je třeba aktualizovat balíčky npm webpacku a webpacku rozhraní příkazového řádku.

Ke správě Správa verzí balíčků npm podporuje několik zápisy, které můžete použít v *package.json*. Tato notace můžete řídit typ balíčku aktualizací, které chcete použít ve vaší aplikaci.

Řekněme, že používáte React a musí obsahovat **react** a **react-dom** balíčku npm. V několika způsoby může určit, že vaše *package.json* souboru. Například následujícím způsobem můžete použít přesnou verzi balíčku.

  ```json
  "dependencies": {
    "react": "16.4.2",
    "react-dom": "16.4.2",
  },
  ```

Předchozí notaci, bude npm vždy získat přesnou verzi zadanou, 16.4.2.

Speciální zápisu můžete použít k omezení aktualizace aktualizace (opravy chyb). V tomto příkladu:

  ```json
  "dependencies": {
    "react": "~16.4.2",
    "react-dom": "~16.4.2",
  },
  ```

Znak tilda (~) použijete říct npm pouze aktualizace balíčku, když je opravit. Proto npm můžete aktualizovat react 16.4.2 k 16.4.3 (nebo 16.4.4, atd.), ale nebude přijímat aktualizace hlavních nebo vedlejších verzí. Proto se 16.5.0 neaktualizují 16.4.2.

Symbol stříšky (^) můžete také použít k určení, že npm můžete aktualizovat číslo podverze.

  ```json
  "dependencies": {
    "react": "^16.4.2",
    "react-dom": "^16.4.2",
  },
  ```

Použití tohoto zápisu, npm můžete aktualizovat react 16.4.2 k 16.5.0 (nebo 16.5.1, 16.6.0, atd.), ale nebude přijímat aktualizace hlavní verze. Proto se 17.0.0 neaktualizují 16.4.2.

Balíčky aktualizací npm, generuje *balíčku lock.json* soubor, který obsahuje seznam verzí balíčku npm skutečné používaných v aplikaci, včetně všech vnořených balíčků. Zatímco *package.json* ovládací prvky přímé závislosti pro svou aplikaci neřídí vnořené závislosti (ostatní balíčky npm vyžaduje balíček konkrétní npm). Můžete použít *balíčku lock.json* souboru v cyklu vývoje, pokud je třeba Ujistěte se, že ostatní vývojáři a testeři používáte přesné balíčky, které používáte, včetně vnořených balíčků. Další informace najdete v tématu [balíčku lock.json](https://docs.npmjs.com/files/package-lock.json) v dokumentaci k npm.

Pro Visual Studio *balíčku lock.json* soubor se nepřidal do projektu, ale najdete ve složce projektu.
