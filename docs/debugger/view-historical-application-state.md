---
title: Zobrazit předchozí stav aplikace pomocí IntelliTrace
description: Naučte se pořizovat snímky a zobrazovat snímky pomocí IntelliTrace kroků zpátky.
ms.custom: seodec18
ms.date: 09/19/2018
ms.topic: tutorial
ms.assetid: 7c60d929-d993-49dc-9db3-43b30be9912b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f1ab54ccb3820b3a03724c30d16f08b3e8a45493
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99933099"
---
# <a name="inspect-previous-app-states-using-intellitrace-step-back-in-visual-studio-visual-studio-enterprise"></a>Kontrola předchozích stavů aplikace pomocí IntelliTrace kroků zpět v aplikaci Visual Studio (Visual Studio Enterprise)

IntelliTraceý krok zpět automaticky provede snímek vaší aplikace při každé události krok zarážky a ladicího programu. Zaznamenané snímky vám umožní přejít zpět na předchozí zarážky nebo kroky a zobrazit stav aplikace, stejně jako v minulosti. IntelliTraceý krok zpátky vám ušetří čas, když chcete zobrazit předchozí stav aplikace, ale nechcete znovu spustit ladění nebo znovu vytvořit požadovaný stav aplikace.

IntelliTrace step-back je k dispozici od verze Visual Studio Enterprise 2017 15,5 a vyšší a vyžaduje aktualizaci Windows 10 pro výročí nebo novější. Tato funkce se aktuálně podporuje pro ladění ASP.NET, WinForms, WPF, spravovaných konzolových aplikací a knihoven spravovaných tříd. Počínaje sadou Visual Studio 2017 Enterprise verze 15,7 je tato funkce také podporována pro ASP.NET Core a .NET Core. Počínaje verzí Visual Studio 2017 Enterprise verze 15,9 Preview 2 je tato funkce také podporována pro nativní aplikace cílené na Windows. Ladění aplikací pro UWP se momentálně nepodporuje.

V tomto kurzu:

> [!div class="checklist"]
> * Povolit IntelliTrace události a snímky
> * Procházení událostí pomocí příkazů zpět a krok vpřed
> * Zobrazení snímků událostí

## <a name="enable-intellitrace-events-and-snapshots-mode"></a>Povolit IntelliTrace události a režim snímků

1. Otevřete projekt v Visual Studio Enterprise.

1. Otevřete   >  **Možnosti** nástrojů  >  nastavení **IntelliTrace** a vyberte možnost **události a snímky IntelliTrace**.

    Počínaje verzí Visual Studio 2017 Enterprise verze 15,9 Preview 2 je tato možnost **IntelliTrace snímky (spravované a nativní)**.

    ![Povolit IntelliTrace události a režim snímků](../debugger/media/intellitrace-enable-snapshots.png "Povolit IntelliTrace události a režim snímků")

1. Pokud chcete konfigurovat možnosti pro zobrazování snímků při výjimkách, v   >  dialogovém okně **Možnosti** vyberte IntelliTrace **Upřesnit** .

    Tyto možnosti jsou k dispozici počínaje verzí Visual Studio 2017 Enterprise verze 15,7.

    ![Konfigurace chování snímků na výjimkách](../debugger/media/intellitrace-enable-snapshots-on-exceptions.png)

    Při povolování událostí a snímků je ve výchozím nastavení také povoleno vytváření snímků s výjimkami. Můžete zakázat snímky na výjimky tím, že zrušíte výběr **shromažďování snímků pro události výjimky**. Když je tato funkce povolená, pro neošetřené výjimky se vyberou snímky. Pro zpracované výjimky jsou snímky provedeny pouze v případě, že je vyvolána výjimka, a pokud se nejedná o opětovné vyvolání dříve vyvolané výjimky. Výběrem hodnoty z rozevíracího seznamu můžete nastavit maximální počet snímků na výjimky. Maximum platí pro pokaždé, když vaše aplikace přejde do režimu přerušení (například když vaše aplikace narazí na zarážku).

    > [!NOTE]
    > Snímky se odebírají jenom pro události výjimky, které IntelliTrace záznamy. Pro spravovaný kód můžete určit, které události IntelliTrace záznamy výběrem **nástrojů**  >  **Možnosti**  >  **IntelliTrace události**.

