---
title: Vytvoření vizuální mapy zásobníku volání | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/26/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.progression.debugwithcodemaps
dev_langs:
- CSharp
- VB
- FSharp
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ede973d96ffe21fb9406bb471400ffa8e2b69251
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/27/2018
ms.locfileid: "52389575"
---
# <a name="create-a-visual-map-of-the-call-stack-while-debugging"></a>Vytvoření vizuální mapy zásobníku volání při ladění 

Vytvořte mapu kódu pro vizuální sledování zásobníku volání během ladění. Můžete si dělat poznámky na mapě můžete sledovat, co kód dělá, abyste se mohli soustředit na hledání chyb.

Návod, podívejte se na toto video: [Video: vizuální ladění díky integraci ladicího programu mapy kódu (kanál 9)](http://go.microsoft.com/fwlink/?LinkId=293418)

Podrobnosti o příkazů a akcí můžete pomocí map kódu, naleznete v tématu [Procházet a uspořádání map kódu](../modeling/browse-and-rearrange-code-maps.md).

>[!IMPORTANT]
>Můžete vytvořit pouze v mapy kódu [edici Visual Studio Enterprise](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017).

Tady je rychlý pohled na mapě kódu:

 ![Ladění se zásobníky volání na mapách kódu](../debugger/media/debuggermap_overview.png "DebuggerMap_Overview")

##  <a name="MapStack"></a> Mapování zásobníku volání

1. V sadě Visual Studio Enterprise C#, Visual Basic, C++, JavaScript nebo X ++ projektu, spustit ladění tak, že vyberete **ladění** > **spustit ladění** nebo stiskněte **F5**.
   
1. Poté, co vaše aplikace přejde do režimu přerušení nebo přejdete na funkci, vyberte **ladění** > **mapy kódu**, nebo stiskněte klávesu **Ctrl**+**Shift** +**`**.

   Aktuální aktuální zásobník volání se zobrazí oranžově na mapě nového kódu:

   ![Zobrazit zásobník volání na mapě kódu](../debugger/media/debuggermap_seeundocallstack.png "DebuggerMap_SeeUndoCallStack")

Kód mapování aktualizace automaticky v průběhu ladění. Změna položek mapování nebo rozložení kód nijak neovlivní. Nebojte se přejmenovat, přesunout nebo odebrat cokoli na mapě.

Pokud chcete získat další informace o položce, najeďte myší nad ním a podívejte se na popis položky. Můžete také vybrat **legendy** na panelu nástrojů se dozvíte, co znamenají jednotlivé ikony.

![Legenda mapy kódu](../debugger/media/debuggermap_showlegend.png "legendu mapy kódu")

>[!NOTE]
>Zpráva **diagram může být založen na starší verzi kódu** v horní části kódu mapy znamená, že kód změnil po poslední aktualizaci mapy. Například volání do mapy nemusí již v kódu existovat. Zavřete zprávu a potom zkuste znovu sestavit řešení před opětovnou aktualizací mapy.

## <a name="map-external-code"></a>Mapování externí kód

Ve výchozím nastavení zobrazí se pouze vlastní kód na mapě. Chcete-li zobrazit externí kód na mapě:
  
- Klikněte pravým tlačítkem **zásobník volání** okna a vyberte **zobrazit externí kód**:
  
  ![Zobrazit externí kód pomocí okna zásobník volání](../debugger/media/debuggermap_callstackmenu.png "DebuggerMap_CallStackMenu")
- Nebo zrušte výběr **povolit volbu pouze vlastní kód** v sadě Visual Studio **nástroje** (nebo **ladění**) > **možnosti**  >   **Ladění**:
  
  ![Zobrazit externí kód pomocí dialogového okna Možnosti](../debugger/media/debuggermap_debugoptions.png "DebuggerMap_DebugOptions")

## <a name="control-the-maps-layout"></a>Řídit rozložení mapy

Změna rozložení na mapě kódu nijak neovlivní. 

Chcete-li řídit rozložení na mapě, vyberte **rozložení** nabídky na panelu nástrojů Mapa. 

V **rozložení** nabídku, můžete:

-   Změňte výchozí rozložení.
-   Zastavit automatické uspořádání mapy odznačením **při ladění automaticky rozmístit**.
-   Změna uspořádání mapy co při přidávání položek, odznačením **Inkrementální rozložení**.

##  <a name="MakeNotes"></a> Tvorba poznámek o kódu

Můžete přidat komentáře pro sledování, co se děje v kódu. 

Chcete-li přidat komentář, klikněte pravým tlačítkem na mapě kódu a vyberte **upravit** > **nový komentář**, zadejte komentář. 

Chcete-li přidat nový řádek v komentáři, stiskněte **Shift**+**Enter**.

 ![Přidat komentář do zásobníku volání na mapě kódu](../debugger/media/debuggermap_addcomment.png "DebuggerMap_AddComment")

##  <a name="UpdateMap"></a> Aktualizace mapy s následujícím zásobníkem volání.

Při spouštění vaší aplikace na další zarážku nebo krok do funkce, mapování přidá nové zásobníky volání automaticky.

![Aktualizace mapy kódu s následujícím zásobníkem volání](../debugger/media/debuggermap_addclearcallstack.png "DebuggerMap_AddClearCallStack")

Chcete-li zabránit mapě v přidání nových zásobníků volání automaticky, vyberte ![zásobníku volání zobrazit na mapě kódu automaticky](../debugger/media/debuggermap_automaticupdateicon.gif "zásobníku volání zobrazit na mapě kódu automaticky") na panelu nástrojů mapy kódu. I nadále zvýraznění existujících zásobníků volání na mapě. Chcete-li ručně přidat aktuální zásobník volání k mapě, stiskněte **Ctrl**+**Shift**+**`**. 

##  <a name="AddRelatedCode"></a> Přidání souvisejícího kódu do mapy

Teď, když je k dispozici mapu, v C# nebo Visual Basic, můžete přidat položky, jako jsou pole, vlastnosti a jiné metody, můžete sledovat, co se děje v kódu. 

Přejít k definici metody v kódu, poklepejte na metodu na mapě nebo vyberte ji a stiskněte klávesu **F12**, nebo pravým tlačítkem myši a vyberte **přejít k definici**.

![Přejít na definici kódu pro metodu na mapě kódu](../debugger/media/debuggermap_gotocodedefinition.png "DebuggerMap_GoToCodeDefinition")

Chcete-li přidat položky, které chcete sledovat na mapě, klikněte pravým tlačítkem na metodu a vyberte položky, které chcete sledovat. Poslední přidané položky se zobrazí zeleně.

![Pole související s metodu na mapě kódu zásobníku volání](../debugger/media/debuggermap_showedfields.png "DebuggerMap_ShowedFields")

>[!NOTE]
>Ve výchozím nastavení přidávání položek do mapy také přidá nadřazené uzly skupiny, například třídy, oboru názvů a sestavení. Tato funkce může vypněte a zapněte tak, že vyberete **zahrnout nadřazené položky** tlačítko na panelu nástrojů mapy kódu nebo stisknutím klávesy **Ctrl** při přidávání položek.

![Zobrazit pole v metodu na mapě kódu zásobníku volání](../debugger/media/debuggermap_showfields.png "DebuggerMap_ShowFields")

Pokračujte v sestavování mapy, pokud chcete zobrazit další kód.

 ![Zobrazit metody, které používají pole: mapy kódu zásobníku volání](../debugger/media/debuggermap_findallreferences.png "DebuggerMap_FindAllReferences")

 ![Metody, které používají pole na mapě kódu zásobníku volání](../debugger/media/debuggermap_foundallreferences.png "DebuggerMap_FoundAllReferences")

##  <a name="FindBugs"></a> Najít chyby pomocí mapy
 Vizualizace kódu můžete nalézt chyby rychleji. Předpokládejme například, že hledáte chyby v aplikaci pro kreslení. Když nakreslíte čáru a pokusíte se vrátit akci zpět, nic se nestane, dokud nenakreslíte další čáru.

 Proto nastavte zarážky v `clear`, `undo`, a `Repaint` metody, spustit ladění a vytvořit mapu podobné následujícímu:

 ![Přidat jiný zásobník volání k mapě kódu](../debugger/media/debuggermap_addpaintobjectcallstack.png "DebuggerMap_AddPaintObjectCallStack")

 Všimněte si, že všechna gesta uživatelů na mapě volají `Repaint`, s výjimkou `undo`. To může vysvětlit, proč `undo` nefunguje okamžitě.

 Po opravě chyby a pokračování ve spouštění aplikace, mapování přidá nové volání z `undo` k `Repaint`:

 ![Přidat nový zásobník volání k volání metody na mapě kódu](../debugger/media/debuggermap_addnewcallforrepaint.png "DebuggerMap_AddNewCallForRepaint")

## <a name="share-the-map-with-others"></a>Sdílet mapu s ostatními

Můžete exportovat mapu, odeslat ji ostatním uživatelům s aplikací Microsoft Outlook, uložte ho do svého řešení a vrátit se změnami do správy verzí.

Chcete-li sdílet nebo uložit na mapě, použijte **sdílet** v panelu nástrojů mapy kódu. 

![Sdílená složka volání zásobníku mapy kódu s ostatními](../debugger/media/debuggermap_sharewithothers.png "sdílené složky volání zásobníku mapy kódu s ostatními")

## <a name="see-also"></a>Viz také:
[Mapování závislostí napříč vaším řešením](../modeling/map-dependencies-across-your-solutions.md)

[Použití map kódu k ladění aplikací](../modeling/use-code-maps-to-debug-your-applications.md)

[Nalezení potenciálních problémů pomocí analyzátorů mapy kódu](../modeling/find-potential-problems-using-code-map-analyzers.md)

[Procházení a změna uspořádání map kódu](../modeling/browse-and-rearrange-code-maps.md)
