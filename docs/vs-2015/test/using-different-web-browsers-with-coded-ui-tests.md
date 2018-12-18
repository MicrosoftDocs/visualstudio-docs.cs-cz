---
title: Používání jiných webových prohlížečů s kódované testy uživatelského rozhraní | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a859595f-6517-43f2-9d61-c706cb55a388
caps.latest.revision: 25
ms.author: gewarren
manager: douge
ms.openlocfilehash: e9e540e35bdfd68d8c371c2bad0ace3fc4b420e0
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49893231"
---
# <a name="using-different-web-browsers-with-coded-ui-tests"></a>Používání jiných webových prohlížečů v programových testech uživatelského rozhraní
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Programové testy UI mohou automatizovat testování webových aplikací tím, že zaznamenají vaše testy pomocí aplikace Internet Explorer. Potom můžete přizpůsobit test a přehrát jej buď pomocí aplikace Internet Explorer, nebo jiných typů prohlížečů pro tyto webové aplikace.  
  
 **Požadavky**  
  
- Visual Studio Enterprise  
  
- Operační systémy:  
  
  -   Microsoft Windows 7  
  
  -   Microsoft Windows 8  
  
  -   Microsoft Windows Server 2008 R2 SP1  
  
- Verze webového prohlížeče:  
  
  -   Windows Internet Explorer 9  
  
  -   Windows Internet Explorer 10  
  
  -   Podporované verze prohlížečů Mozilla Firefox a Google Chrome, přejděte [zde](http://visualstudiogallery.msdn.microsoft.com/11cfc881-f8c9-4f96-b303-a2780156628d/)  
  
- Nainstalujte [součásti Selenium pro programové testování uživatelského rozhraní pro různé prohlížeče](http://visualstudiogallery.msdn.microsoft.com/11cfc881-f8c9-4f96-b303-a2780156628d/).  
  
  **Co je podporováno ve všech webových prohlížečích?**  
  
- [Přidání vlastního kódu pro řízení funkcí](http://blogs.msdn.com/b/visualstudioalm/archive/2012/12/10/coded-ui-test-configuring-search-properties-while-recording-on-internet-explorer.aspx) například vlastnosti, vyhledávání a podprocesy přehrávání.  
  
- Automaticky otevíraná okna a dialogová okna  
  
- [Spustit základní JavaScript bez návratového typu](http://blogs.msdn.com/b/visualstudioalm/archive/2013/01/18/introducing-jscript-execution-on-internetexplorer-and-crossbrowser-in-coded-ui-test.aspx)  
  
- Hledat oblasti odolnosti (pomocí inteligentní shody) a [vylepšení výkonu](http://blogs.msdn.com/b/visualstudioalm/archive/2012/02/01/guidelines-on-improving-performance-of-coded-ui-test-playback.aspx)  
  
## <a name="why-should-i-use-coded-ui-tests-across-multiple-web-browser-types"></a>Proč bych měl používat programové testy UI napříč několika typy webových prohlížečů?  
 Při testování webové aplikace pomocí různých typů webových prohlížečů můžete lépe emulovat zkušenosti vašich uživatelů s uživatelským rozhraním na různých prohlížečích. Aplikace může například obsahovat ovládací prvek nebo kód v aplikaci Internet Explorer, který není kompatibilní s jinými webovými prohlížeči. Spuštěním programových testů UI na různých prohlížečích můžete objevit a opravit jakýkoliv problém předtím, než ovlivní vaše zákazníky.  
  
## <a name="how-do-i-record-and-play-back-coded-ui-tests-on-web-applications-using-the-supported-web-browsers"></a>Jak mohu zaznamenat a přehrát programové testy UI webových aplikacích pomocí podporovaných webových prohlížečů?  
 **Záznam:** Tvůrce programového testu UI musíte použít k záznamu testu webové aplikace pomocí aplikace Internet Explorer. Volitelně můžete pomocí předdefinované sady vlastností přidat kód pro ověření a přizpůsobení testovaných ovládacích prvků, jak byste to obvykle udělali v případě programových testů UI. Další informace najdete v tématu [pomocí uživatelského rozhraní automatizace k testu kódu](../test/use-ui-automation-to-test-your-code.md).  
  
> [!NOTE]
>  Programové testy UI nelze zaznamenat pomocí prohlížečů Google Chrome nebo Mozilla Firefox.  
  
 **Přehrávání pomocí aplikace Internet Explorer:** při není explicitně zadán žádný prohlížeč, testy budou spuštěny v aplikaci Internet Explorer ve výchozím nastavení. Můžete explicitně uvést prohlížeče tak, že nastavíte **BrowserWindow.CurrentBrowser** vlastností v kódu testu. Pro aplikaci Internet Explorer by měla být tato vlastnost nastavená na **IE** nebo **aplikace Internet Explorer**.  
  
 **Přehrávání pomocí webového prohlížeče Internet Explorer:** přehrát v prohlížečích, Internet Explorer, změňte vlastnost BrowserWindow.CurrentBrowser v kódu testu buď **Firefox** nebo **Chrome** .  
  
 Chcete-li přehrát testy v prohlížečích než Internet Exploreru, je nutné nainstalovat **součásti Selenium pro programové testování uživatelského rozhraní pro různé prohlížeče**.  
  
#### <a name="installing-selenium-components"></a>Instalace součástí Selenium  
  
1. Na **nástroje** nabídce zvolte **rozšíření a aktualizace**.  
  
2. V dialogovém okně rozšíření a aktualizace vyhledejte `Selenium components for Cross Browser Testing`.  
  
3. Zvýrazněte rozšíření a zvolte možnost **Stáhnout**.  
  
   > [!TIP]
   >  Můžete také stáhnout součásti Selenium pro programové testování uživatelského rozhraní pro různé prohlížeče z [tady](http://visualstudiogallery.msdn.microsoft.com/11cfc881-f8c9-4f96-b303-a2780156628d/).  
  
   Další informace o vytváření a používání kódované UI testy, naleznete v tématu [vytváření programových testů UI](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate).  
  
### <a name="enable-debugging"></a>Povolení ladění  
 Chcete-li povolit ladění webové aplikace, je nutné dokončit následující možnosti konfigurace:  
  
1.  Povolit volbu Pouze vlastní kód:  
  
    1.  Na **nástroje** nabídce zvolte **možnosti** a klikněte na tlačítko **ladění**.  
  
    2.  Vyberte **povolit volbu pouze vlastní kód**.  
  
2.  Zakázání výjimek CLR:  
  
    1.  Na **ladění** nabídce zvolte **výjimky**.  
  
    2.  Pro **výjimky modulu Common Language Runtime**, zrušte zaškrtnutí políčka **uživatelem neošetřené**.  
  
##  <a name="generate"></a> *Nevidím možnost změnit atribut BrowserWindow.CurrentBrowser v programovém testu uživatelského rozhraní.*  
 Používáte verzi [!INCLUDE[vs2011_first](../includes/vs2011-first-md.md)] nepodporující programové testy UI pomocí různých webových prohlížečů. Pokud chcete použít tyto programové testy UI, musíte použít Visual Studio Enterprise.  
  
 *Co dalšího mohu vědět?*  
 **Poznámky**  
  
- ![Prerequsite](../test/media/prereq.png "požadavky") webový prohlížeč Apple Safari není podporován.  
  
- ![Prerequsite](../test/media/prereq.png "požadavky") akce spuštění webového prohlížeče musí být součástí programového testu uživatelského rozhraní.  
  
   Pokud je již webový prohlížeč otevřen a chcete v něm spustit příslušné kroky, aniž byste používali aplikaci Internet Explorer, přehrávání selže. Je proto vhodné zahrnout spuštění webového prohlížeče jako součást programových testů UI.  
  
- ![Prerequsite](../test/media/prereq.png "požadavky") prohlížeče automatizace specifické podle akce uživatelského rozhraní, jako je maximalizace, minimalizace a obnovení se nepodporuje.  
  
  **Tipy**  
  
- ![Tip](../test/media/tip.png "Tip") můžete nakonfigurovat výstup do obsahoval snímky obrazovky v kódovaných protokolech UI. Chcete-li tak učinit, musíte provést některá nastavení konfigurace v souboru QTAgent32.exe.config. Ve výchozím nastavení je tento soubor nainstalován v následujícím umístění:  
  
   **C:\Program Files (x86)\Microsoft Visual Studio 11.0\Common7\IDE**  
  
   Nastavte následující hodnoty:  
  
  - `EqtTraceLevel` v `system.diagnostics` oddílu.  
  
  - `<add name="EqtTraceLevel" value="4" />`  
  
     Nastavíte-li hodnotu 3 nebo vyšší, budou snímky obrazovky pořízeny pro každou akci. Pokud je hodnota nastavena na 1 nebo 2, budou snímky obrazovky pořízeny pouze pro chybové akce.  
  
    Další informace najdete v tématu [analýza programových testů pomocí programového uživatelského rozhraní protokolů testů](../test/analyzing-coded-ui-tests-using-coded-ui-test-logs.md).  
  
## <a name="external-resources"></a>Externí zdroje  
  
### <a name="videos"></a>Videa  
 [Záznam v aplikaci Internet Explorer a přehrávání všude](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!183&authkey=!ANqaLtCZbtJrImU)  
  
 [Autor testů pro různé prohlížeče pomocí Tvůrce programového testu UI](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!184&authkey=!AKG8CSow_qmeTq8)  
  
 [Autor testů pro různé prohlížeče pomocí prostého ručního kódování bez mapování uživatelského rozhraní](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!186&authkey=!AJaEvxJnsefyAT4)  
  
 [Spuštění testů pro různé prohlížeče postupně v různé prohlížeče](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!187&authkey=!ADI8eCQkxHnpOR8)  
  
 [Řešení potíží pro různé prohlížeče selhání testu](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!182&authkey=!AEpS48i295B49FI)  
  
### <a name="guidance"></a>Doprovodné materiály  
 [Testování pro nepřetržité dodávky s Visual Studio 2012 – kapitola 2: testování částí: testování uvnitř](http://go.microsoft.com/fwlink/?LinkID=255188)  
  
 [Testování pro nepřetržité dodávky s Visual Studio 2012 – kapitola 5: automatizace systémových testů](http://go.microsoft.com/fwlink/?LinkID=255196)  
  
### <a name="faq"></a>Nejčastější dotazy  
 [Programové testy UI – nejčastější dotazy – 1](http://go.microsoft.com/fwlink/?LinkID=230576)  
  
 [Programové testy UI – nejčastější dotazy -2](http://go.microsoft.com/fwlink/?LinkID=230578)  
  
### <a name="forum"></a>Fórum  
 [Visual Studio automatické testování uživatelského rozhraní (včetně programového uživatelského rozhraní)](http://go.microsoft.com/fwlink/?LinkID=224497)  
  
## <a name="see-also"></a>Viz také  
 [Použití automatizace uživatelského rozhraní k testování kódu](../test/use-ui-automation-to-test-your-code.md)   
 [Podporované konfigurace a platformy pro programové testy uživatelského rozhraní a zaznamenávání akcí](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)   
 [Analýza programových testů uživatelského rozhraní pomocí protokolů z těchto testů](../test/analyzing-coded-ui-tests-using-coded-ui-test-logs.md)