1. V projektu nastavte jednu nebo více zarážek a spusťte ladění (stiskněte klávesu **F5**) nebo spusťte ladění procházením kódu (**F10** nebo **F11**).

    IntelliTrace pořizuje snímek procesu aplikace v každém kroku ladicího programu, události zarážky a neošetřené události výjimky. Tyto události se zaznamenávají na kartě **události** v **diagnostické nástroje** okně spolu s dalšími událostmi IntelliTrace. Chcete-li otevřít toto okno, vyberte možnost **ladit**  >  **Windows**  >  **Zobrazit diagnostické nástroje**.

    Vedle událostí, pro které jsou dostupné snímky, se zobrazí ikona kamery.

    ![Karta události se snímky](../debugger/media/intellitrace-events-tab-with-snapshots.png "Karta události se snímky na zarážekch a krocích")

    Z důvodů výkonu se snímky neprovádí při velmi rychlém kroku. Pokud se vedle kroku nezobrazí žádná ikona kamery, zkuste krok pomaleji.

## <a name="navigate-and-view-snapshots"></a>Procházení a zobrazení snímků

1. Přecházení mezi událostmi pomocí tlačítek **krok zpět (Alt + [)** a **krok vpřed (ALT +])** na panelu nástrojů ladění.

    Tato tlačítka přecházejí na události, které se zobrazí na kartě **události** v **okně diagnostické nástroje**. Krok zpět nebo dopředu události automaticky aktivuje [historické ladění](../debugger/historical-debugging.md) u vybrané události.

    ![Krokovat tlačítka zpět a dopředu](../debugger/media/intellitrace-step-back-icons-description.png "Krokovat zpět a krokovat tlačítka dopředu")

    Když přejdete zpět nebo předáte krok vzad, Visual Studio přejde do režimu historických ladění. V tomto režimu se kontext ladicího programu přepne na čas, kdy se vybraná událost nahrála. Visual Studio také přesune ukazatel na odpovídající řádek kódu v okně zdroje.

    Z tohoto zobrazení můžete zkontrolovat hodnoty v oknech **zásobník volání**, **místní** hodnoty, **Automatické** hodnoty a **sledovat** . Můžete také umístit ukazatel myši na proměnné pro zobrazení datových tipů a vyhodnocení výrazu v **příkazovém** okně. Data, která vidíte, pochází ze snímku procesu aplikace v daném okamžiku.

    Takže například pokud jste narazili na zarážku a provedli krok (**F10**), přesune tlačítko **krok zpět** do historického režimu na řádek kódu odpovídající zarážce.

    ![Aktivace historického režimu pro událost se snímkem](../debugger/media/intellitrace-historical-mode-with-snapshot.png "Aktivace historického režimu pro událost se snímkem")

2. Chcete-li se vrátit k živému provádění, klikněte na tlačítko **pokračovat (F5)** nebo na informačním panelu klikněte na odkaz **návrat k živému ladění** .

3. Snímek můžete také zobrazit na kartě **události** . Provedete to tak, že vyberete událost se snímkem a kliknete na **aktivovat historické ladění**.

    ![Aktivovat historické ladění pro událost](../debugger/media/intellitrace-activate-historical-debugging.png "Aktivovat historické ladění pro událost")

    Na rozdíl od příkazu **nastavit další příkaz** se při zobrazení snímku nespustí váš kód znovu. poskytuje statické zobrazení stavu aplikace v určitém bodě v čase, k němuž došlo v minulosti.

    ![Přehled IntelliTrace kroků zpět](../debugger/media/intellitrace-step-back-overview.png "Přehled IntelliTrace kroků zpět")

    Další informace o tom, jak kontrolovat proměnné v aplikaci Visual Studio, naleznete v tématu [první pohled na ladicí program](../debugger/debugger-feature-tour.md) .

## <a name="frequently-asked-questions"></a>Nejčastější dotazy

#### <a name="how-is-intellitrace-step-back-different-from-intellitrace-events-only-mode"></a>Jak se IntelliTrace krok zpět liší od režimu pouze událostí IntelliTrace?

IntelliTrace v režimu pouze události umožňuje aktivovat historické ladění pro kroky ladicího programu a zarážky. IntelliTrace ale zachytí pouze data v **místních** a **automatických** oknech, pokud jsou otevřená okna a zachytí pouze data, která jsou rozbalená a zobrazená. V režimu pouze události často nemusíte mít úplné zobrazení proměnných a složitých objektů. Vyhodnocování výrazů a zobrazování dat v okně **kukátko** navíc není podporováno.

