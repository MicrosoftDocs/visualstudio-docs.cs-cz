---
title: Zobrazit předchozí stav aplikace pomocí nástroje IntelliTrace
description: Zjistěte, jak dělat jeho snímky a zobrazení snímků pomocí zpětného kroku IntelliTrace
ms.custom: seodec18
ms.date: 09/19/2018
ms.technology: vs-ide-debug
ms.topic: tutorial
ms.assetid: 7c60d929-d993-49dc-9db3-43b30be9912b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ba1ab23fead36cfabc8b2754535e8b10de981987
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53060142"
---
# <a name="inspect-previous-app-states-using-intellitrace-step-back-in-visual-studio"></a>Kontrola předchozí nové aplikace pomocí zpětného kroku IntelliTrace v sadě Visual Studio

Zpětného kroku IntelliTrace automaticky vytvoří snímek vaší aplikace v každé zarážce a ladicí program krok události. Zaznamenané snímky umožňují snadno vrátit k předchozím zarážkám nebo krokům a zobrazit stav aplikace jako v minulosti. IntelliTrace zpětným krokem vám může ušetřit čas při chcete zobrazit předchozí stav aplikace, ale nebudete chtít znovu spusťte ladění nebo znovu vytvořit stav požadované aplikace.

Zpětného kroku IntelliTrace je k dispozici od verze Visual Studio Enterprise 2017 verze 15.5 a vyšší a vyžaduje aktualizaci Windows 10 Anniversary Update nebo novější. Tato funkce je momentálně podporovaná pro ladění ASP.NET, WinForms, WPF, aplikací spravované konzoly a knihoven spravovaných tříd. Od verze Visual Studio Enterprise 2017 verze 15.7, tato funkce je také podporována pro ASP.NET Core a .NET Core. Od verze Visual Studio Enterprise 2017 verzi 15.9 ve verzi Preview 2, tato funkce je také podporována pro nativní aplikace určené pro Windows. Ladění aplikací UWP se momentálně nepodporuje.

V tomto kurzu se naučíte:

> [!div class="checklist"]
> * Povolit události Intellitrace a snímky
> * Procházet události pomocí příkazů krok zpátky a krok vpřed
> * Zobrazit události snímky
  
## <a name="enable-intellitrace-events-and-snapshots-mode"></a>Povolit režim události a snímky IntelliTrace 

1. Otevřete svůj projekt v sadě Visual Studio Enterprise.

1. Otevřít **nástroje** > **možnosti** > **IntelliTrace** nastavení a vyberete možnost **IntelliTrace události a snímky** . 

    Spouští se v sadě Visual Studio 2017 Enterprise verzi 15.9 ve verzi Preview 2, tato možnost je **snímky IntelliTrace (spravovaný a nativní)**. 

    ![Povolit režim události IntelliTrace a snímky](../debugger/media/intellitrace-enable-snapshots.png "režim povolit události IntelliTrace a snímky")

1. Pokud chcete nakonfigurovat možnosti pro zobrazení snímky při výjimkách, zvolte **IntelliTrace** > **Upřesnit** z **možnosti** dialogové okno.

    Tyto možnosti jsou dostupné od verze Visual Studio Enterprise 2017 verze 15.7.

    ![Konfigurace chování pro snímky při výjimkách](../debugger/media/intellitrace-enable-snapshots-on-exceptions.png)

    Když povolíte události a snímky, pořizování snímků u výjimek je také povolena ve výchozím nastavení. Snímky pro výjimky můžete zakázat odznačením **shromažďovat události výjimky**. Pokud je tato funkce povolena, snímky pořízeny pro neošetřené výjimky. Zpracování výjimek snímky pocházejí jenom v případě, že je vyvolána výjimka, a pokud nebude znovu vyvolat výjimku dříve vyvolána. Maximální počet snímků u výjimek můžete nastavit tak, že vyberete hodnotu z rozevíracího seznamu. Maximum platí pro pokaždé, když vaše aplikace přejde do režimu přerušení (například pokud vaše aplikace narazí na zarážku).

    > [!NOTE]
    > Snímky pořízeny pouze pro události výjimky nástroj IntelliTrace zaznamenává. Pro spravovaný kód, můžete zadat tak, že vyberete jaké události IntelliTrace zaznamená **nástroje** > **možnosti** > **události IntelliTrace**.

