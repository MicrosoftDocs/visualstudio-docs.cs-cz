---
title: Funkce IntelliTrace | Microsoft Docs
ms.date: 09/19/2018
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1ac7ca0e59a479aff3386486d2ceaf061038db68
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85536575"
---
# <a name="intellitrace-features-c-visual-basic-c"></a>Funkce IntelliTrace (C#, Visual Basic, C++)

IntelliTrace můžete použít k zaznamenání událostí a metod volání do vaší aplikace, což vám umožní prostudovat svůj stav (a hodnoty zásobníku volání a lokální proměnné) v různých fázích provádění. Stačí spustit ladění, protože standardně je ve výchozím nastavení zapnutá – IntelliTrace. informace IntelliTrace se zaznamenávají do nového **diagnostické nástroje** okna na kartě **události** . Vyberte událost a kliknutím na **aktivovat historické ladění** zobrazíte zásobník volání a místní údaje zaznamenané pro tuto událost.

Podrobný popis najdete v tématu [Návod: použití IntelliTrace](../debugger/walkthrough-using-intellitrace.md).

IntelliTrace je k dispozici v edici Visual Studio Enterprise, ale ne v edicích Visual Studio Professional nebo Community.

Chcete-li zkontrolovat, zda je IntelliTrace zapnutý, otevřete stránku **> nástroje možnosti > možnosti IntelliTrace** . **Povolit IntelliTrace** by mělo být ve výchozím nastavení zaškrtnuté.

> [!NOTE]
> Rozsah všech nastavení na stránce možnosti **IntelliTrace** je Visual Studio jako celek, ne jednotlivé projekty nebo řešení. Změna v těchto nastaveních platí pro všechny instance aplikace Visual Studio, všechny relace ladění a všechny projekty nebo řešení.

## <a name="choose-the-events-that-intellitrace-records-c-visual-basic"></a><a name="ChooseEvents"></a>Zvolit události, které IntelliTrace záznamy (C#, Visual Basic)

Záznam pro konkrétní události IntelliTrace můžete zapnout nebo vypnout.

Pokud ladíte, zastavte ladění. V **nabídce nástroje > možnosti > události IntelliTrace > IntelliTrace**. Vyberte události, které mají IntelliTrace zaznamenávat.

## <a name="collect-snapshots-c-visual-basic-c"></a><a name="Snapshots"></a>Shromáždit snímky (C#, Visual Basic, C++)

Tato možnost není ve výchozím nastavení povolená, ale IntelliTrace může zachytit snímky vaší aplikace při každé události zarážky a kroku ladicího programu a tyto snímky můžete zobrazit v historické relaci ladění. Snímek vám poskytne přehled o celém stavu aplikace. Pokud chcete povolit zachytávání snímků, v nabídce **nástroje > možnosti > IntelliTrace > obecné**a vyberte **snímky IntelliTrace (spravované a nativní)**. Další informace najdete v tématu [Kontrola předchozích stavů aplikace pomocí IntelliTrace](../debugger/view-historical-application-state.md).

Snímky jsou k dispozici v Visual Studio Enterprise 2017 verze 15,5 a vyšší a vyžaduje aktualizaci Windows 10 pro výročí nebo novější.  Pro aplikace .NET Core a ASP.NET Core se vyžaduje Visual Studio Enterprise 2017 verze 15,7. Pro nativní aplikace cílené na Windows se vyžaduje Visual Studio Enterprise 2017 verze 15,9 Preview 2.

## <a name="collect-intellitrace-events-and-call-information-c-visual-basic"></a><a name="GoingFurther"></a>Shromažďovat události IntelliTrace a informace o volání (C#, Visual Basic)

Tato možnost není ve výchozím nastavení povolená, ale IntelliTrace může zaznamenat volání metod spolu s událostmi. Chcete-li povolit shromažďování volání metody, přečtěte si **nástroje > možnosti > IntelliTrace > obecné**a vyberte **události IntelliTrace a informace o volání (pouze spravované)**.

Informace o voláních nejsou aktuálně k dispozici pro aplikace .NET Core a ASP.NET Core.

To vám umožní zobrazit historii zásobníku volání a krokovat zpět a vpřed prostřednictvím volání ve vašem kódu. IntelliTrace zaznamenává data, jako jsou názvy metod, vstupní a výstupní body metody a některé hodnoty parametrů a návratové hodnoty.

