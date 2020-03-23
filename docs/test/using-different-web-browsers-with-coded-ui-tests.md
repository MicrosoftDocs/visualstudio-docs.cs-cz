---
title: Používání jiných webových prohlížečů v programových testech uživatelského rozhraní
ms.date: 11/04/2016
ms.topic: conceptual
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 104bdcc7a3f609456d521e710ac6ec2aeda2bb75
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75585571"
---
# <a name="use-different-web-browsers-with-coded-ui-tests"></a>Použití různých webových prohlížečů s kódovými testy uživatelského rozhraní

Programové testy UI mohou automatizovat testování webových aplikací tím, že zaznamenají vaše testy pomocí aplikace Internet Explorer. Potom můžete přizpůsobit test a přehrát jej buď pomocí aplikace Internet Explorer, nebo jiných typů prohlížečů pro tyto webové aplikace.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

Nejprve nainstalujte [součásti Selenu pro kódované testování mezi prohlížeči .](https://marketplace.visualstudio.com/items?itemName=AtinBansal.SeleniumcomponentsforCodedUICrossBrowserTesting)

## <a name="whats-supported-across-all-web-browsers"></a>Co je podporováno ve všech webových prohlížečích?

- [Přidejte vlastní kód pro řízení funkcí,](https://devblogs.microsoft.com/devops/coded-ui-test-configuring-search-properties-while-recording-on-internet-explorer/) jako jsou vlastnosti, vyhledávání a číšníci přehrávání.

- Automaticky otevíraná okna a dialogová okna

- [Spuštění základního JavaScriptu bez návratového typu](https://devblogs.microsoft.com/devops/introducing-javascript-execution-on-internetexplorer-and-crossbrowser-in-coded-ui-test/)

- Odolnost vyhledávání (pomocí inteligentního shodu) a [vylepšení výkonu](https://devblogs.microsoft.com/devops/guidelines-on-improving-performance-of-coded-ui-test-playback/)

## <a name="why-should-i-use-coded-ui-tests-across-multiple-web-browser-types"></a>Proč bych měl používat programové testy UI napříč několika typy webových prohlížečů?

Při testování webové aplikace pomocí různých typů webových prohlížečů můžete lépe emulovat zkušenosti vašich uživatelů s uživatelským rozhraním na různých prohlížečích. Aplikace může například obsahovat ovládací prvek nebo kód v aplikaci Internet Explorer, který není kompatibilní s jinými webovými prohlížeči. Spuštěním programových testů UI na různých prohlížečích můžete objevit a opravit jakýkoliv problém předtím, než ovlivní vaše zákazníky.

## <a name="how-do-i-record-and-play-back-coded-ui-tests-on-web-applications-using-the-supported-web-browsers"></a>Jak mohu zaznamenat a přehrát programové testy UI webových aplikacích pomocí podporovaných webových prohlížečů?

**Záznam:** K zaznamenání testu webové aplikace pomocí aplikace Internet Explorer je nutné použít Tvůrce testů programového uživatelského rozhraní. Volitelně můžete pomocí předdefinované sady vlastností přidat kód pro ověření a přizpůsobení testovaných ovládacích prvků, jak byste to obvykle udělali v případě programových testů UI. Další informace naleznete v [tématu Použití automatizace uživatelského rozhraní k testování kódu](../test/use-ui-automation-to-test-your-code.md).

> [!NOTE]
> Programové testy UI nelze zaznamenat pomocí prohlížečů Google Chrome nebo Mozilla Firefox.

**Přehrání v aplikaci Internet Explorer:** Pokud není explicitně zadán žádný prohlížeč, testy budou ve výchozím nastavení spuštěny v aplikaci Internet Explorer. Můžete explicitně uvést prohlížeč, který má být použit nastavením **BrowserWindow.CurrentBrowser** vlastnost v testovacíkód. V aplikaci Internet Explorer by tato vlastnost měla být nastavena na **aplikaci Internet** Explorer nebo **Internet Explorer**.

**Přehrávání s webovými prohlížeči, které nejsou v aplikaci Internet Explorer:** Chcete-li přehrávat webové prohlížeče jiné než Internet Explorer, změňte vlastnost BrowserWindow.CurrentBrowser v testovacím kódu na **Firefox** nebo **Chrome**.

Chcete-li přehrát testy na webových prohlížečích **Selenium components for Coded UI Cross Browser Testing**jiných než Internet,...

### <a name="install-selenium-components"></a>Instalace součástí selenu

::: moniker range="vs-2017"

1. V nabídce **Nástroje** zvolte **Rozšíření a aktualizace**.

2. V dialogovém okně **Rozšíření a** `Selenium components for Cross Browser Testing`aktualizace vyhledejte .

::: moniker-end

::: moniker range=">=vs-2019"

1. V nabídce **Rozšíření** zvolte **Spravovat rozšíření**.

2. V dialogovém okně **Spravovat** rozšíření `Selenium components for Cross Browser Testing`vyhledejte .

::: moniker-end

3. Zvýrazněte rozšíření a zvolte **Stáhnout**.

    > [!TIP]
    > Můžete si také stáhnout komponenty Selen pro kódované UI Cross Browser Testování [zde](https://marketplace.visualstudio.com/items?itemName=AtinBansal.SeleniumcomponentsforCodedUICrossBrowserTesting).

Další informace o vytváření a používání kódovaných testů ui naleznete [v tématu Vytvoření kódovaných testů ui](../test/use-ui-automation-to-test-your-code.md).

### <a name="enable-debugging"></a>Povolení ladění

Chcete-li povolit ladění webové aplikace, je nutné dokončit následující možnosti konfigurace:

1. Povolit volbu Pouze vlastní kód:

    1. V nabídce **Nástroje** zvolte **Možnosti** a pak zvolte **Ladění**.

    2. Vyberte **povolit pouze můj kód**.

2. Zakázání výjimek CLR:

    1. V nabídce **Ladění** zvolte **Výjimky**.

    2. U **běžných výjimek za běhu jazyka**odškrtnete **políčko Neošetřený uživatel**.

Pokud nevidíte možnost změny `BrowserWindow.CurrentBrowser` v programovém testu uživatelského rozhraní, je možné, že používáte verzi sady Visual Studio, která nepodporuje kódované testy uživatelského rozhraní pomocí různých webových prohlížečů. Chcete-li použít takové kódované testy ui, musíte použít Visual Studio Enterprise edition.

Zde jsou některé další věci, které byste měli vědět:

- Webový prohlížeč Apple Safari není podporován.

- Akce spuštění webového prohlížeče musí být součástí programového testu UI.

   Pokud je již webový prohlížeč otevřen a chcete v něm spustit příslušné kroky, aniž byste používali aplikaci Internet Explorer, přehrávání selže. Je proto vhodné zahrnout spuštění webového prohlížeče jako součást programových testů UI.

- Automatizace akcí UI specifických podle prohlížeče, jako je maximalizace, minimalizace a obnovení, není podporována.

## <a name="tips"></a>Tipy

Můžete nakonfigurovat výstup tak, aby obsahoval snímky obrazovky v kódovaných protokolech UI. Chcete-li tak učinit, musíte nastavit některá nastavení konfigurace v souboru *QTAgent32.exe.config.* Ve výchozím nastavení je tento soubor nainstalován v následujícím umístění:

*%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE*

Nastavte následující hodnoty:

- `EqtTraceLevel`v `system.diagnostics` sekci.

- `<add name="EqtTraceLevel" value="4" />`

   Nastavením hodnoty na 3 nebo vyšší, screenshoty jsou pořízeny pro každou akci. Pokud je hodnota nastavena na 1 nebo 2, budou snímky obrazovky pořízeny pouze pro chybové akce.

Další informace naleznete v [tématu Analýza kódovaných testů ui pomocí kódovaných protokolů testů ui](../test/analyzing-coded-ui-tests-using-coded-ui-test-logs.md).

## <a name="video-resources"></a>Video zdroje

[Záznam na IE a přehrávání všude](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!183&authkey=!ANqaLtCZbtJrImU)

[Autor křížové testy prohlížeče s kódované UI test builder](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!184&authkey=!AKG8CSow_qmeTq8)

[Autor cross browser testy pomocí plain hand kódování bez UI map](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!186&authkey=!AJaEvxJnsefyAT4)

[Spouštění testů mezi prohlížeči postupně ve více prohlížečích](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!187&authkey=!ADI8eCQkxHnpOR8)

[Poradce při potížích s chybami testů mezi prohlížeči](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!182&authkey=!AEpS48i295B49FI)

## <a name="see-also"></a>Viz také

- [Testování kódu pomocí automatizace uživatelského rozhraní](../test/use-ui-automation-to-test-your-code.md)
- [Podporované konfigurace a platformy pro kódované testy a záznamy akcí](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
- [Analýza kódovaných testů ui pomocí kódovaných protokolů testů ui](../test/analyzing-coded-ui-tests-using-coded-ui-test-logs.md)