1. Ve vašem projektu, nastavte jednu nebo více zarážek a spustit ladění (stisknutím klávesy **F5**), nebo spustit ladění krokování kódu (**F10** nebo **F11**).

    IntelliTrace pořídí snímek procesu vaší aplikace na každý krok ladicího programu, událost zarážky a události neošetřené výjimky. Tyto události se zaznamenávají do **události** kartu **diagnostické nástroje** okna, společně s další události IntelliTrace. Chcete-li otevřít toto okno, zvolte **ladění** > **Windows** > **zobrazit diagnostické nástroje**.

    Vedle událostí, pro které jsou k dispozici snímky se zobrazí ikonu fotoaparátu. 

    ![Události kartě se snímky](../debugger/media/intellitrace-events-tab-with-snapshots.png "kartu události pomocí snímků na zarážkách a kroky")

    Z důvodů výkonu nejsou přijata snímků při krokování s velmi rychle. Pokud se nezobrazí ikona fotoaparátu vedle příslušného kroku, zkuste krokování pomaleji.

## <a name="navigate-and-view-snapshots"></a>Vyhledání a zobrazení snímků

1. Přecházet mezi jednotlivými události pomocí **krok zpět (Alt + [)** a **krok dál (Alt +])** tlačítek na panelu nástrojů ladění.

    Tato tlačítka Procházet události, které se zobrazují v **události** kartu **okno diagnostické nástroje**. Automaticky krokování zpět nebo vpřed na událost aktivuje [historické ladění](../debugger/historical-debugging.md) u vybrané události.

    ![Krokovat zpět a vpřed tlačítka](../debugger/media/intellitrace-step-back-icons-description.png "tlačítka pro krok zpět a krok vpřed")

    Při zastav nebo krok vpřed, Visual Studio přejde do režimu historické ladění. V tomto režimu se kontext ladicího programu přepne na čas, kdy se přihlášení vybrané události. Visual Studio také přesune ukazatel na odpovídající řádek kódu v okně zdroje. 

    V tomto zobrazení si můžete prohlédnout hodnoty **zásobník volání**, **místní hodnoty**, **automatické hodnoty**, a **Watch** windows. Může také myší proměnné zobrazení datových tipech a provést vyhodnocení výrazu v **okamžité** okna. Data, která se zobrazí, je ze snímku proces aplikací přijatá od tohoto okamžiku v čase.

    Tak například, pokud jste se dostali na zarážku a trvání kroku (**F10**), **krok zpět** tlačítko vloží sady Visual Studio v režimu historických na řádek kódu odpovídající až k zarážce. 

    ![Aktivace režimu historických pro událost pomocí snímku](../debugger/media/intellitrace-historical-mode-with-snapshot.png "aktivace historických režimu pro událost pomocí snímku")

2. Chcete-li vrátit k živé spuštění, zvolte **pokračovat (F5)** nebo klikněte na tlačítko **vrátit k živému ladění** odkaz na informačním panelu. 

3. Můžete zobrazit také snímek ze **události** kartu. Chcete-li to provést, vyberte události pomocí snímku a klikněte na **aktivovat historické ladění**.

    ![Aktivovat historické ladění pro událost](../debugger/media/intellitrace-activate-historical-debugging.png "aktivovat historické ladění pro událost")

    Na rozdíl od **nastavit další příkaz** znovu nespustí příkaz zobrazení snímku kódu; poskytuje statické zobrazení stavu aplikace v bodě v čase, ke kterým došlo v minulosti.

    ![Přehled zpětného kroku IntelliTrace](../debugger/media/intellitrace-step-back-overview.png "přehled o zpětného kroku IntelliTrace")

    Další informace o tom, jak kontrolovat proměnné v sadě Visual Studio najdete v tématu [prohlídka funkcí ladicího programu](../debugger/debugger-feature-tour.md)  

## <a name="frequently-asked-questions"></a>Nejčastější dotazy

#### <a name="how-is-intellitrace-step-back-different-from-intellitrace-events-only-mode"></a>Čím se liší od režimu pouze události IntelliTrace zpětného kroku IntelliTrace

V režimu pouze události IntelliTrace umožňuje aktivovat historické ladění na ladicí program kroků a zarážek. Ale IntelliTrace zaznamená pouze data v **lokální** a **automatické hodnoty** windows, pokud se systému windows jsou otevřené a zaznamená pouze data, která je rozbalená a v zobrazení. V režimu jen pro události které není často nutné ucelený pohled proměnných a komplexních objektů. Kromě toho výraz hodnocení a zobrazení dat v **Watch** okno není podporováno. 

