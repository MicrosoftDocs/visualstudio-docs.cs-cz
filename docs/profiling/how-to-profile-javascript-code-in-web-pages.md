---
title: 'Postup: Profil javascriptového kódu na webových stránkách | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- JavaScript performance profiling
- Profiling Tools,JavaScript
- web site performance profiling
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 07c628b3c1f0be1c7ecc615dcae44f7736aa884e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74775303"
---
# <a name="how-to-profile-javascript-code-in-web-pages"></a>Postup: Profil javascriptového kódu na webových stránkách

Nástroje pro profilování sady Visual Studio mohou shromažďovat údaje [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] o výkonu pro kód Jazyka JavaScript, který se spouští ve webové aplikaci, libovolné webové stránce nebo v aplikaci JavaScript pomocí metody profilování instrumentace. Vyžaduje aplikaci Internet Explorer 8 nebo novější.

> [!WARNING]
> Chcete-li profilovat JavaScript v aplikacích UPW, přečtěte si téma [JavaScript Memory](../profiling/javascript-memory.md)

Průvodce profilováním můžete použít k vytvoření relace výkonu. Zadejte metodu instrumentace a pak určete volbu profilování javascriptu na stránce Instrumentace dialogového okna vlastností relace výkonu.

Když zadáte profilování javascriptu, profilování javascriptového jazyka, [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] který se spustí v prohlížeči, i kód, který se spustí na serveru, se profilují.

- Pro [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] webovou aplikaci jsou profilovány jak kód Jazyka [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] JavaScript, který se spouští v prohlížeči, tak kód, který se spouští na serveru.

- Pro libovolnou webovou stránku je profilován kód JavaScriptu, který se spustí v prohlížeči.

## <a name="to-profile-javascript-in-an-aspnet-web-application-project"></a>Profilování JavaScriptu v projektu webové aplikace ASP.NET

1. Otevřete [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] webový projekt v sadě Visual Studio.

2. V nabídce **Analyzovat** klepněte na tlačítko **Spustit Průvodce výkonem**.

3. Na první stránce Průvodce výkonem zadejte metodu profilování **instrumentace** a klepněte na tlačítko **Další**.

4. Na druhé stránce průvodce zkontrolujte, zda je v seznamu cílů vybrán aktuální projekt, a klepněte na tlačítko **Další.**

5. Na třetí stránce průvodce zaškrtněte políčko **Profil JavaScriptu** a klepněte na tlačítko **Další**.

6. Na čtvrté stránce průvodce spusťte webovou aplikaci v prohlížeči klepnutím na **tlačítko Dokončit.**

7. Využijte funkce, které chcete profilovat.

8. Chcete-li ukončit relaci profilování, zavřete prohlížeč.

### <a name="to-profile-javascript-in-individual-web-pages-or-a-javascript-applications"></a>Profilování JavaScriptu na jednotlivých webových stránkách nebo v javascriptových aplikacích

1. Otevřete sadu Visual Studio.

2. V nabídce **Analyzovat** klepněte na tlačítko **Spustit Průvodce výkonem**.

3. Na první stránce Průvodce výkonem zadejte metodu profilování **instrumentace** a klepněte na tlačítko **Další**.

4. Na druhé stránce průvodce klikněte na ASP.NET nebo JavaScript a potom klikněte na **Další.**

5. Na třetí stránce průvodce:

    1. Do pole Co bude **spuštěna adresa URL nebo cesta, která bude spuštěna.**

    2. Zaškrtněte políčko **Profile JavaScript** a klepněte na tlačítko **Další**.

6. Na čtvrté stránce průvodce spusťte webovou stránku v prohlížeči klepnutím na **tlačítko Dokončit.**

7. Využijte funkce, které chcete profilovat.

8. Chcete-li ukončit relaci profilování, zavřete prohlížeč.
