---
title: 'Postupy: profilování kódu JavaScriptu na webových stránkách | Microsoft Docs'
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
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74775303"
---
# <a name="how-to-profile-javascript-code-in-web-pages"></a>Postupy: profilování kódu JavaScriptu na webových stránkách

Visual Studio Nástroje pro profilaci může shromažďovat údaje o výkonu pro kód JavaScriptu, který se spouští v [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] webové aplikaci, libovolné webové stránce nebo aplikaci JavaScriptu pomocí metody profilace instrumentace. Vyžaduje aplikaci Internet Explorer 8 nebo novější.

> [!WARNING]
> Profilace JavaScriptu v aplikacích pro UWP najdete v tématu [paměť JavaScriptu](../profiling/javascript-memory.md) .

Můžete použít Průvodce profilací k vytvoření výkonnostní relace. Zadejte metodu instrumentace a pak určete možnost profilace JavaScriptu na stránce instrumentace v dialogovém okně Vlastnosti pro relaci výkonu.

Když zadáte profilaci JavaScriptu, budou profilace JavaScriptu spouštěná v prohlížeči i kód [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], který se spouští na serveru.

- Pro [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] webové aplikace se profiluje kód JavaScriptu, který se spouští v prohlížeči, a kód [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], který se spouští na serveru.

- V případě libovolné webové stránky je kód JavaScriptu, který se spouští v prohlížeči, profilace.

## <a name="to-profile-javascript-in-an-aspnet-web-application-project"></a>Profilace JavaScriptu v projektu webové aplikace ASP.NET

1. Otevřete [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] webový projekt v aplikaci Visual Studio.

2. V nabídce **analyzovat** klikněte na možnost **Spustit Průvodce výkonem**.

3. Na první stránce Průvodce výkonem zadejte metodu profilace **instrumentace** a potom klikněte na tlačítko **Další**.

4. Na druhé stránce průvodce se ujistěte, že je v seznamu cílů vybraný aktuální projekt, a pak klikněte na **Další.**

5. Na třetí stránce průvodce vyberte zaškrtávací políčko **profil JavaScript** a pak klikněte na **Další**.

6. Na čtvrté stránce průvodce kliknutím na tlačítko **Dokončit** spusťte webovou aplikaci v prohlížeči.

7. Využijte funkci, kterou chcete profilovat.

8. Chcete-li ukončit relaci profilování, zavřete prohlížeč.

### <a name="to-profile-javascript-in-individual-web-pages-or-a-javascript-applications"></a>Profilace JavaScriptu na jednotlivých webových stránkách nebo v aplikacích JavaScriptu

1. Otevřete Visual Studio.

2. V nabídce **analyzovat** klikněte na možnost **Spustit Průvodce výkonem**.

3. Na první stránce Průvodce výkonem zadejte metodu profilace **instrumentace** a potom klikněte na tlačítko **Další**.

4. Na druhé stránce průvodce klikněte na aplikaci ASP.NET nebo JavaScript a potom klikněte na tlačítko **Další.**

5. Na třetí stránce průvodce:

    1. Zadejte adresu URL stránky v poli **Jaká adresa URL nebo cesta spustí vaši aplikaci** .

    2. Zaškrtněte políčko **profil JavaScript** a potom klikněte na tlačítko **Další**.

6. Na čtvrté stránce průvodce kliknutím na tlačítko **Dokončit** otevřete webovou stránku v prohlížeči.

7. Využijte funkci, kterou chcete profilovat.

8. Chcete-li ukončit relaci profilování, zavřete prohlížeč.
