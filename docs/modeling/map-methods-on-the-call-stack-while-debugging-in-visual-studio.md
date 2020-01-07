---
title: Mapování metod v zásobníku volání při ladění
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.progression.debugwithcodemaps
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- call stacks, code maps
- Call Stack window, mapping calls
- debugging [Visual Studio], diagramming the call stack
- call stacks, mapping
- Call Stack window, visualizing
- debugging code visually
- debugging [Visual Studio], mapping the call stack
- call stacks, visualizing
- debugging, code maps
- Call Stack window, tracing calls visually
- Call Stack window, show on code map
- debugging [Visual Studio], tracing the call stack visually
- debugging [Visual Studio], visualizing the call stack
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4a918cc94cd242c74b672ff65c3d5093f111a25f
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593301"
---
# <a name="map-methods-on-the-call-stack-while-debugging-in-visual-studio"></a>Mapování metod v zásobníku volání při ladění v sadě Visual Studio

Vytvořte mapu kódu pro vizuální sledování zásobníku volání během ladění. Můžete si dělat poznámky na mapě ke sledování kódu činnosti tak, abyste se mohli zaměřit na hledání chyb.

 ![Ladění se zásobníky volání na mapách kódu](../debugger/media/debuggermap_overview.png)

 Budete potřebovat:

 ::: moniker range="vs-2017"

- [Visual Studio Enterprise](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)

::: moniker-end

::: moniker range="vs-2019"

