---
title: Funkce IntelliTrace | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
ms.assetid: 5ccc059c-6097-46b4-9d4b-34236c02d549
caps.latest.revision: 73
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: dc16094c98a912d073bd6b873ecb3d1b3b411d1e
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74298952"
---
# <a name="intellitrace-features"></a>Funkce IntelliTrace
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

IntelliTrace můžete použít k zaznamenání událostí a metod volání do vaší aplikace, což vám umožní prostudovat svůj stav (a hodnoty zásobníku volání a lokální proměnné) v různých fázích provádění. Stačí spustit ladění, protože standardně je ve výchozím nastavení zapnutá – IntelliTrace. informace IntelliTrace se zaznamenávají do nového **diagnostické nástroje** okna na kartě **události** . Vyberte událost a kliknutím na **aktivovat historické ladění** zobrazíte zásobník volání a místní údaje zaznamenané pro tuto událost.  
  
 Podrobný popis najdete v tématu [Návod: použití IntelliTrace](../debugger/walkthrough-using-intellitrace.md).  
  
 IntelliTrace je k dispozici v edici Visual Studio Enterprise, ale ne v edicích Visual Studio Professional nebo Community.  
  
 Pokud chcete potvrdit, že je IntelliTrace zapnutý, otevřete stránku možnosti **Nástroje/možnosti/IntelliTrace** . **Povolit IntelliTrace** by mělo být ve výchozím nastavení zaškrtnuté.  
  
> [!NOTE]
> Rozsah všech nastavení na stránce možnosti **IntelliTrace** je Visual Studio jako celek, ne jednotlivé projekty nebo řešení. Změna v těchto nastaveních platí pro všechny instance aplikace Visual Studio, všechny relace ladění a všechny projekty nebo řešení.  
  
## <a name="ChooseEvents"></a>Zvolit události, které IntelliTrace záznamy  
 Záznam pro konkrétní události IntelliTrace můžete zapnout nebo vypnout.  
  
 Pokud ladíte, zastavte ladění. Přejdete na **události nástroje/možnosti/IntelliTrace/IntelliTrace**. Vyberte události, které mají IntelliTrace zaznamenávat.  
  
## <a name="GoingFurther"></a>Shromažďovat události IntelliTrace a informace o voláních  
 Tato možnost není ve výchozím nastavení povolená, ale IntelliTrace může zaznamenat volání metod spolu s událostmi. Chcete-li povolit shromažďování volání metod, použijte možnost **Nástroje/možnosti/IntelliTrace/obecné**a vyberte **události IntelliTrace a informace o volání**.  
  
 To vám umožní zobrazit historii zásobníku volání a krokovat zpět a vpřed prostřednictvím volání ve vašem kódu. IntelliTrace zaznamenává data, jako jsou názvy metod, vstupní a výstupní body metody a některé hodnoty parametrů a návratové hodnoty.  
  