V režimu události a snímky IntelliTrace zaznamená celý snímek procesu aplikace, včetně složitých objektů. V řádku kódu můžete zobrazit stejné informace, jako kdyby byly zastavení na zarážce (a nezáleží, jestli byly dříve rozvíjeny informace). Vyhodnocení výrazu je také podporované při prohlížení snímku.  

#### <a name="what-is-the-performance-impact-of-this-feature"></a>Co je dopad na výkon této funkce? 

Dopad na celkový výkon taktování závisí na vaší aplikace. Nároky na pořízení snímku je přibližně 30 ms. Když se pořídí snímek, Rozvětvená proces aplikací a rozvětveného kopírování je pozastaveno. Při zobrazení snímku sady Visual Studio se připojuje k rozvětveného kopii procesu. U jednotlivých snímků sady Visual Studio zkopíruje pouze tabulky stránky a pro kopírování na zápis na stránkách. Pokud objektů na haldě změnit mezi ladicí program se přidružené snímky, tabulky příslušné stránky se pak zkopíruje, výsledkem je minimální paměti náklady. Pokud sada Visual Studio zjistí, že není dostatek paměti k vytvoření snímku, nepřijímá jeden.
 
## <a name="known-issues"></a>Známé problémy  
* Pokud používáte režim události a snímky IntelliTrace ve verzích Windows starších než Windows 10 Fall Creators Update (RS3), a pokud je ladicí Cílová platforma aplikace nastavená na x86, nepřijímá snímky IntelliTrace.

    Alternativní řešení:
  * Pokud jste na Windows 10 Anniversary Update (RS1) a nižší než verze 10.0.14393.2273, [nainstalovat KB4103720](https://support.microsoft.com/help/4103720/windows-10-update-kb4103720). 
  * Pokud jste ve Windows 10 Creators Update (RS2) a nižší než verze 10.0.15063.1112, [nainstalovat KB4103722](https://support.microsoft.com/help/4103722/windows-10-update-4103722).
  * Instalaci nebo upgradu na Windows 10 Fall Creators Update (RS3). 
  * Další možností: 
    1. Nainstalujte z instalačního programu Visual studio sadu nástrojů VC++ 2015.3 v140 pro desktop (x86, x64).
    2. Sestavte cílovou aplikaci.
    3. Z příkazového řádku, použijte nástroj editbin a pro nastavení `Largeaddressaware` příznak pro cílový spustitelný soubor. Například můžete použít tento příkaz (po aktualizaci cesty): "C:\Program Files (x86) \Microsoft Visual Studio\Preview\Enterprise\VC\Tools\MSVC\14.12.25718\bin\Hostx86\x86\editbin.exe" / LARGEADDRESSAWARE "C:\Path\To\Application\app.exe".
    4. Chcete-li spustit ladění, stiskněte **F5**. Nyní snímky se přesunete na ladicí program kroků a zarážek.

       > [!Note]
       > `Largeaddressaware` Musí být nastaven příznak pokaždé, když se spustitelný soubor je znovu sestaví se změnami.

* Pokud na aplikaci, která používá trvalý soubor mapovaných do paměti se pořídí snímek aplikace procesu, proces se snímkem udržuje výhradní zámek souborů mapovaných do paměti (i po nadřazený proces vydala platnost zámku). Jiné procesy jsou stále moct číst, ale nikoli zápis do souborů mapovaných do paměti.

    Alternativní řešení:
    * Vymažte všechny snímky tím, že ukončení relace ladění. 

* Při ladění aplikace, jejichž proces má vysoký počet jedinečných paměti oblastech, jako je například aplikace, která načte velký počet knihoven DLL, krokování výkonu pomocí snímků povolené může mít vliv. Tento problém bude vyřešen v budoucí verzi systému Windows. Pokud máte potíže, kontaktujte nás na adrese stepback@microsoft.com. 

* Při ukládání souboru s **ladit > IntelliTrace > relace IntelliTrace Uložit** v režimu události a snímky dalších dat zachycených snímků není k dispozici v souboru .itrace. Na zarážce a kroku události uvidíte stejné informace, jako kdyby jste uložili soubor v režimu pouze události IntelliTrace. 

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste zjistili, jak pomocí zpětného kroku IntelliTrace. Můžete získat další informace o dalších funkcí technologie IntelliTrace.

> [!div class="nextstepaction"]
> [Funkce IntelliTrace](../debugger/intellitrace-features.md)
