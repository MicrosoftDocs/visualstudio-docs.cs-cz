---
title: Zobrazení předchozího stavu aplikace pomocí intelliTrace
description: Naučte se pořizovat snímky a zobrazit snímky pomocí krokového zpět nýtu IntelliTrace
ms.custom: seodec18
ms.date: 09/19/2018
ms.topic: tutorial
ms.assetid: 7c60d929-d993-49dc-9db3-43b30be9912b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 83d444cb5e3345d79ca6e1422982c0ecd37e4287
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "67825530"
---
# <a name="inspect-previous-app-states-using-intellitrace-step-back-in-visual-studio-visual-studio-enterprise"></a>Kontrola předchozích stavů aplikace pomocí intelliTrace krok zpět v Sadě Visual Studio (Visual Studio Enterprise)

Krok zpět intelliTrace automaticky pořídí snímek vaší aplikace při každé události kroku zarážky a ladicího programu. Zaznamenané snímky umožňují vrátit se k předchozím zarážky nebo kroky a zobrazit stav aplikace, jak tomu bylo v minulosti. IntelliTrace krok-back můžete ušetřit čas, když chcete zobrazit předchozí stav aplikace, ale nechcete restartovat ladění nebo znovu vytvořit požadovaný stav aplikace.

Krok zpět ný aplikace IntelliTrace je k dispozici od verze 15.5 a vyšší ve Visual Studiu Enterprise 2017 a vyšší a vyžaduje aktualizaci Windows 10 Anniversary Update nebo vyšší. Tato funkce je aktuálně podporována pro ladění ASP.NET, WinForms, WPF, aplikací spravované konzoly a knihoven spravovaných tříd. Počínaje Visual Studio 2017 Enterprise verze 15.7, funkce je také podporována pro ASP.NET Core a .NET Core. Počínaje Visual Studio 2017 Enterprise verze 15.9 Preview 2 je tato funkce podporována také pro nativní aplikace zaměřené na Windows. Ladění aplikací UPW není aktuálně podporováno.

V tomto kurzu provedete následující:

> [!div class="checklist"]
> * Povolit události a snímky IntelliTrace
> * Navigace při událostech pomocí příkazů krok zpět a krok vpřed
> * Zobrazit snímky událostí

## <a name="enable-intellitrace-events-and-snapshots-mode"></a>Povolit režim událostí a snímků IntelliTrace

1. Otevřete projekt v sadě Visual Studio Enterprise.

1. **Otevřete** > nastavení Nástroje**Možnosti** > **IntelliTrace** a vyberte možnost **IntelliTrace události a snímky**.

    Počínaje Visual Studio 2017 Enterprise verze 15.9 Náhled 2, tato možnost je **IntelliTrace snímky (spravované a nativní)**.

    ![Povolit režim událostí a snímků IntelliTrace](../debugger/media/intellitrace-enable-snapshots.png "Povolit režim událostí a snímků IntelliTrace")

1. Pokud chcete nakonfigurovat možnosti pro zobrazení snímků na výjimkách, zvolte **IntelliTrace** > **Upřesnit** z dialogového okna **Možnosti.**

    Tyto možnosti jsou k dispozici od visual studia 2017 Enterprise verze 15.7.

    ![Konfigurace chování pro snímky na výjimky](../debugger/media/intellitrace-enable-snapshots-on-exceptions.png)

    Když povolíte události a snímky, pořizování snímků na výjimky je také povolena ve výchozím nastavení. Snímky na výjimkách můžete zakázat zrušením zaškrtnutí políčka **Shromáždit snímky na událostech výjimek**. Pokud je tato funkce povolena, snímky jsou pořízeny pro neošetřené výjimky. Pro zpracované výjimky snímky jsou převzaty pouze v případě, že je vyvolána výjimka a pokud není re-throw dříve vyvolána výjimku. Maximální počet snímků na výjimky můžete nastavit výběrem hodnoty z rozevíracího seznamu. Maximální hodnota platí pro každou dobu, kdy vaše aplikace přejde do režimu přerušení (například když aplikace narazí na zarážku).

    > [!NOTE]
    > Snímky jsou pořštité pouze pro události výjimky, které IntelliTrace zaznamenává. Pro spravovaný kód můžete určit, jaké události intelliTrace zaznamenává výběrem**možnosti** >  **nástroje** > **IntelliTrace Události**.

