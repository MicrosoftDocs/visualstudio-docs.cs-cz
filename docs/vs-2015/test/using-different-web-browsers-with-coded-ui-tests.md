---
title: Používání různých webových prohlížečů s programovým testem uživatelského rozhraní | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: a859595f-6517-43f2-9d61-c706cb55a388
caps.latest.revision: 25
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5234dddad13ccb52cc653a68ad1c35370a4eae18
ms.sourcegitcommit: da5ebc29544fdbdf625ab4922c9777faf2bcae4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/29/2020
ms.locfileid: "82586331"
---
# <a name="using-different-web-browsers-with-coded-ui-tests"></a>Používání jiných webových prohlížečů v programových testech uživatelského rozhraní
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Programové testy UI mohou automatizovat testování webových aplikací tím, že zaznamenají vaše testy pomocí aplikace Internet Explorer. Potom můžete přizpůsobit test a přehrát jej buď pomocí aplikace Internet Explorer, nebo jiných typů prohlížečů pro tyto webové aplikace.

 **Požadavky**

- Visual Studio Enterprise

- Operační systémy:

  - Microsoft Windows 7

  - Microsoft Windows 8

  - Microsoft Windows Server 2008 R2 SP1

- Verze webového prohlížeče:

  - Windows Internet Explorer 9

  - Windows Internet Explorer 10

  - V případě podporovaných verzí aplikace Mozilla Firefox a Google Chrome můžete přejít [sem](https://marketplace.visualstudio.com/items?itemName=AtinBansal.SeleniumcomponentsforCodedUICrossBrowserTesting) .

- Nainstalujte [komponenty selen pro testování programového uživatelského rozhraní pro více prohlížečů](https://marketplace.visualstudio.com/items?itemName=AtinBansal.SeleniumcomponentsforCodedUICrossBrowserTesting).

  **Co je podporováno ve všech webových prohlížečích?**

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

#### <a name="installing-selenium-components"></a>Instalace součástí Selenium

1. V nabídce **nástroje** vyberte **rozšíření a aktualizace**.

2. V dialogovém okně rozšíření a aktualizace vyhledejte `Selenium components for Cross Browser Testing`.

3. Zvýrazněte rozšíření a klikněte na tlačítko **Stáhnout**.

   > [!TIP]
   > Komponenty selenu můžete také stáhnout pro testování programového uživatelského rozhraní v různých [prohlížečích.](https://marketplace.visualstudio.com/items?itemName=AtinBansal.SeleniumcomponentsforCodedUICrossBrowserTesting)

   Další informace o vytváření a používání programových testů UI naleznete v tématu vytváření programových [testů uživatelského rozhraní](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate).

### <a name="enable-debugging"></a>Povolení ladění
 Chcete-li povolit ladění webové aplikace, je nutné dokončit následující možnosti konfigurace:

1. Povolit volbu Pouze vlastní kód:

    1. V nabídce **nástroje** zvolte **Možnosti** a pak zvolte možnost **ladění**.

    2. Vyberte **povolit pouze můj kód**.

2. Zakázání výjimek CLR:

    1. V nabídce **ladění** vyberte možnost **výjimky**.

    2. V případě **výjimek modulu CLR (Common Language Runtime)** zrušte kontrolu **neošetřeného uživatelem**.

## <a name="i-dont-see-the-option-to-change-browserwindowcurrentbrowser-in-the-coded-ui-test"></a><a name="generate"></a>*V programovém testu UI se nezobrazuje možnost změnit BrowserWindow. CurrentBrowser.*
 Je možné [!INCLUDE[vs2011_first](../includes/vs2011-first-md.md)] , že používáte verzi, která nepodporuje programové testy UI pomocí různých webových prohlížečů. Chcete-li použít tyto programové testy uživatelského rozhraní, je nutné použít Visual Studio Enterprise.

 *Co dalšího mám vědět?*
 **Poznámky**

- ![Prerequsite](../test/media/prereq.png "Požadavků ohlásila") Webový prohlížeč Apple Safari není podporován.

- ![Prerequsite](../test/media/prereq.png "Požadavků ohlásila") Akce spuštění webového prohlížeče musí být součástí kódovaného testu uživatelského rozhraní.

   Pokud je již webový prohlížeč otevřen a chcete v něm spustit příslušné kroky, aniž byste používali aplikaci Internet Explorer, přehrávání selže. Je proto vhodné zahrnout spuštění webového prohlížeče jako součást programových testů UI.

- ![Prerequsite](../test/media/prereq.png "Požadavků ohlásila") Automatizace specifických akcí uživatelského rozhraní založeného na prohlížeči, jako je maximalizace, minimalizace a obnovení, se nepodporuje.

  **Tip**

- ![Tip](../test/media/tip.png "Tip") Výstup můžete nakonfigurovat tak, aby zahrnoval snímky obrazovky v protokolech kódovaného uživatelského rozhraní. Chcete-li tak učinit, musíte provést některá nastavení konfigurace v souboru QTAgent32.exe.config. Ve výchozím nastavení je tento soubor nainstalován v následujícím umístění:

   **C:\Program Files (x86) \Microsoft Visual Studio 11.0 \ Common7\IDE**

   Nastavte následující hodnoty:

  - `EqtTraceLevel`v `system.diagnostics` části.

  - `<add name="EqtTraceLevel" value="4" />`

     Nastavíte-li hodnotu 3 nebo vyšší, budou snímky obrazovky pořízeny pro každou akci. Pokud je hodnota nastavena na 1 nebo 2, budou snímky obrazovky pořízeny pouze pro chybové akce.

    Další informace naleznete v tématu [Analýza programových testů uživatelského rozhraní pomocí protokolů kódovaného testu uživatelského rozhraní](../test/analyzing-coded-ui-tests-using-coded-ui-test-logs.md).

## <a name="external-resources"></a>Externí zdroje

### <a name="videos"></a>Videa
 [Záznam v aplikaci IE a přehrávání všude](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!183&authkey=!ANqaLtCZbtJrImU)

 [Vytváření testů pro různé prohlížeče pomocí Tvůrce programového testu uživatelského rozhraní](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!184&authkey=!AKG8CSow_qmeTq8)

 [Vytváření testů pro různé prohlížeče pomocí jednoduchých ručního kódování bez mapování uživatelského rozhraní](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!186&authkey=!AJaEvxJnsefyAT4)

 [Spuštění testů pro různé prohlížeče postupně na více prohlížečích](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!187&authkey=!ADI8eCQkxHnpOR8)

 [Řešení potíží se selháním testů pro různé prohlížeče](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!182&authkey=!AEpS48i295B49FI)

### <a name="guidance"></a>Doprovodné materiály
 [Testování pro průběžné doručování pomocí sady Visual Studio 2012 – Kapitola 2: testování částí: testování uvnitř](https://msdn.microsoft.com/library/jj159340.aspx)

 [Testování pro průběžné doručování pomocí sady Visual Studio 2012 – Kapitola 5: automatizace systémových testů](https://msdn.microsoft.com/library/jj159335.aspx)

### <a name="faq"></a>Nejčastější dotazy
 [Nejčastější dotazy k programovým testům UI – 1](https://docs.microsoft.com/archive/blogs/mathew_aniyan/content-index-for-coded-ui-test)

 [Nejčastější dotazy k programovým testům UI – 2](https://social.msdn.microsoft.com/Forums/en-US/vsautotest/thread/3a74dd2c-cef8-4923-abbf-7a91f489e6c4)

### <a name="forum"></a>Fórum
 [Testování automatizace uživatelského rozhraní sady Visual Studio (včetně kódovaného uživatelského rozhraní)](https://social.msdn.microsoft.com/Forums/en-US/vsautotest)

## <a name="see-also"></a>Viz také
 [Použití automatizace uživatelského rozhraní k otestování](../test/use-ui-automation-to-test-your-code.md) [Konfigurace podporovaných konfigurací a platforem pro programové testy uživatelského rozhraní a záznamy akcí při](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md) analýze programových testů uživatelského rozhraní [pomocí protokolů kódovaného testu uživatelského rozhraní](../test/analyzing-coded-ui-tests-using-coded-ui-test-logs.md)