- [Visual Studio Enterprise](https://visualstudio.microsoft.com/downloads)

::: moniker-end

- Kód, který lze ladit, jako je Visual C#, Visual Basic, C++, JavaScript nebo X ++

  Další informace:

- [Video: Vizuální ladění díky integraci ladicího programu mapy kódu (kanál 9)](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012Debug-visually-with-Code-Map-debugger-integration)

- [Mapování zásobníku volání](#MapStack)

- [Tvorba poznámek o kódu](#MakeNotes)

- [Aktualizace mapy s následujícím zásobníkem volání.](#UpdateMap)

- [Přidání souvisejícího kódu do mapy](#AddRelatedCode)

- [Najít chyby pomocí mapy](#FindBugs)

- [FUNKCE Q &AMP; A](#QA)

  Podrobnosti příkazů a akcí, které můžete použít při práci s mapami kódu najdete v tématu [Procházet a uspořádání map kódu](../modeling/browse-and-rearrange-code-maps.md).

## <a name="MapStack"></a> Mapování zásobníku volání

1. Spusťte ladění. (Klávesnice: **F5**)

2. Až se vaše aplikace přejde do režimu přerušení nebo přejdete na funkci, zvolte **mapy kódu**. (Klávesnice: **Ctrl** + **Shift** +  **`** )

     ![Vyberte mapu kódu pro spuštění mapování zásobníku volání](../debugger/media/debuggermap_choosecodemap.png)

     Aktuální aktuální zásobník volání se zobrazí oranžově na mapě nového kódu:

     ![Zobrazit zásobník volání na mapě kódu](../debugger/media/debuggermap_seeundocallstack.png)

     Na mapě se automaticky aktualizovat, když budete pokračovat v ladění. Zobrazit [aktualizace mapy s následujícím zásobníkem volání](#UpdateMap).

## <a name="MakeNotes"></a> Tvorba poznámek o kódu

 Přidejte komentáře pro sledování, co se děje v kódu. Chcete-li přidat nový řádek v komentáři, stiskněte **Shift + Return**.

 ![Přidat komentář do zásobníku volání na mapě kódu](../debugger/media/debuggermap_addcomment.png)

## <a name="UpdateMap"></a> Aktualizace mapy s následujícím zásobníkem volání.

 Spuštění vaší aplikace na další zarážku nebo krok do funkce. Mapování přidá nový zásobník volání.

 ![Aktualizace mapy kódu s následujícím zásobníkem volání.](../debugger/media/debuggermap_addclearcallstack.png)

## <a name="AddRelatedCode"></a> Přidání souvisejícího kódu do mapy

 Nyní máte k dispozici mapu – co dále? Pokud pracujete s C# nebo Visual Basic, přidejte položky, jako je například pole, vlastnosti a jiné metody, můžete sledovat, co se děje v kódu.

 Poklepejte na metodu a zobrazte její definici kódu tak, nebo použijte místní nabídku pro metodu. (Klávesnice: Vyberte metodu na mapě a stiskněte klávesu **F12**)

 ![Přejít k definici kódu pro metodu na mapě kódu](../debugger/media/debuggermap_gotocodedefinition.png)

 Přidejte položky, které chcete sledovat na mapě.

 ![Zobrazit pole v metodu na mapě kódu zásobníku volání](../debugger/media/debuggermap_showfields.png)

> [!NOTE]
> Ve výchozím nastavení přidávání položek do mapy také přidá nadřazené uzly skupiny, například třídy, oboru názvů a sestavení. I to je užitečné, abyste mohli mapy jednoduché vypnutím této funkce pomocí **zahrnout nadřazené položky** tlačítko na panelu nástrojů mapy nebo stisknutím klávesy **CTRL** při přidávání položek.

 ![Pole související s metodu na mapě kódu zásobníku volání](../debugger/media/debuggermap_showedfields.png)

 Zde můžete snadno zobrazit metody, které používají stejná pole. Poslední přidané položky se zobrazí zeleně.

 Pokračujte v sestavování mapy, pokud chcete zobrazit další kód.

 ![Zobrazit metody, které používají pole: mapy kódu zásobníku volání](../debugger/media/debuggermap_findallreferences.png)

 ![Metody, které používají pole na mapě kódu zásobníku volání](../debugger/media/debuggermap_foundallreferences.png)

## <a name="FindBugs"></a> Najít chyby pomocí mapy

 Vizualizace kódu můžete nalézt chyby rychleji. Předpokládejme například, že hledáte chyby v programu kreslení. Když nakreslíte čáru a pokusíte se vrátit akci zpět, nic se nestane, dokud nenakreslíte další čáru.

 Proto nastavte zarážky v `clear`, `undo`, a `Repaint` metody, spustit ladění a vytvořit mapu podobné následujícímu:

 ![Přidat jiný zásobník volání k mapě kódu](../debugger/media/debuggermap_addpaintobjectcallstack.png)

 Všimněte si, že všechna gesta uživatelů na mapě volají `Repaint`, s výjimkou `undo`. To může vysvětlit, proč `undo` nefunguje okamžitě.

 Po opravě chyby a pokračování ve spouštění programu, mapování přidá nové volání z `undo` k `Repaint`:

 ![Přidat nový zásobník volání k volání metody na mapě kódu](../debugger/media/debuggermap_addnewcallforrepaint.png)

## <a name="QA"></a> Q & A

- **Ne všechna volání se zobrazí na mapě. Proč?**

   Ve výchozím nastavení zobrazí se pouze vlastní kód na mapě. Chcete-li zobrazit externí kód, zapněte ho v **zásobník volání** okno:

   ![Zobrazit externí kód pomocí okna zásobník volání](../debugger/media/debuggermap_callstackmenu.png)

   nebo se vypnout **povolit volbu pouze vlastní kód** v možnostech ladění aplikace Visual Studio:

   ![Zobrazit externí kód pomocí dialogové okno Možnosti](../debugger/media/debuggermap_debugoptions.png)

- **Změna mapování kód ovlivní?**

   Změna mapování kód nijak neovlivní. Nebojte se přejmenovat, přesunout nebo odebrat cokoli na mapě.

- **Co tato zpráva znamená: "diagram může být založen na starší verzi kódu"?**

   Po poslední aktualizaci mapy mohl být kód změněn. Například volání do mapy nemusí již v kódu existovat. Zavřete zprávu a potom zkuste znovu sestavit řešení před opětovnou aktualizací mapy.

- **Jak můžu řídit rozložení mapy?**

   Otevřít **rozložení** nabídky na panelu nástrojů mapy:

  - Změňte výchozí rozložení.

  - Chcete-li zastavit automatické uspořádání mapy, vypněte **při ladění automaticky rozmístit**.

  - Chcete-li změnit uspořádání mapy co při přidávání položek, vypněte **Inkrementální rozložení**.

- **Mohu sdílet mapu s ostatními?**

   Můžete exportovat mapu, odeslat ji ostatním uživatelům Pokud máte aplikaci Microsoft Outlook nebo uložit do vašeho řešení, abyste je mohli vrátit se změnami do správy zdrojového kódu.

   ![Sdílená složka volání zásobníku mapy kódu s ostatními](../debugger/media/debuggermap_sharewithothers.png)

- **Jak mohu zabránit mapě v automaticky přidání nových zásobníků volání?**

   Zvolte ![tlačítko &#45; zásobníku volání zobrazit na mapě kódu automaticky](../debugger/media/debuggermap_automaticupdateicon.gif) na panelu nástrojů Mapa. Chcete-li ručně přidat aktuální zásobník volání k mapě, stiskněte **Ctrl** + **Shift** +  **`** .

   Mapa bude pokračovat ve zvýraznění existujících zásobníků volání na mapě během ladění.

- **Co ikony položky a šipky znamenají?**

   Pokud chcete získat další informace o položce, přesuňte ukazatel myši nad ním a podívejte se na popis položky. Můžete také prohlédnout **legendy** se dozvíte, co znamenají jednotlivé ikony.

   ![Co znamenají ikony na mapě kódu zásobníku volání](../debugger/media/debuggermap_showlegend.png)

  Další informace:

- [Mapování zásobníku volání](#MapStack)

- [Tvorba poznámek o kódu](#MakeNotes)

- [Aktualizace mapy s následujícím zásobníkem volání.](#UpdateMap)

- [Přidání souvisejícího kódu do mapy](#AddRelatedCode)

- [Najít chyby pomocí mapy](#FindBugs)

## <a name="see-also"></a>Viz také:

- [Mapování závislostí napříč vaším řešením](../modeling/map-dependencies-across-your-solutions.md)
- [Použití map kódu k ladění aplikací](../modeling/use-code-maps-to-debug-your-applications.md)
- [Nalezení potenciálních problémů pomocí analyzátorů mapy kódu](../modeling/find-potential-problems-using-code-map-analyzers.md)
- [Procházení a změna uspořádání map kódu](../modeling/browse-and-rearrange-code-maps.md)