1. V projektu nastavte jeden nebo více zarážek a začněte ladit (stiskněte **klávesu F5**) nebo začněte ladit krokováním kódu (**F10** nebo **F11**).

    IntelliTrace pořídí snímek procesu aplikace na každém kroku ladicího programu, události zarážky a události neošetřené výjimky. Tyto události jsou **zaznamenány** na kartě Události v okně **Diagnostické nástroje** spolu s dalšími událostmi IntelliTrace. Chcete-li otevřít toto okno, zvolte **Ladit** > **diagnostické nástroje služby****Windows** > Show .

    Vedle událostí, pro které jsou k dispozici snímky, se zobrazí ikona kamery.

    ![Karta Události se snímky](../debugger/media/intellitrace-events-tab-with-snapshots.png "Karta Události se snímky zarážky a kroky")

    Z důvodů výkonu snímky nejsou pořízeny při krok velmi rychle. Pokud se vedle kroku nezobrazí žádná ikona fotoaparátu, zkuste krokovat pomaleji.

## <a name="navigate-and-view-snapshots"></a>Navigace a zobrazení snímků

1. Procházejte mezi událostmi pomocí tlačítek **Krok zpět (Alt + [)** a **Krok vpřed (Alt + ])** na panelu nástrojů Ladění.

    Tato tlačítka procházet události, které se zobrazí na kartě **Události** v **okně Diagnostické nástroje**. Krokování zpět nebo vpřed na událost automaticky aktivuje [historické ladění](../debugger/historical-debugging.md) vybrané události.

    ![Krok vpřed a vpřed](../debugger/media/intellitrace-step-back-icons-description.png "Tlačítka Krok vpřed a Krok vpřed")

    Když krok zpět nebo krok vpřed, Visual Studio přejde do režimu historické ladění. V tomto režimu se kontext ladicího programu přepne na čas, kdy byla zaznamenána vybraná událost. Visual Studio také přesune ukazatel na odpovídající řádek kódu ve zdrojovém okně.

    V tomto zobrazení můžete zkontrolovat hodnoty v režimech **Zásobník volání**, **Místní ,** **Autos**a **Sledovat.** Můžete také najet na proměnné, abyste si mohli zobrazit datatipy a provést vyhodnocení výrazu v okně **Okamžité.** Data, která vidíte, jsou z snímku procesu aplikace pořízenév tomto okamžiku.

    Takže například pokud jste narazili na zarážku a provedli krok **(F10),** tlačítko **Krok zpět** umístí Visual Studio v historickém režimu na řádku kódu odpovídající zarážky.

    ![Aktivace historického režimu na události se snímkem](../debugger/media/intellitrace-historical-mode-with-snapshot.png "Aktivace historického režimu na události se snímkem")

2. Chcete-li se vrátit k živému spuštění, zvolte **Pokračovat (F5)** nebo klepněte na odkaz **Návrat do živého ladění** na informačním panelu.

3. Snímek můžete také zobrazit na kartě **Události.** Chcete-li to provést, vyberte událost se snímkem a klepněte na tlačítko **Aktivovat historické ladění**.

    ![Aktivace historického ladění události](../debugger/media/intellitrace-activate-historical-debugging.png "Aktivace historického ladění události")

    Na rozdíl od příkazu **Nastavit další příkaz** zobrazení snímku znovu nespustí váš kód; poskytuje statický pohled na stav aplikace v okamžiku, ke kterému došlo v minulosti.

    ![Přehled krok-back IntelliTrace](../debugger/media/intellitrace-step-back-overview.png "Přehled krokového zpětného kroku IntelliTrace")

    Další informace o kontrole proměnných v sadě Visual Studio najdete v [tématu První pohled na ladicí program](../debugger/debugger-feature-tour.md)

## <a name="frequently-asked-questions"></a>Nejčastější dotazy

#### <a name="how-is-intellitrace-step-back-different-from-intellitrace-events-only-mode"></a>Jak se intelliTrace krok zpět liší od intelliTrace pouze režim událostí?

IntelliTrace v režimu pouze události umožňuje aktivovat historické ladění na kroky ladicího programu a zarážky. IntelliTrace však zachycuje data pouze v **místních a** **automatických oken,** pokud jsou otevřená okna a zachycuje pouze data, která je rozbalená a v zobrazení. V režimu pouze události často nemáte úplné zobrazení proměnných a složitých objektů. Kromě toho není podporováno vyhodnocení výrazu a zobrazení dat v okně **kukátka.**

