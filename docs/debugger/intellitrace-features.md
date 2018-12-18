---
title: Funkce IntelliTrace | Dokumentace Microsoftu
ms.custom: ''
ms.date: 09/19/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- IntelliTrace, debugging with events
- IntelliTrace, recording execution history
- debugging [Visual Studio ALM], recording execution history
- IntelliTrace, turn off
- IntelliTrace, navigating event and call history
- IntelliTrace, saving your session
- IntelliTrace, enabling
- IntelliTrace, start debugging
- IntelliTrace, debugging with events and call information
- IntelliTrace, disabling
- IntelliTrace, turn on
- debugging [Visual Studio ALM], IntelliTrace
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 59ff5fa898aa808c99dd5f52df1605336edd1694
ms.sourcegitcommit: a749c287ec7d54148505978e8ca55ccd406b71ee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/21/2018
ms.locfileid: "46542465"
---
# <a name="intellitrace-features"></a>Funkce IntelliTrace

Můžete zaznamenat události IntelliTrace a volá metodu vaší aplikace, který umožňuje zkontrolovat jeho stav (zásobník volání a místní proměnné hodnoty) v různých fázích provádění. Stačí obvyklým způsobem spustit ladění – nástroj IntelliTrace je ve výchozím nastavení zapnutá a zobrazí se informace, které nástroj IntelliTrace zaznamenává v novém **diagnostické nástroje** okně **události** kartu. Vyberte událost a klikněte na tlačítko **aktivovat historické ladění** zobrazíte zásobník volání a místní hodnoty pro tuto událost.

Podrobný popis najdete v tématu [návod: použití IntelliTrace](../debugger/walkthrough-using-intellitrace.md).

Nástroj IntelliTrace je k dispozici v edici Visual Studio Enterprise, ale ne v edicích Visual Studio Professional nebo Community.

Pokud chcete potvrdit, že nástroj IntelliTrace je zapnutý, otevřete **nástroje > Možnosti > Nástroje IntelliTrace** stránka možností. **Povolení technologie IntelliTrace** by měl být ve výchozím nastavení zaškrtnuto.

> [!NOTE]
> Obor všechna nastavení na **IntelliTrace** stránka možností je sada Visual Studio jako celek, nikoli jednotlivé projekty nebo řešení. Změna těchto nastavení se vztahuje na všechny instance sady Visual Studio, všechny ladicí relace a všechny projekty nebo řešení.

## <a name="ChooseEvents"></a> Vyberte události, které nástroj IntelliTrace zaznamenává (pouze pro spravovaný kód)

Můžete zapnout nebo vypnout zaznamenávání určitých událostí IntelliTrace.

Pokud ladíte, zastavte ladění. Přejděte na **nástroje > Možnosti > Nástroje IntelliTrace > události IntelliTrace**. Zvolte událostí, které má IntelliTrace zaznamenávat.

## <a name="Snapshots"></a> Shromažďovat snímky

Tato možnost není povolena ve výchozím nastavení, ale nástroj IntelliTrace můžete zachytit snímek vaší aplikace v každé události krok zarážky a ladicí program a tyto snímky můžete zobrazit v stará ladicí relace. Snímek poskytuje přehled stavu vaší celou aplikaci. Chcete-li povolit zachytávání snímků, přejděte na **nástroje > Možnosti > Nástroje IntelliTrace > Obecné**a vyberte **snímky IntelliTrace (spravovaný a nativní)**. Další informace najdete v tématu [kontrolovat předchozí nové aplikace pomocí nástroje IntelliTrace](../debugger/view-historical-application-state.md)

Snímky jsou k dispozici v sadě Visual Studio Enterprise 2017 verze 15.5 nebo novější a vyžaduje aktualizaci Windows 10 Anniversary Update nebo novější.  Pro aplikace .NET Core a ASP.NET Core se vyžaduje Visual Studio Enterprise 2017 verze 15.7. Pro nativní aplikace určené pro Windows, Visual Studio Enterprise 2017 verzi 15.9 ve verzi Preview 2 je povinný.

## <a name="GoingFurther"></a> Shromažďovat události IntelliTrace a informací o (pouze pro spravovaný kód) volání

Tato možnost není povolena ve výchozím nastavení, ale nástroj IntelliTrace umí zaznamenat volání metody spolu s událostmi. Povolte shromažďování metoda volání přejít na **nástroje > Možnosti > Nástroje IntelliTrace > Obecné**a vyberte **události IntelliTrace a informací o (režim pouze spravovaný) volání**.

