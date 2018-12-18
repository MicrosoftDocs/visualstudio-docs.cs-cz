---
title: Používání jiných webových prohlížečů v programových testech uživatelského rozhraní
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: f7301ef674e3ad3b940204be30bfffa878f88e45
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2018
ms.locfileid: "52895103"
---
# <a name="use-different-web-browsers-with-coded-ui-tests"></a>Používání jiných webových prohlížečů v programových testech uživatelského rozhraní

Programové testy UI mohou automatizovat testování webových aplikací tím, že zaznamenají vaše testy pomocí aplikace Internet Explorer. Potom můžete přizpůsobit test a přehrát jej buď pomocí aplikace Internet Explorer, nebo jiných typů prohlížečů pro tyto webové aplikace.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

Nejdřív nainstalujte [součásti Selenium pro programové uživatelského rozhraní pro různé prohlížeče testování](https://marketplace.visualstudio.com/items?itemName=AtinBansal.SeleniumcomponentsforCodedUICrossBrowserTesting).

## <a name="whats-supported-across-all-web-browsers"></a>Co je podporováno ve všech webových prohlížečích?

-   [Přidání vlastního kódu pro řízení funkcí](https://blogs.msdn.microsoft.com/devops/2012/12/09/coded-ui-test-configuring-search-properties-while-recording-on-internet-explorer/) například vlastnosti, vyhledávání a podprocesy přehrávání.

-   Automaticky otevíraná okna a dialogová okna

-   [Spustit základní JavaScript bez návratového typu](https://blogs.msdn.microsoft.com/devops/2013/01/18/introducing-javascript-execution-on-internetexplorer-and-crossbrowser-in-coded-ui-test/)

-   Hledat oblasti odolnosti (pomocí inteligentní shody) a [vylepšení výkonu](https://blogs.msdn.microsoft.com/devops/2012/01/31/guidelines-on-improving-performance-of-coded-ui-test-playback/)

## <a name="why-should-i-use-coded-ui-tests-across-multiple-web-browser-types"></a>Proč bych měl používat programové testy UI napříč několika typy webových prohlížečů?

Při testování webové aplikace pomocí různých typů webových prohlížečů můžete lépe emulovat zkušenosti vašich uživatelů s uživatelským rozhraním na různých prohlížečích. Aplikace může například obsahovat ovládací prvek nebo kód v aplikaci Internet Explorer, který není kompatibilní s jinými webovými prohlížeči. Spuštěním programových testů UI na různých prohlížečích můžete objevit a opravit jakýkoliv problém předtím, než ovlivní vaše zákazníky.

## <a name="how-do-i-record-and-play-back-coded-ui-tests-on-web-applications-using-the-supported-web-browsers"></a>Jak mohu zaznamenat a přehrát programové testy UI webových aplikacích pomocí podporovaných webových prohlížečů?

**Záznam:** Tvůrce programového testu UI musíte použít k záznamu testu webové aplikace pomocí aplikace Internet Explorer. Volitelně můžete pomocí předdefinované sady vlastností přidat kód pro ověření a přizpůsobení testovaných ovládacích prvků, jak byste to obvykle udělali v případě programových testů UI. Další informace najdete v tématu [automatizace uživatelského rozhraní k testování kódu](../test/use-ui-automation-to-test-your-code.md).

> [!NOTE]
> Programové testy UI nelze zaznamenat pomocí prohlížečů Google Chrome nebo Mozilla Firefox.

 **Přehrávání pomocí aplikace Internet Explorer:** při není explicitně zadán žádný prohlížeč, testy budou spuštěny v aplikaci Internet Explorer ve výchozím nastavení. Můžete explicitně uvést prohlížeče tak, že nastavíte **BrowserWindow.CurrentBrowser** vlastností v kódu testu. Pro aplikaci Internet Explorer by měla být tato vlastnost nastavená na **IE** nebo **aplikace Internet Explorer**.

 **Přehrávání pomocí webového prohlížeče Internet Explorer:** přehrát v prohlížečích, Internet Explorer, změňte vlastnost BrowserWindow.CurrentBrowser v kódu testu buď **Firefox** nebo **Chrome** .

 Chcete-li přehrát testy v prohlížečích než Internet Exploreru, je nutné nainstalovat **součásti Selenium pro programové testování uživatelského rozhraní pro různé prohlížeče**.

### <a name="install-selenium-components"></a>Instalace součástí Selenium

1.  Na **nástroje** nabídce zvolte **rozšíření a aktualizace**.

2.  V **rozšíření a aktualizace** dialogovém okně vyhledejte `Selenium components for Cross Browser Testing`.

3.  Zvýrazněte rozšíření a zvolte možnost **Stáhnout**.

    > [!TIP]
    > Můžete také stáhnout součásti Selenium pro programové testování uživatelského rozhraní pro různé prohlížeče z [tady](https://marketplace.visualstudio.com/items?itemName=AtinBansal.SeleniumcomponentsforCodedUICrossBrowserTesting).

Další informace o vytváření a používání kódované UI testy, naleznete v tématu [vytvořit kódované testy uživatelského rozhraní](../test/use-ui-automation-to-test-your-code.md).

### <a name="enable-debugging"></a>Povolení ladění

Chcete-li povolit ladění webové aplikace, je nutné dokončit následující možnosti konfigurace:

1.  Povolit volbu Pouze vlastní kód:

    1.  Na **nástroje** nabídce zvolte **možnosti** a klikněte na tlačítko **ladění**.

    2.  Vyberte **povolit volbu pouze vlastní kód**.

2.  Zakázání výjimek CLR:

    1.  Na **ladění** nabídce zvolte **výjimky**.

    2.  Pro **výjimky modulu Common Language Runtime**, zrušte zaškrtnutí políčka **uživatelem neošetřené**.

Pokud nevidíte možnost změnit `BrowserWindow.CurrentBrowser` v programovém testu uživatelského rozhraní, může pomocí verze sady Visual Studio, který nepodporuje programové testy UI pomocí různých webových prohlížečů. Pokud chcete použít tyto programové testy UI, musíte použít edici sady Visual Studio Enterprise.

Tady jsou některé další možnosti, které byste měli vědět:

- Webový prohlížeč Apple Safari není podporován.

- Akce spuštění webového prohlížeče musí být součástí programového testu UI.

   Pokud je již webový prohlížeč otevřen a chcete v něm spustit příslušné kroky, aniž byste používali aplikaci Internet Explorer, přehrávání selže. Je proto vhodné zahrnout spuštění webového prohlížeče jako součást programových testů UI.

- Automatizace akcí UI specifických podle prohlížeče, jako je maximalizace, minimalizace a obnovení, není podporována.

## <a name="tips"></a>Tipy

Můžete nakonfigurovat výstup tak, aby obsahoval snímky obrazovky v kódovaných protokolech UI. Uděláte to tak, je nutné nastavit některá nastavení konfigurace *QTAgent32.exe.config* souboru. Ve výchozím nastavení je tento soubor nainstalován v následujícím umístění:

*% ProgramFiles (x86) %\Microsoft Visual Studio\2017\Enterprise\Common7\IDE*

Nastavte následující hodnoty:

- `EqtTraceLevel` v `system.diagnostics` oddílu.

- `<add name="EqtTraceLevel" value="4" />`

   Tím, že nastavíte hodnotu 3 nebo vyšší, budou snímky obrazovky pořízeny pro každou akci. Pokud je hodnota nastavena na 1 nebo 2, budou snímky obrazovky pořízeny pouze pro chybové akce.

Další informace najdete v tématu [analyzovat kódované testy uživatelského rozhraní pomocí protokolů z programových testů uživatelského rozhraní](../test/analyzing-coded-ui-tests-using-coded-ui-test-logs.md).

## <a name="video-resources"></a>Grafické prostředky

 [Záznam v aplikaci Internet Explorer a přehrávání všude](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!183&authkey=!ANqaLtCZbtJrImU)

 [Autor testů pro různé prohlížeče pomocí Tvůrce programového testu uživatelského rozhraní](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!184&authkey=!AKG8CSow_qmeTq8)

 [Autor testů pro různé prohlížeče pomocí prostého ručního kódování bez mapování uživatelského rozhraní](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!186&authkey=!AJaEvxJnsefyAT4)

 [Spuštění testů pro různé prohlížeče postupně v různé prohlížeče](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!187&authkey=!ADI8eCQkxHnpOR8)

 [Řešení potíží pro různé prohlížeče selhání testu](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!182&authkey=!AEpS48i295B49FI)

## <a name="see-also"></a>Viz také:

- [Použití automatizace uživatelského rozhraní k testování kódu](../test/use-ui-automation-to-test-your-code.md)
- [Podporované konfigurace a platformy pro programové testy uživatelského rozhraní a zaznamenávání akcí](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
- [Analýza programových testů uživatelského rozhraní pomocí protokolů z programových testů uživatelského rozhraní](../test/analyzing-coded-ui-tests-using-coded-ui-test-logs.md)