V režimu událostí a snímků IntelliTrace zachycuje celý snímek procesu aplikace, včetně složitých objektů. Na řádku kódu můžete zobrazit stejné informace, jako kdybyste byli zastaveni na zarážky (a nezáleží na tom, zda jste dříve rozbalili informace). Vyhodnocení výrazu je také podporováno při zobrazení snímku.  

#### <a name="what-is-the-performance-impact-of-this-feature"></a>Jaký je dopad této funkce na výkon? 

Dopad na celkový výkon krokování závisí na vaší aplikaci. Režie pořízení snímku je kolem 30 ms. Po pořízení snímku se proces aplikace rozpisuje a rozpůlená kopie je pozastavena. Při zobrazení snímku Visual Studio se připojuje k rozpůlené kopii procesu. Pro každý snímek Visual Studio zkopíruje pouze stránkovací tabulku a nastaví stránky pro kopírování při zápisu. Pokud se objekty na haldě mění mezi kroky ladicího programu s přidruženými snímky, příslušná stránkovací tabulka se pak zkopíruje, což vede k minimálním nákladům na paměť. Pokud Visual Studio zjistí, že není dostatek paměti pro pořízení snímku, netrvá jeden.

## <a name="known-issues"></a>Známé problémy
* Pokud používáte intelliTrace události a snímky režimu ve verzích systému Windows starší než Windows 10 Fall Creators Update (RS3), a pokud ladění platformy cíl aplikace je nastavena na x86, IntelliTrace nepořizovat snímky.

    Alternativní řešení:
  * Pokud jste na Windows 10 Výročí Update (RS1) a pod verzí 10.0.14393.2273, [nainstalujte KB4103720](https://support.microsoft.com/help/4103720/windows-10-update-kb4103720).
  * Pokud jste na Windows 10 Creators Update (RS2) a pod verzí 10.0.15063.1112, [nainstalujte KB4103722](https://support.microsoft.com/help/4103722/windows-10-update-4103722).
  * Nainstalujte nebo upgradujte na aktualizaci Windows 10 Fall Creators Update (RS3).
  * Máte k dispozici i další možnosti:
    1. Nainstalujte z instalačního programu Visual studio sadu nástrojů VC++ 2015.3 v140 pro desktop (x86, x64).
    2. Sestavte cílovou aplikaci.
    3. Z příkazového řádku nastavte příznak cílového `Largeaddressaware` spustitelného souboru pomocí nástroje editbin. Můžete například použít tento příkaz (po aktualizaci cesty): "C:\Program Files (x86)\Microsoft Visual Studio\Preview\Enterprise\VC\Tools\MSVC\14.12.25718\bin\Hostx86\x86\editbin.exe" /Largeaddressaware "C:\Path\To\Application\app.exe".
    4. Ladění spustíte stisknutím **klávesy F5**. Nyní snímky jsou pořízeny na kroky ladicího programu a zarážky.

       > [!Note]
       > Příznak `Largeaddressaware` musí být nastaven pokaždé, když je spustitelný soubor znovu sestaven se změnami.

* Při snímek procesu aplikace je přijata v aplikaci, která používá soubor mapovaný trvalé paměti, proces s snímek obsahuje výhradní zámek na mapované maškarní soubor (i poté, co nadřazený proces vydal a jeho zámek). Ostatní procesy jsou stále schopni číst, ale ne zapisovat, do souboru mapovaného paměti.

  Alternativní řešení:
  * Vymazat všechny snímky ukončením relace ladění.

* Při ladění aplikace, jejíž proces má vysoký počet oblastí jedinečné paměti, jako je například aplikace, která načte velký počet knihovny DLL, krokování výkon s povolenými snímky může být ovlivněna. Tento problém bude vyřešen v budoucí verzi systému Windows. Pokud se u Vás tento problém vyskytne, sáhněte se na nás na adrese stepback@microsoft.com.

* Při ukládání souboru s **ladění > IntelliTrace > Uložit intelliTrace relace v** režimu událostí a snímků, další data zachycená ze snímků není k dispozici v souboru .itrace. Na události zarážky a kroku se zobrazí stejné informace, jako kdybyste uložili soubor v režimu pouze události IntelliTrace.

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste se naučili, jak používat IntelliTrace krok zpět. Můžete se dozvědět více o dalších funkcích IntelliTrace.

> [!div class="nextstepaction"]
> [Funkce IntelliTrace](../debugger/intellitrace-features.md)
