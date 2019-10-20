---
title: Mapování metod v zásobníku volání při ladění
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
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
ms.assetid: d6a72e5e-f88d-46fc-94a3-1789d34805ef
caps.latest.revision: 43
author: MikeJo5000
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 81ae908c29b45b09d2ecec84c3189e6fb4e7a45b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657591"
---
# <a name="map-methods-on-the-call-stack-while-debugging-in-visual-studio"></a>Mapování metod v zásobníku volání při ladění v sadě Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vytvořte mapu kódu pro vizuální sledování zásobníku volání během ladění. Můžete si dělat poznámky na mapě ke sledování kódu činnosti tak, abyste se mohli zaměřit na hledání chyb.

 ![Ladění pomocí zásobníků volání v mapách kódu](../debugger/media/debuggermap-overview.png "DebuggerMap_Overview")

 Budete potřebovat:

- [Visual Studio Enterprise](https://www.visualstudio.com/downloads/download-visual-studio-vs)

- Kód, který lze ladit, jako je například C# Visual .net, Visual Basic .NET C++,, JavaScript nebo X + +

  Viz: [video: vizuální ladění díky integraci ladicího programu mapy kódu (kanál 9)](http://go.microsoft.com/fwlink/?LinkId=293418) • [mapování zásobníku volání](#MapStack) • [poznámky k kódu](#MakeNotes) • [aktualizace mapy s následujícím zásobníkem volání](#UpdateMap) • [Přidání souvisejícího kódu do mapy](#AddRelatedCode) • [najít chyby pomocí mapování](#FindBugs) • [Q & A](#QA)

  Podrobnosti o příkazech a akcích, které můžete použít při práci s mapami kódu, naleznete v tématu [procházení a změna uspořádání map kódu](../modeling/browse-and-rearrange-code-maps.md).

## <a name="MapStack"></a>Mapování zásobníku volání

1. Spustit ladění. (Klávesnice: **F5**)

2. Jakmile vaše aplikace přejde do režimu přerušení nebo přejdete do funkce, vyberte **Mapa kódu**. (Klávesnice: **Ctrl**  + **SHIFT**  +  **`** )

     ![Zvolit mapu kódu pro začátek mapování zásobníku volání](../debugger/media/debuggermap-choosecodemap.png "DebuggerMap_ChooseCodeMap")

     Aktuální aktuální zásobník volání se zobrazí oranžově na mapě nového kódu:

     ![Zobrazit zásobník volání na mapě kódu](../debugger/media/debuggermap-seeundocallstack.png "DebuggerMap_SeeUndoCallStack")

     Mapa se automaticky aktualizuje, když budete pokračovat v ladění. Viz [aktualizace mapy s následujícím zásobníkem volání](#UpdateMap).

## <a name="MakeNotes"></a>Vytvoření poznámek o kódu
 Přidejte komentáře pro sledování, co se děje v kódu. Pokud chcete přidat nový řádek v komentáři, stiskněte **Shift + Return**.

 ![Přidat komentář k zásobníku volání na mapě kódu](../debugger/media/debuggermap-addcomment.png "DebuggerMap_AddComment")

## <a name="UpdateMap"></a>Aktualizace mapy s následujícím zásobníkem volání
 Spuštění vaší aplikace na další zarážku nebo krok do funkce. Mapování přidá nový zásobník volání.

 ![Aktualizovat mapu kódu pomocí dalšího zásobníku volání](../debugger/media/debuggermap-addclearcallstack.png "DebuggerMap_AddClearCallStack")

## <a name="AddRelatedCode"></a>Přidat související kód do mapy
 Nyní máte k dispozici mapu – co dál? Při práci s prostředími Visual C#, .NET nebo Visual Basic .NET přidejte položky, například pole, vlastnosti a jiné metody, chcete-li sledovat, co se děje v kódu.

 Dvojím kliknutím na metodu zobrazte její definici kódu nebo použijte místní nabídku pro metodu. (Klávesnice: Vyberte metodu na mapě a stiskněte klávesu **F12**)

 ![Přejít na definici kódu pro metodu na mapě kódu](../debugger/media/debuggermap-gotocodedefinition.png "DebuggerMap_GoToCodeDefinition")

 Přidejte položky, které chcete sledovat na mapě.

 ![Zobrazit pole v metodě v mapě kódu zásobníku volání](../debugger/media/debuggermap-showfields.png "DebuggerMap_ShowFields")

> [!NOTE]
> Ve výchozím nastavení přidat položky do mapy také přidá uzly nadřazené skupiny, jako je například třída, obor názvů a sestavení. I když je to užitečné, můžete udržet mapu jednoduchou tím, že tuto funkci vypnete pomocí tlačítka **Zahrnout nadřazené prvky** na panelu nástrojů mapa nebo stisknutím klávesy **CTRL** při přidávání položek.

 ![Pole související s metodou v mapě kódu zásobníku volání](../debugger/media/debuggermap-showedfields.png "DebuggerMap_ShowedFields")

 Zde můžete snadno zobrazit metody, které používají stejná pole. Poslední přidané položky se zobrazí zeleně.

 Pokračujte v sestavování mapy, pokud chcete zobrazit další kód.

 ![Viz metody, které používají pole: mapa kódu zásobníku volání](../debugger/media/debuggermap-findallreferences.png "DebuggerMap_FindAllReferences")

 ![Metody, které používají pole v mapě kódu zásobníku volání](../debugger/media/debuggermap-foundallreferences.png "DebuggerMap_FoundAllReferences")

## <a name="FindBugs"></a>Najít chyby pomocí mapy
 Vizualizace kódu můžete nalézt chyby rychleji. Předpokládejme například, že hledáte chyby v aplikaci pro kreslení. Když nakreslíte čáru a pokusíte se vrátit akci zpět, nic se nestane, dokud nenakreslíte další čáru.

 Takže můžete nastavit zarážky v metodách `clear`, `undo` a `Repaint`, spustit ladění a vytvořit mapu, jako je tato:

 ![Přidat další zásobník volání do mapy kódu](../debugger/media/debuggermap-addpaintobjectcallstack.png "DebuggerMap_AddPaintObjectCallStack")

 Všimněte si, že všechna gesta uživatele v `Repaint` volání map, s výjimkou `undo`. To může vysvětlit, proč `undo` nefunguje hned.

 Po opravě chyby a pokračování ve spouštění programu Mapa přidá nové volání z `undo` do `Repaint`:

 ![Přidat nové volání metody do zásobníku volání na mapě kódu](../debugger/media/debuggermap-addnewcallforrepaint.png "DebuggerMap_AddNewCallForRepaint")

## <a name="QA"></a>Otázka & A

- **Ne všechna volání se zobrazí na mapě. Proč?**

   Ve výchozím nastavení se na mapě zobrazí pouze váš vlastní kód. Chcete-li zobrazit externí kód, zapněte ho v okně **zásobník volání** :

   ![Zobrazit externí kód pomocí okna zásobník volání](../debugger/media/debuggermap-callstackmenu.png "DebuggerMap_CallStackMenu")

   nebo vypněte možnost **povolit pouze můj kód** v možnostech ladění sady Visual Studio:

   ![Zobrazit externí kód pomocí dialogu Možnosti](../debugger/media/debuggermap-debugoptions.png "DebuggerMap_DebugOptions")

- **Má změna mapy vliv na kód?**

   Změna mapování kód nijak neovlivní. Nebojte se přejmenovat, přesunout nebo odebrat cokoli na mapě.

- **Co tato zpráva znamená: "diagram může být založen na starší verzi kódu"?**

   Po poslední aktualizaci mapy mohl být kód změněn. Například volání do mapy nemusí již v kódu existovat. Zavřete zprávu a potom zkuste znovu sestavit řešení před opětovnou aktualizací mapy.

- **Návody ovládací prvek rozložení mapy?**

   Otevřete nabídku **rozložení** na panelu nástrojů mapa:

  - Změňte výchozí rozložení.

  - Chcete-li zastavit přeuspořádání mapy automaticky, vypněte **Automatické rozložení při ladění**.

  - Chcete-li změnit uspořádání mapy co nejméně při přidávání položek, vypněte možnost **přírůstkové rozložení**.

- **Můžu sdílet mapu s ostatními?**

   Můžete exportovat mapu, odeslat ji ostatním uživatelům, pokud máte aplikaci Microsoft Outlook, nebo ji uložit do vašeho řešení, abyste ji mohli vrátit se změnami do řízení verzí Team Foundation.

   ![Sdílení mapy kódu zásobníku volání s ostatními](../debugger/media/debuggermap-sharewithothers.png "DebuggerMap_ShareWithOthers")

- **Návody zastavit mapu, aby se automaticky přidaly nové zásobníky volání?**

   Vyberte ![tlačítko &#45; zobrazit zásobník volání na mapě kódu automaticky](../debugger/media/debuggermap-automaticupdateicon.gif "DebuggerMap_AutomaticUpdateIcon") na panelu nástrojů mapa. Chcete-li ručně přidat aktuální zásobník volání k mapě, stiskněte klávesu **Ctrl**  + **SHIFT**  +  **`** .

   Mapa bude pokračovat ve zvýraznění existujících zásobníků volání na mapě během ladění.

- **Co znamenají ikony a šipky položky?**

   Chcete-li získat další informace o položce, přesuňte ukazatel myši nad něj a podívejte se na popis položky. Můžete si také prohlédnout **legendu** , kde se dozvíte, co každá ikona znamená.

   ![Jak ikony na mapě kódu zásobníku volání znamenají?](../debugger/media/debuggermap-showlegend.png "DebuggerMap_ShowLegend")

  Viz: [namapování zásobníku volání](#MapStack) • [vytvoření poznámek o kódu](#MakeNotes) • [aktualizace mapy s následujícím zásobníkem volání](#UpdateMap) • [Přidání souvisejícího kódu do mapy](#AddRelatedCode) • [najít chyby pomocí mapy](#FindBugs)

## <a name="see-also"></a>Viz také
 [Mapování závislostí ve vašich řešeních](../modeling/map-dependencies-across-your-solutions.md) [použití map kódu k ladění aplikací](../modeling/use-code-maps-to-debug-your-applications.md) [hledání potenciálních problémů pomocí analyzátorů mapy kódu](../modeling/find-potential-problems-using-code-map-analyzers.md) [procházení a změna uspořádání map kódu](../modeling/browse-and-rearrange-code-maps.md)
