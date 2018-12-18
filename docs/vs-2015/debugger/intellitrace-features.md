---
title: Funkce IntelliTrace | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: d1d7e949236067331408c6b9a8268891ff8b88db
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51817474"
---
# <a name="intellitrace-features"></a>Funkce IntelliTrace
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete zaznamenat události IntelliTrace a volá metodu vaší aplikace, který umožňuje zkontrolovat jeho stav (zásobník volání a místní proměnné hodnoty) v různých fázích provádění. Stačí obvyklým způsobem spustit ladění – nástroj IntelliTrace je ve výchozím nastavení zapnutá a zobrazí se informace, které nástroj IntelliTrace zaznamenává v novém **diagnostické nástroje** okně **události** kartu. Vyberte událost a klikněte na tlačítko **aktivovat historické ladění** zobrazíte zásobník volání a místní hodnoty pro tuto událost.  
  
 Podrobný popis najdete v tématu [návod: použití IntelliTrace](../debugger/walkthrough-using-intellitrace.md).  
  
 Nástroj IntelliTrace je k dispozici v edici Visual Studio Enterprise, ale ne v edicích Visual Studio Professional nebo Community.  
  
 Chcete-li ověřit, že nástroj IntelliTrace je zapnutý, otevřete **nástroje / Možnosti / IntelliTrace** stránka možností. **Povolení technologie IntelliTrace** by měl být ve výchozím nastavení zaškrtnuto.  
  
> [!NOTE]
>  Obor všechna nastavení na **IntelliTrace** stránka možností je sada Visual Studio jako celek, nikoli jednotlivé projekty nebo řešení. Změna těchto nastavení se vztahuje na všechny instance sady Visual Studio, všechny ladicí relace a všechny projekty nebo řešení.  
  
##  <a name="ChooseEvents"></a> Vyberte události, které nástroj IntelliTrace zaznamenává.  
 Můžete zapnout nebo vypnout zaznamenávání určitých událostí IntelliTrace.  
  
 Pokud ladíte, zastavte ladění. Přejděte na **nástroje / Možnosti / IntelliTrace nebo události IntelliTrace**. Zvolte událostí, které má IntelliTrace zaznamenávat.  
  
##  <a name="GoingFurther"></a> Shromažďovat události IntelliTrace a informací o volání  
 Tato možnost není povolena ve výchozím nastavení, ale nástroj IntelliTrace umí zaznamenat volání metody spolu s událostmi. Povolte shromažďování metoda volání přejít na **nástroje / Možnosti / IntelliTrace / Obecné**a vyberte **události IntelliTrace a informací o volání**.  
  
 To umožňuje zobrazit historii zásobníku volání, krokovat zpět a vpřed mezi voláními ve vašem kódu. Nástroj IntelliTrace zaznamenává data, jako jsou názvy metod, metoda vstupní a výstupní body a některé hodnoty parametrů a návratové hodnoty.  
  