> [!TIP]
> Tato možnost není ve výchozím nastavení povolená, protože přináší značnou režii. Pouze IntelliTrace musí zachytit všechny metody, které vaše aplikace dělá, ale také musí zabývat s mnohem větším množstvím dat, když se na obrazovce zobrazí nebo trvale zachová na disk.  
>   
> Omezením výkonu můžete snížit nároky na výkon tím, že omezíte seznam událostí, které IntelliTrace záznamy, a zachováte tak minimální počet modulů, které shromažďujete. Další informace najdete v tématu [určení toho, kolik informací o volání IntelliTrace záznamy](../debugger/intellitrace-features.md#ControlCallData).  
  
### <a name="using-the-navigation-gutter"></a>Použití navigačního hřbetu  
 Můžete použít navigační hřbet, který se zobrazí nalevo od okna Code (kód). Pokud se navigační hřbet nezobrazuje, přejděte na **Nástroje/možnosti/IntelliTrace/Upřesnit**a vyberte **Zobrazit navigační tlačítko v režimu ladění**.  
  
 Navigační hřbet umožňuje přesunout vpřed a zpět prostřednictvím volání metod a událostí v historickém režimu ladění. Další informace o historických ladění naleznete v tématu [historická ladění](../debugger/historical-debugging.md). Má několik příkazů:  
  
|||  
|-|-|  
|**Zde nastavit kontext ladicího programu**|Nastavte kontext ladění na časový rámec volání, kde se zobrazí.<br /><br /> Tato ikona se zobrazí pouze v aktuálním zásobníku volání.|  
|**Vrátit se k volání webu**|Přesuňte ukazatel a kontext ladění zpátky na místo, kde byla volána aktuální funkce.<br /><br /> Pokud jste v režimu živého ladění, tento příkaz zapne historické ladění na. Pokud přejdete zpět k původnímu přerušení spuštění, bude ladění historických verzí vypnuto a je zapnuté živé ladění.|  
|**Přejít na předchozí volání nebo událost IntelliTrace**|Přesune ukazatel a kontext ladění zpátky na předchozí volání nebo událost.<br /><br /> Pokud jste v režimu živého ladění, tento příkaz zapne historické ladění.|  
|**Krokovat s**|Krok do aktuálně vybrané funkce.<br /><br /> Tento příkaz je k dispozici, pouze pokud jste v historickém režimu ladění.|  
|**Přejít na další volání nebo událost IntelliTrace**|Přesuňte ukazatel a kontext ladění na další volání nebo událost, pro kterou existuje IntelliTrace data.<br /><br /> Tento příkaz je k dispozici, pouze pokud jste v historickém režimu ladění.|  
|**Přejít do živého režimu**|Vrátí se do režimu živého ladění.|  
  
### <a name="search-for-a-line-or-method-in-intellitrace"></a>Hledání řádku nebo metody v IntelliTrace  
 Metody můžete hledat pouze v případě, že byly povoleny informace o volání metody. Můžete hledat v historii IntelliTrace konkrétního řádku nebo metody. I když je spuštění ladicího programu zastaveno, klikněte pravým tlačítkem myši uvnitř těla funkce, aby se zobrazila kontextová nabídka, a klikněte buď na **Hledat tento řádek v IntelliTrace** , nebo **vyhledejte tuto metodu v IntelliTrace**.  
  
### <a name="ControlCallData"></a>Určit, kolik informací o volání IntelliTrace záznamy  
 Ve výchozím nastavení IntelliTrace zaznamenává informace pro všechny moduly, které vaše řešení používá. Můžete nastavit IntelliTrace na záznam informací o volání pouze pro moduly, které vás zajímají. V **nabídce Nástroje/možnosti/IntelliTrace/moduly**můžete určit moduly, které mají být zahrnuty, nebo moduly, které mají být vyloučeny z IntelliTrace. IntelliTrace shromáždí pouze události, které pocházejí z určených modulů, a volání metody, k nimž došlo v rámci modulů, které vás zajímají.  
  
 Chcete-li přidat více modulů, použijte zástupný znak * na začátku nebo konci řetězce. V případě názvů modulů použijte názvy souborů, nikoli názvy sestavení. Není možné použít cesty k souborům.  
  
 Snažte se udržet počet modulů na minimum. Získáte lepší výkon, protože se shromažďují méně dat. V uživatelském rozhraní získáte také menší šum, protože je k dispozici méně dat, než je možné projít.  
  
## <a name="SaveSession"></a>Ukládání dat IntelliTrace do souboru  
 Můžete uložit data, která IntelliTrace shromáždila při ladění **/IntelliTrace/ukládání relace IntelliTrace** během ladění, a aplikace je ve stavu přerušení. Položka nabídky je zakázaná a nebudete moct uložit data IntelliTrace, pokud je aplikace pořád spuštěná, nebo pokud jste zastavili ladění.  
  
 IntelliTrace můžete nakonfigurovat tak, aby se automaticky ukládaly do souboru, a to tak, že v tomto adresáři kliknete na **Nástroje/možnosti/IntelliTrace/Upřesnit** a vyberete **ukládat IntelliTrace záznamy**. Pro generovaný soubor můžete také nakonfigurovat velikost sady, která způsobí, že IntelliTrace při vynechání volného místa zapisuje přes starší data. Visual Studio vytvoří dva soubory pro každou IntelliTrace relaci, když jsou uloženy automaticky a hostující proces sady Visual Studio (vshost. exe) je zapnutý.  
  
> [!TIP]
> Pokud chcete ušetřit místo na disku, vypněte ukládání souborů automaticky, když je už nepotřebujete. Existující soubory nebudou smazány. V místní nabídce můžete vždycky ukládat do souboru na vyžádání.  
  
 Když ukládáte IntelliTrace data do souboru, získáte jeden soubor. iTrace pro každý proces, ze kterého byl IntelliTrace shromážděn. Pak můžete soubor. iTrace otevřít v aplikaci Visual Studio tak, že v dialogovém okně otevřít soubor zadáte **soubor/otevřít/soubor** a vyberete soubor. iTrace. Další informace najdete v tématu [použití uložených IntelliTrace dat](../debugger/using-saved-intellitrace-data.md).  
  
## <a name="blogs"></a>Blogy  
 [IntelliTrace v Visual Studio Enterprise 2015](https://devblogs.microsoft.com/devops/intellitrace-in-visual-studio-ultimate-2015/)  
  
 [Návod k živému ladění pomocí IntelliTrace v aplikaci Visual Studio 2015 (textový editor)](https://devblogs.microsoft.com/devops/walkthrough-of-live-debugging-using-intellitrace-in-visual-studio-2015-text-editor/)  
  
 [Návod k živému ladění pomocí IntelliTrace ve Visual Studiu 2015 (sociální klub)](https://devblogs.microsoft.com/devops/walkthrough-of-live-debugging-using-intellitrace-in-visual-studio-2015-social-club/)  
  
 [IntelliTrace v Visual Studio Enterprise 2015 teď podporuje připojení!](https://devblogs.microsoft.com/devops/intellitrace-in-visual-studio-enterprise-2015-now-supports-attach/)  
  
 [Shromažďování dat ze služby systému Windows pomocí samostatného kolektoru IntelliTrace](https://devblogs.microsoft.com/devops/collect-data-from-a-windows-service-using-the-intellitrace-standalone-collector/)  
  
 [Úprava plánu kolekce IntelliTrace](https://devblogs.microsoft.com/devops/editing-the-intellitrace-collection-plan/)  
  
 [Vlastní TraceSource a ladění pomocí IntelliTrace](https://devblogs.microsoft.com/devops/custom-tracesource-and-debugging-using-intellitrace/)  
  
 [IntelliTrace samostatnou kolekci a fondy aplikací spuštěné v rámci účtů Active Directory](https://devblogs.microsoft.com/devops/intellitrace-standalone-collector-and-application-pools-running-under-active-directory-accounts/)  
  
## <a name="forums"></a>Fóra  
 [Ladicí program sady Visual Studio](https://go.microsoft.com/fwlink/?LinkId=262263)  
  
## <a name="videos"></a>Videa  
 [Prostředí IntelliTrace](https://channel9.msdn.com/Series/Visual-Studio-2015-Enterprise-Videos/IntelliTrace-Experience)  
  
 [Historické ladění pomocí IntelliTrace v Microsoft Visual Studio Ultimate 2015](https://channel9.msdn.com/events/Ignite/2015/BRK3716)