> [!TIP]
> Tato možnost není ve výchozím nastavení povolená, protože přináší značnou režii. Pouze IntelliTrace musí zachytit všechny metody, které vaše aplikace dělá, ale také musí zabývat s mnohem větším množstvím dat, když se na obrazovce zobrazí nebo trvale zachová na disk.
>
> Omezením výkonu můžete snížit nároky na výkon tím, že omezíte seznam událostí, které IntelliTrace záznamy, a zachováte tak minimální počet modulů, které shromažďujete. Další informace najdete v tématu [určení toho, kolik informací o volání IntelliTrace záznamy](../debugger/intellitrace-features.md#ControlCallData).

### <a name="use-the-navigation-gutter"></a>Použití navigačních hřbetů

Můžete použít navigační hřbet, který se zobrazí nalevo od okna Code (kód). Pokud se navigační hřbet nezobrazuje, přejděte do části **nástroje > možnosti > IntelliTrace > Upřesnit**a **v režimu ladění vyberte Zobrazit navigační**okraj.

Navigační hřbet umožňuje přesunout vpřed a zpět prostřednictvím volání metod a událostí v historickém režimu ladění. Další informace o historických ladění naleznete v tématu [historická ladění](../debugger/historical-debugging.md). Má několik příkazů:

|Příkaz|Popis|
|-|-|
|**Zde nastavit kontext ladicího programu**|Nastavte kontext ladění na časový rámec volání, kde se zobrazí.<br /><br /> Tato ikona se zobrazí pouze v aktuálním zásobníku volání.|
|**Vrátit se k volání webu**|Přesuňte ukazatel a kontext ladění zpátky na místo, kde byla volána aktuální funkce.<br /><br /> Pokud jste v režimu živého ladění, tento příkaz zapne historické ladění na. Pokud přejdete zpět k původnímu přerušení spuštění, bude ladění historických verzí vypnuto a je zapnuté živé ladění.|
|**Přejít na předchozí volání nebo událost IntelliTrace**|Přesune ukazatel a kontext ladění zpátky na předchozí volání nebo událost.<br /><br /> Pokud jste v režimu živého ladění, tento příkaz zapne historické ladění.|
|**Krokovat s**|Krok do aktuálně vybrané funkce.<br /><br /> Tento příkaz je k dispozici, pouze pokud jste v historickém režimu ladění.|
|**Přejít na další volání nebo událost IntelliTrace**|Přesuňte ukazatel a kontext ladění na další volání nebo událost, pro kterou existuje IntelliTrace data.<br /><br /> Tento příkaz je k dispozici, pouze pokud jste v historickém režimu ladění.|
|**Přejít do živého režimu**|Vrátí se do režimu živého ladění.|

### <a name="search-for-a-line-or-method-in-intellitrace"></a>Hledání řádku nebo metody v IntelliTrace

Metody můžete hledat pouze v případě, že byly povoleny informace o volání metody. Můžete hledat v historii IntelliTrace konkrétního řádku nebo metody. I když je spuštění ladicího programu zastaveno, klikněte pravým tlačítkem myši uvnitř těla funkce, aby se zobrazila kontextová nabídka, a klikněte buď na **Hledat tento řádek v IntelliTrace** , nebo **vyhledejte tuto metodu v IntelliTrace**.

### <a name="control-how-much-call-information-intellitrace-records"></a><a name="ControlCallData"></a>Určit, kolik informací o volání IntelliTrace záznamy

Ve výchozím nastavení IntelliTrace zaznamenává informace pro všechny moduly, které vaše řešení používá. Můžete nastavit IntelliTrace na záznam informací o volání pouze pro moduly, které vás zajímají. V části **nástroje > možnosti > IntelliTrace > moduly**můžete určit moduly, které mají být zahrnuty, nebo moduly, které mají být vyloučeny z IntelliTrace. IntelliTrace shromáždí pouze události, které pocházejí z určených modulů, a volání metody, k nimž došlo v rámci modulů, které vás zajímají.

Chcete-li přidat více modulů, použijte zástupný znak * na začátku nebo konci řetězce. V případě názvů modulů použijte názvy souborů, nikoli názvy sestavení. Není možné použít cesty k souborům.

Snažte se udržet počet modulů na minimum. Získáte lepší výkon, protože se shromažďují méně dat. V uživatelském rozhraní získáte také menší šum, protože je k dispozici méně dat, než je možné projít.

## <a name="save-intellitrace-data-to-file-c-visual-basic-c"></a><a name="SaveSession"></a>Ukládat IntelliTrace data do souboru (C#, Visual Basic, C++)

Data, která IntelliTrace shromáždila, můžete uložit do **ladění > IntelliTrace > při ladění ukládat relaci IntelliTrace** a aplikace je ve stavu přerušení. Položka nabídky je zakázaná a nebudete moct uložit data IntelliTrace, pokud je aplikace pořád spuštěná, nebo pokud jste zastavili ladění.

IntelliTrace můžete nakonfigurovat tak, aby se automaticky ukládaly do souboru, a to tak, že v **nabídce nástroje > možnosti > IntelliTrace > Upřesnit** a **v tomto adresáři vyberete Uložit záznamy IntelliTrace**. Pro generovaný soubor můžete také nakonfigurovat velikost sady, která způsobí, že IntelliTrace při vynechání volného místa zapisuje přes starší data. Visual Studio vytvoří dva soubory pro každou IntelliTrace relaci, když jsou uloženy automaticky a hostitelský proces sady Visual Studio (vshost.exe) je zapnutý.

> [!TIP]
> Pokud chcete ušetřit místo na disku, vypněte ukládání souborů automaticky, když je už nepotřebujete. Existující soubory nebudou smazány. V místní nabídce můžete vždycky ukládat do souboru na vyžádání.

Když ukládáte IntelliTrace data do souboru, získáte jeden soubor. iTrace pro každý proces, ze kterého byl IntelliTrace shromážděn. Pak můžete soubor. iTrace otevřít v aplikaci Visual Studio tak, že na **soubor > otevřete > soubor** a v dialogovém okně otevřít soubor vyberete soubor. iTrace. Další informace najdete v tématu [použití uložených IntelliTrace dat](../debugger/using-saved-intellitrace-data.md).

## <a name="blogs"></a>Blogy

[IntelliTrace v Visual Studio Enterprise 2015](https://devblogs.microsoft.com/devops/intellitrace-in-visual-studio-ultimate-2015/)

[Návod k živému ladění pomocí IntelliTrace v aplikaci Visual Studio 2015 (textový editor)](https://devblogs.microsoft.com/devops/walkthrough-of-live-debugging-using-intellitrace-in-visual-studio-2015-text-editor/)

[Návod k živému ladění pomocí IntelliTrace ve Visual Studiu 2015 (sociální klub)](https://devblogs.microsoft.com/devops/walkthrough-of-live-debugging-using-intellitrace-in-visual-studio-2015-social-club/)

[IntelliTrace v Visual Studio Enterprise 2015 teď podporuje připojení!](https://devblogs.microsoft.com/devops/intellitrace-in-visual-studio-enterprise-2015-now-supports-attach/)

[Shromažďování dat ze služby systému Windows pomocí samostatného kolektoru IntelliTrace](https://devblogs.microsoft.com/devops/collect-data-from-a-windows-service-using-the-intellitrace-standalone-collector/)

[Úprava plánu kolekce IntelliTrace](https://devblogs.microsoft.com/devops/editing-the-intellitrace-collection-plan)

[Vlastní TraceSource a ladění pomocí IntelliTrace](https://devblogs.microsoft.com/devops/custom-tracesource-and-debugging-using-intellitrace/)

[IntelliTrace samostatnou kolekci a fondy aplikací spuštěné v rámci účtů Active Directory](https://devblogs.microsoft.com/devops/intellitrace-standalone-collector-and-application-pools-running-under-active-directory-accounts/)

## <a name="forums"></a>Fóra

[Visual Studio – ladicí program](https://social.msdn.microsoft.com/Forums/en-US/home)

## <a name="videos"></a>Videa

[Prostředí IntelliTrace](https://channel9.msdn.com/Series/Visual-Studio-2015-Enterprise-Videos/IntelliTrace-Experience)

[Historické ladění pomocí IntelliTrace v Microsoft Visual Studio Ultimate 2015](https://channel9.msdn.com/events/Ignite/2015/BRK3716)