> [!TIP]
>  Tato možnost není standardně povolená, protože přidá značné režijní náklady. Nejen IntelliTrace musí zachytit každé volání metody, které vaše aplikace provádí, ale má také řešit mnohem větší sadě dat při přechodu do režimu zobrazení na obrazovce nebo uložením na disk.  
>   
>  Můžete snížit nároky na výkon tak, že omezíte nástroj IntelliTrace zaznamenává. seznam událostí a udržováním počet modulů shromažďujete na minimum. Další informace najdete v tématu [řízení množství informací o volání nástroj IntelliTrace zaznamenává](../debugger/intellitrace-features.md#ControlCallData).  
  
### <a name="using-the-navigation-gutter"></a>Pomocí navigační ovládací prvek  
 Můžete použít navigační ovládací prvek, který se zobrazí nalevo od okna kódu. Pokud nevidíte navigační ovládací prvek, přejděte na **nástroje / Možnosti / IntelliTrace / pokročilé**a vyberte **zobrazit navigační ovládací prvek v režimu ladění**.  
  
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
  
###  <a name="ControlCallData"></a> Řízení množství informací o volání nástroj IntelliTrace zaznamenává  
 Ve výchozím nastavení nástroj IntelliTrace zaznamenává informace pro všechny moduly používané v řešení. Nástroj IntelliTrace můžete nastavit na zaznamenávat informace o voláních pouze u modulů, které vás zajímají. V **nástroje / Možnosti / IntelliTrace / moduly**, můžete určit moduly, které chcete zahrnout nebo moduly, které chcete vyloučit z nástroje IntelliTrace. IntelliTrace se shromažďuje pouze události, které pochází z modulů, které jste zadali, a volání metod, ke kterým došlo v rámci moduly se zajímáte.  
  
 Chcete-li přidat více modulů, použijte zástupný znak * na začátku nebo konci řetězce. V případě názvů modulů použijte názvy souborů, nikoli názvy sestavení. Není možné použít cesty k souborům.  
  
 Pokuste se zachovat počet modulů na minimum. Protože je méně dat, které se mají shromažďovat, dosahovat vyšších výkonů. Získáte také menší šumu v uživatelském rozhraní vzhledem k tomu je méně dat a absolvovat.  
  
##  <a name="SaveSession"></a> Ukládání dat IntelliTrace do souboru  
 Data shromážděná IntelliTrace můžete uložit na **ladění / IntelliTrace / uložit relaci IntelliTrace** při ladění a aplikace je ve stavu přerušení. Položka nabídky je zakázaná a není možné uložit data, která nástroj IntelliTrace se budou shromažďovat v Pokud je stále spuštěná aplikace nebo zastavení ladění.  
  
 Můžete nakonfigurovat IntelliTrace automaticky uloží do souboru tak, že přejdete do **nástroje / Možnosti / IntelliTrace / pokročilé** a vyberete **záznamy Store IntelliTrace v tomto adresáři**. Můžete také nakonfigurovat nastavení velikosti pro generovaný soubor, což způsobí, že nástroj IntelliTrace zapisovat přes starší data, pokud jí dojde místo. Visual Studio vytvoří dva soubory pro každou relaci IntelliTrace, když se automaticky uloží a proces hostování (vshost.exe) sady Visual Studio je zapnuté.  
  
> [!TIP]
>  Chcete-li ušetřit místo na disku vypněte ukládání souborů automaticky, když už nepotřebujete. Veškeré stávající soubory se neodstraní. Vždy můžete uložit do souboru na vyžádání v místní nabídce.  
  
 Při ukládání dat IntelliTrace do souboru získáte jeden soubor .itrace pro každý proces, který nástroj IntelliTrace shromažďuje ze. Pak můžete otevřít soubor .itrace v sadě Visual Studio tak, že přejdete do **souboru / otevřít / File** a vyberete soubor .itrace v dialogovém okně Otevřít soubor. Další informace najdete v tématu [použití uložených dat řešení IntelliTrace](../debugger/using-saved-intellitrace-data.md).  
  
## <a name="blogs"></a>Blogy  
 [Nástroj IntelliTrace v sadě Visual Studio Enterprise 2015](http://blogs.msdn.com/b/visualstudioalm/archive/2015/01/16/intellitrace-in-visual-studio-ultimate-2015.aspx)  
  
 [Názorný postup z živého ladění pomocí IntelliTrace v sadě Visual Studio 2015 (textový Editor)](http://blogs.msdn.com/b/visualstudioalm/archive/2015/01/16/walkthrough-of-live-debugging-using-intellitrace-in-visual-studio-2015-text-editor.aspx)  
  
 [Názorný postup z živého ladění pomocí IntelliTrace v sadě Visual Studio 2015 (sociální klub)](http://blogs.msdn.com/b/visualstudioalm/archive/2000/1/1/walkthrough-of-live-debugging-using-intellitrace-in-visual-studio-2015-social-club.aspx)  
  
 [IntelliTrace v sadě Visual Studio Enterprise 2015 nyní podporuje připojení!](http://blogs.msdn.com/b/visualstudioalm/archive/2015/05/14/intellitrace-in-visual-studio-enterprise-2015-now-supports-attach.aspx)  
  
 [Shromažďování dat ze služby systému windows pomocí samostatného Kolektoru IntelliTrace](http://blogs.msdn.com/b/visualstudioalm/archive/2015/05/14/collect-data-from-a-windows-service-using-the-intellitrace-standalone-collector.aspx)  
  
 [Úpravě plánu kolekce IntelliTrace](http://blogs.msdn.com/b/visualstudioalm/archive/2015/03/09/editing-the-intellitrace-collection-plan.aspx)  
  
 [Vlastní třídy TraceSource a ladění pomocí IntelliTrace](http://blogs.msdn.com/b/visualstudioalm/archive/2014/12/17/custom-tracesource-and-debugging-using-intellitrace.aspx)  
  
 [Spuštění samostatného Kolektoru IntelliTrace a fondy aplikací v rámci účtů služby Active Directory](http://blogs.msdn.com/b/visualstudioalm/archive/2014/12/22/intellitrace-standalone-collector-and-application-pools-running-under-active-directory-accounts.aspx)  
  
## <a name="forums"></a>Diskuzní fóra  
 [Ladicí program sady Visual Studio](http://go.microsoft.com/fwlink/?LinkId=262263)  
  
## <a name="videos"></a>Videa  
 [Prostředí IntelliTrace](https://channel9.msdn.com/Series/Visual-Studio-2015-Enterprise-Videos/IntelliTrace-Experience)  
  
 [Historické ladění pomocí nástroje IntelliTrace v sadě Microsoft Visual Studio Ultimate 2015](https://channel9.msdn.com/events/Ignite/2015/BRK3716)





