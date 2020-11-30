---
title: Používání jiných webových prohlížečů v programových testech uživatelského rozhraní
description: Naučte se přizpůsobit svůj test a přehrát ho pomocí různých prohlížečů pro vaše webové aplikace.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 6baddaeac3fdea3d27f60722e728df209bfd768d
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/30/2020
ms.locfileid: "96330027"
---
# <a name="use-different-web-browsers-with-coded-ui-tests"></a>Použití různých webových prohlížečů s programovým testem uživatelského rozhraní

Programové testy UI mohou automatizovat testování webových aplikací tím, že zaznamenají vaše testy pomocí aplikace Internet Explorer. Potom můžete přizpůsobit test a přehrát jej buď pomocí aplikace Internet Explorer, nebo jiných typů prohlížečů pro tyto webové aplikace.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

Nejprve nainstalujte [komponenty selen pro programové testování uživatelského rozhraní pro různé prohlížeče](https://marketplace.visualstudio.com/items?itemName=AtinBansal.SeleniumcomponentsforCodedUICrossBrowserTesting).

## <a name="whats-supported-across-all-web-browsers"></a>Co je podporováno ve všech webových prohlížečích?

- [Přidejte vlastní kód pro řídící funkce](https://devblogs.microsoft.com/devops/coded-ui-test-configuring-search-properties-while-recording-on-internet-explorer/) , jako jsou vlastnosti, hledání a čekání na přehrávání.

- Automaticky otevíraná okna a dialogová okna

- [Spustit základní JavaScript bez návratového typu](https://devblogs.microsoft.com/devops/introducing-javascript-execution-on-internetexplorer-and-crossbrowser-in-coded-ui-test/)

- Prohledat odolnost (pomocí inteligentní shody) a [vylepšení výkonu](https://devblogs.microsoft.com/devops/guidelines-on-improving-performance-of-coded-ui-test-playback/)

## <a name="why-should-i-use-coded-ui-tests-across-multiple-web-browser-types"></a>Proč bych měl používat programové testy UI napříč několika typy webových prohlížečů?

Při testování webové aplikace pomocí různých typů webových prohlížečů můžete lépe emulovat zkušenosti vašich uživatelů s uživatelským rozhraním na různých prohlížečích. Aplikace může například obsahovat ovládací prvek nebo kód v aplikaci Internet Explorer, který není kompatibilní s jinými webovými prohlížeči. Spuštěním programových testů UI na různých prohlížečích můžete objevit a opravit jakýkoliv problém předtím, než ovlivní vaše zákazníky.

## <a name="how-do-i-record-and-play-back-coded-ui-tests-on-web-applications-using-the-supported-web-browsers"></a>Jak mohu zaznamenat a přehrát programové testy UI webových aplikacích pomocí podporovaných webových prohlížečů?

**Záznam:** Chcete-li zaznamenat test webové aplikace pomocí aplikace Internet Explorer, je nutné použít Tvůrce programového testu uživatelského rozhraní. Volitelně můžete pomocí předdefinované sady vlastností přidat kód pro ověření a přizpůsobení testovaných ovládacích prvků, jak byste to obvykle udělali v případě programových testů UI. Další informace naleznete v tématu [použití automatizace uživatelského rozhraní k otestování kódu](../test/use-ui-automation-to-test-your-code.md).

> [!NOTE]
> Programové testy UI nelze zaznamenat pomocí prohlížečů Google Chrome nebo Mozilla Firefox.

**Přehrávání pomocí aplikace Internet Explorer:** Pokud není explicitně zadán žádný prohlížeč, testy se ve výchozím nastavení spustí v aplikaci Internet Explorer. Můžete explicitně uvést prohlížeč, který se má použít, nastavením vlastnosti **BrowserWindow. CurrentBrowser** v kódu testu. Pro Internet Explorer by tato vlastnost měla být nastavená na **IE** nebo **Internet Explorer**.

**Hraní webových prohlížečů, které nejsou v Internet Exploreru:** Chcete-li se vrátit k webovým prohlížečům, které nejsou v aplikaci Internet Explorer, změňte vlastnost BrowserWindow. CurrentBrowser v kódu testu na **Firefox** nebo **Chrome**.

Chcete-li přehrát testy v webových prohlížečích bez prohlížeče IE, je nutné nainstalovat **komponenty selen pro testování programového uživatelského rozhraní pro různé prohlížeče**.

### <a name="install-selenium-components"></a>Nainstalovat komponenty selenu

::: moniker range="vs-2017"

1. V nabídce **nástroje** vyberte **rozšíření a aktualizace**.

2. V dialogovém okně **rozšíření a aktualizace** vyhledejte `Selenium components for Cross Browser Testing` .

::: moniker-end

::: moniker range=">=vs-2019"

1. V nabídce **rozšíření** vyberte **Spravovat rozšíření**.

2. V dialogovém okně **Spravovat rozšíření** vyhledejte `Selenium components for Cross Browser Testing` .

::: moniker-end

3. Zvýrazněte rozšíření a klikněte na tlačítko **Stáhnout**.

    > [!TIP]
    > Komponenty selenu můžete také stáhnout pro testování programového uživatelského rozhraní v různých [prohlížečích.](https://marketplace.visualstudio.com/items?itemName=AtinBansal.SeleniumcomponentsforCodedUICrossBrowserTesting)

Další informace o vytváření a používání programových testů UI naleznete v tématu [Create Code test UI](../test/use-ui-automation-to-test-your-code.md).

### <a name="enable-debugging"></a>Povolení ladění

Chcete-li povolit ladění webové aplikace, je nutné dokončit následující možnosti konfigurace:

1. Povolit volbu Pouze vlastní kód:

    1. V nabídce **nástroje** zvolte **Možnosti** a pak zvolte možnost **ladění**.

    2. Vyberte **povolit pouze můj kód**.

2. Zakázání výjimek CLR:

    1. V nabídce **ladění** vyberte možnost **výjimky**.

    2. V případě **výjimek modulu CLR (Common Language Runtime)** zrušte kontrolu **neošetřeného uživatelem**.

Pokud nevidíte možnost změny v programovém `BrowserWindow.CurrentBrowser` testu UI, možná budete používat verzi sady Visual Studio, která nepodporuje programové testy UI pomocí různých webových prohlížečů. Chcete-li použít tyto programové testy uživatelského rozhraní, je nutné použít edici Visual Studio Enterprise.

Tady je několik dalších věcí, které byste měli znát:

- Webový prohlížeč Apple Safari není podporován.

- Akce spuštění webového prohlížeče musí být součástí programového testu UI.

   Pokud je již webový prohlížeč otevřen a chcete v něm spustit příslušné kroky, aniž byste používali aplikaci Internet Explorer, přehrávání selže. Je proto vhodné zahrnout spuštění webového prohlížeče jako součást programových testů UI.

- Automatizace akcí UI specifických podle prohlížeče, jako je maximalizace, minimalizace a obnovení, není podporována.

## <a name="tips"></a>Tipy

Můžete nakonfigurovat výstup tak, aby obsahoval snímky obrazovky v kódovaných protokolech UI. K tomu je potřeba nastavit některá nastavení konfigurace v souboru *QTAgent32.exe.config* . Ve výchozím nastavení je tento soubor nainstalován v následujícím umístění:

*% ProgramFiles (x86)% \ Microsoft Visual Studio\2017\Enterprise\Common7\IDE*

Nastavte následující hodnoty:

- `EqtTraceLevel` v `system.diagnostics` části.

- `<add name="EqtTraceLevel" value="4" />`

   Když nastavíte hodnotu na 3 nebo vyšší, snímky obrazovky se vyberou pro každou akci. Pokud je hodnota nastavena na 1 nebo 2, budou snímky obrazovky pořízeny pouze pro chybové akce.

Další informace naleznete v tématu [Analýza programových testů uživatelského rozhraní pomocí protokolů kódovaného testu uživatelského rozhraní](../test/analyzing-coded-ui-tests-using-coded-ui-test-logs.md).

## <a name="video-resources"></a>Zdroje informací ve formě videí

[Záznam v aplikaci IE a přehrávání všude](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!183&authkey=!ANqaLtCZbtJrImU)

[Vytváření testů pro různé prohlížeče pomocí Tvůrce programového testu uživatelského rozhraní](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!184&authkey=!AKG8CSow_qmeTq8)

[Vytváření testů pro různé prohlížeče pomocí jednoduchých ručního kódování bez mapování uživatelského rozhraní](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!186&authkey=!AJaEvxJnsefyAT4)

[Spuštění testů pro různé prohlížeče postupně na více prohlížečích](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!187&authkey=!ADI8eCQkxHnpOR8)

[Řešení potíží se selháním testů pro různé prohlížeče](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!182&authkey=!AEpS48i295B49FI)

## <a name="see-also"></a>Viz také

- [Použití automatizace uživatelského rozhraní k otestování kódu](../test/use-ui-automation-to-test-your-code.md)
- [Podporované konfigurace a platformy pro programové testy uživatelského rozhraní a záznamy akcí](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
- [Analýza programových testů uživatelského rozhraní pomocí protokolů kódovaného testu uživatelského rozhraní](../test/analyzing-coded-ui-tests-using-coded-ui-test-logs.md)