Informace o volání není aktuálně k dispozici pro aplikace .NET Core a ASP.NET Core. 

To umožňuje zobrazit historii zásobníku volání, krokovat zpět a vpřed mezi voláními ve vašem kódu. Nástroj IntelliTrace zaznamenává data, jako jsou názvy metod, metoda vstupní a výstupní body a některé hodnoty parametrů a návratové hodnoty.

> [!TIP]
> Tato možnost není standardně povolená, protože přidá značné režijní náklady. Nejen IntelliTrace musí zachytit každé volání metody, které vaše aplikace provádí, ale má také řešit mnohem větší sadě dat při přechodu do režimu zobrazení na obrazovce nebo uložením na disk.
>
> Můžete snížit nároky na výkon tak, že omezíte nástroj IntelliTrace zaznamenává. seznam událostí a udržováním počet modulů shromažďujete na minimum. Další informace najdete v tématu [řízení množství informací o volání nástroj IntelliTrace zaznamenává](../debugger/intellitrace-features.md#ControlCallData).

### <a name="use-the-navigation-gutter"></a>Použijte navigační ovládací prvek

Můžete použít navigační ovládací prvek, který se zobrazí nalevo od okna kódu. Pokud nevidíte navigační ovládací prvek, přejděte na **nástroje > Možnosti > Nástroje IntelliTrace > Upřesnit**a vyberte **zobrazit navigační ovládací prvek v režimu ladění**.

Navigační ovládací prvek umožňuje přesunout vpřed a zpět prostřednictvím volání metody a události v režimu historické ladění. Další informace o historické ladění, naleznete v tématu [historické ladění](../debugger/historical-debugging.md). Má řadu příkazů:

|||
|-|-|
|**Zde nastavit kontext ladicího programu**|Nastavte kontext ladění na časový rámec volání, kde se zobrazí.<br /><br /> Tato ikona se zobrazuje jenom na aktuální zásobník volání.|
|**Vrátit se k volání webu**|Přesune ukazatel a kontext ladění zpět do kde byla volána aktuální funkce.<br /><br /> Pokud jste v režimu živého ladění, tento příkaz zapne historické ladění. Pokud přejdete zpět na původní přerušení provádění, je vypnutá historické ladění a živé ladění je zapnuté.|
|**Přejít na předchozí volání nebo událost IntelliTrace**|Přesune ukazatel a kontext ladění zpět na předchozí volání nebo událost.<br /><br /> Pokud jste v režimu živého ladění, tento příkaz zapne historické ladění.|
|**Vstoupit**|Krokovat s vnořením aktuálně vybrané funkce.<br /><br /> Tento příkaz je k dispozici pouze v případě, že jste v režimu historické ladění.|
|**Přejít na další volání nebo událost IntelliTrace**|Přesune ukazatel a kontext ladění na další volání nebo událost, pro které nástroj IntelliTrace dat existuje.<br /><br /> Tento příkaz je k dispozici pouze v případě, že jste v režimu historické ladění.|
|**Přejít do živého režimu**|Vraťte se do režimu živého ladění.|

### <a name="search-for-a-line-or-method-in-intellitrace"></a>Vyhledejte řádek nebo metody v IntelliTrace

Metody můžete prohledávat pouze v případě, že se povolila informací o volání metody. Můžete prohledat historii nástroje IntelliTrace na konkrétní řádek nebo metodu. Při zastavení spuštění ladicího programu, klikněte pravým tlačítkem uvnitř těla funkce Zobrazit kontextovou nabídku a klikněte na možnost **vyhledávání pro tento řádek v IntelliTrace** nebo **vyhledávání pro tuto metodu v IntelliTrace**.

### <a name="ControlCallData"></a> Řízení množství informací o volání nástroj IntelliTrace zaznamenává

Ve výchozím nastavení nástroj IntelliTrace zaznamenává informace pro všechny moduly používané v řešení. Nástroj IntelliTrace můžete nastavit na zaznamenávat informace o voláních pouze u modulů, které vás zajímají. V **nástroje > Možnosti > Nástroje IntelliTrace > moduly**, můžete určit moduly, které chcete zahrnout nebo moduly, které chcete vyloučit z nástroje IntelliTrace. IntelliTrace se shromažďuje pouze události, které pochází z modulů, které jste zadali, a volání metod, ke kterým došlo v rámci moduly se zajímáte.

Chcete-li přidat více modulů, použijte zástupný znak * na začátku nebo konci řetězce. V případě názvů modulů použijte názvy souborů, nikoli názvy sestavení. Není možné použít cesty k souborům.

Pokuste se zachovat počet modulů na minimum. Protože je méně dat, které se mají shromažďovat, dosahovat vyšších výkonů. Získáte také menší šumu v uživatelském rozhraní vzhledem k tomu je méně dat a absolvovat.

## <a name="SaveSession"></a> Ukládání dat IntelliTrace do souboru

Data shromážděná IntelliTrace můžete uložit na **ladit > IntelliTrace > Uložit relaci IntelliTrace** při ladění a aplikace je ve stavu přerušení. Položka nabídky je zakázaná a není možné uložit data, která nástroj IntelliTrace se budou shromažďovat v Pokud je stále spuštěná aplikace nebo zastavení ladění.

Můžete nakonfigurovat IntelliTrace automaticky uloží do souboru tak, že přejdete do **nástroje > Možnosti > Nástroje IntelliTrace > Upřesnit** a vyberete **záznamy Store IntelliTrace v tomto adresáři**. Můžete také nakonfigurovat nastavení velikosti pro generovaný soubor, což způsobí, že nástroj IntelliTrace zapisovat přes starší data, pokud jí dojde místo. Visual Studio vytvoří dva soubory pro každou relaci IntelliTrace, když se automaticky uloží a proces hostování (vshost.exe) sady Visual Studio je zapnuté.

> [!TIP]
> Chcete-li ušetřit místo na disku vypněte ukládání souborů automaticky, když už nepotřebujete. Veškeré stávající soubory se neodstraní. Vždy můžete uložit do souboru na vyžádání v místní nabídce.

Při ukládání dat IntelliTrace do souboru získáte jeden soubor .itrace pro každý proces, který nástroj IntelliTrace shromažďuje ze. Pak můžete otevřít soubor .itrace v sadě Visual Studio tak, že přejdete do **soubor > Otevřít > soubor** a vyberete soubor .itrace v dialogovém okně Otevřít soubor. Další informace najdete v tématu [použití uložených dat řešení IntelliTrace](../debugger/using-saved-intellitrace-data.md).

## <a name="blogs"></a>Blogy

[Nástroj IntelliTrace v sadě Visual Studio Enterprise 2015](https://blogs.msdn.microsoft.com/devops/2015/01/16/intellitrace-in-visual-studio-ultimate-2015/)

[Názorný postup z živého ladění pomocí IntelliTrace v sadě Visual Studio 2015 (textový Editor)](https://blogs.msdn.microsoft.com/devops/2015/01/16/walkthrough-of-live-debugging-using-intellitrace-in-visual-studio-2015-text-editor/)

[Názorný postup z živého ladění pomocí IntelliTrace v sadě Visual Studio 2015 (sociální klub)](https://blogs.msdn.microsoft.com/devops/2015/04/29/walkthrough-of-live-debugging-using-intellitrace-in-visual-studio-2015-social-club/)

[IntelliTrace v sadě Visual Studio Enterprise 2015 nyní podporuje připojení!](https://blogs.msdn.microsoft.com/devops/2015/05/14/intellitrace-in-visual-studio-enterprise-2015-now-supports-attach/)

[Shromažďování dat ze služby systému windows pomocí samostatného Kolektoru IntelliTrace](https://blogs.msdn.microsoft.com/devops/2015/05/14/collect-data-from-a-windows-service-using-the-intellitrace-standalone-collector/)

[Úpravě plánu kolekce IntelliTrace](https://blogs.msdn.microsoft.com/devops/2015/03/09/editing-the-intellitrace-collection-plan/)

[Vlastní třídy TraceSource a ladění pomocí IntelliTrace](https://blogs.msdn.microsoft.com/devops/2014/12/16/custom-tracesource-and-debugging-using-intellitrace/)

[Spuštění samostatného Kolektoru IntelliTrace a fondy aplikací v rámci účtů služby Active Directory](https://blogs.msdn.microsoft.com/devops/2014/12/22/intellitrace-standalone-collector-and-application-pools-running-under-active-directory-accounts/)

## <a name="forums"></a>Diskuzní fóra

[Ladicí program sady Visual Studio](http://go.microsoft.com/fwlink/?LinkId=262263)

## <a name="videos"></a>Videa

[Prostředí IntelliTrace](https://channel9.msdn.com/Series/Visual-Studio-2015-Enterprise-Videos/IntelliTrace-Experience)

[Historické ladění pomocí nástroje IntelliTrace v sadě Microsoft Visual Studio Ultimate 2015](https://channel9.msdn.com/events/Ignite/2015/BRK3716)