V režimu události a snímky IntelliTrace zachycuje celý snímek procesu aplikace, včetně složitých objektů. V jednom řádku kódu vidíte stejné informace, jako kdyby jste zastavili na zarážce (a nezáleží na tom, zda jste dříve rozšířili informace). Při prohlížení snímku se podporuje taky vyhodnocení výrazu.  

#### <a name="what-is-the-performance-impact-of-this-feature"></a>Jaký má dopad na výkon této funkce? 

Dopad na celkový výkon krokování závisí na vaší aplikaci. Režie při pořizování snímku je okolo 30 ms. Při pořízení snímku se proces aplikace rozvětvení a pozastaví se rozvětvená kopie. Při zobrazení snímku se Visual Studio připojí k rozvětvené kopii procesu. Pro každý snímek sada Visual Studio zkopíruje pouze tabulku stránky a nastaví stránky na kopírování do zápisu. Pokud se objekty v haldě mění mezi kroky ladicího programu s přidruženými snímky, bude zkopírována příslušná tabulka stránky, což vede k minimálnímu množství paměti. Pokud aplikace Visual Studio zjistí, že není k dispozici dostatek paměti k pořízení snímku, nebere v úvahu žádnou z nich.

## <a name="known-issues"></a>Známé problémy
* Pokud používáte IntelliTrace události a režim snímků ve verzích Windows starších než Windows 10, poklesne Creators Update (RS3) a pokud je cílová platforma ladění aplikace nastavená na x86, IntelliTrace nebere snímky.

    Alternativní řešení:
  * Pokud se nacházíte na Windows 10 – aktualizace pro výročí (RS1) a nižší verze 10.0.14393.2273, [nainstalujte KB4103720](https://support.microsoft.com/help/4103720/windows-10-update-kb4103720).
  * Pokud jste na Windows 10 Creators Update (RS2) a nižší verze 10.0.15063.1112, [nainstalujte KB4103722](https://support.microsoft.com/help/4103722/windows-10-update-4103722).
  * Nainstalujte nebo upgradujte na Windows 10, které patří do aktualizace Creators Update (RS3).
  * Máte k dispozici i další možnosti:
    1. Nainstalujte z instalačního programu Visual studio sadu nástrojů VC++ 2015.3 v140 pro desktop (x86, x64).
    2. Sestavte cílovou aplikaci.
    3. Z příkazového řádku použijte nástroj nástroje EDITBIN k nastavení `Largeaddressaware` příznaku pro cílový spustitelný soubor. Tento příkaz můžete například použít (po aktualizaci cesty): "C:\Program Files (x86) \Microsoft Visual Studio\Preview\Enterprise\VC\Tools\MSVC\14.12.25718\bin\Hostx86\x86\editbin.exe"/LARGEADDRESSAWARE "C:\Path\To\Application\app.exe".
    4. Ladění spustíte stisknutím klávesy **F5**. Nyní jsou snímky odebírány na kroky ladicího programu a zarážky.

       > [!Note]
       > `Largeaddressaware`Příznak musí být nastaven pokaždé, když se znovu sestaví spustitelný soubor se změnami.

* Když je snímek procesu aplikace vytvořen v aplikaci, která používá trvalý soubor mapované paměti, proces se snímkem uchovává exkluzivní zámek na souboru mapované paměti (i po uvolnění zámku nadřazeného procesu). Jiné procesy jsou stále schopné číst, ale nikoli zapisovat, do souboru mapovaného do paměti.

  Alternativní řešení:
  * Zruší všechny snímky ukončením relace ladění.

* Při ladění aplikace, jejíž proces má velký počet jedinečných oblastí paměti, jako je například aplikace, která načítá velký počet knihoven DLL, může být ovlivněn výkon krokování s povolenými snímky. Tento problém bude řešen v budoucí verzi Windows. Pokud se s tímto problémem pracujete, můžete nás kontaktovat na adrese stepback@microsoft.com .

* Když ukládáte soubor s **laděním > IntelliTrace > uložíte relaci IntelliTrace** v režimu události a snímky, další data zachycená ze snímků nejsou v souboru. iTrace k dispozici. U událostí zarážek a krokovat se zobrazí stejné informace, jako kdyby byl soubor uložen pouze v režimu IntelliTrace Events.

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste se naučili, jak používat IntelliTrace krok zpět. Možná budete chtít získat další informace o dalších funkcích IntelliTrace.

> [!div class="nextstepaction"]
> [Funkce IntelliTrace](../debugger/intellitrace-features.md)
