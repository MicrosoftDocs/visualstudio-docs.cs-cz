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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c294ce3c6dcf3a880cf5f57ca825064366e08e2b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668236"
---
# <a name="map-methods-on-the-call-stack-while-debugging-in-visual-studio"></a>Mapování metod v zásobníku volání při ladění v sadě Visual Studio

Vytvořte mapu kódu pro vizuální trasování zásobníku volání při ladění. Můžete si dělat poznámky na mapě ke sledování kódu činnosti tak, abyste se mohli zaměřit na hledání chyb.

 ![Ladění pomocí zásobníků volání v mapách kódu](../debugger/media/debuggermap_overview.png)

 Budete potřebovat:

 ::: moniker range="vs-2017"

- [Visual Studio Enterprise](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)

::: moniker-end

::: moniker range="vs-2019"

- [Visual Studio Enterprise](https://visualstudio.microsoft.com/downloads)

::: moniker-end

- Kód, který lze ladit, jako je například C#Visual, Visual Basic C++,, JavaScript nebo X + +

  Další informace:

- [Video: vizuální ladění díky integraci ladicího programu mapy kódu (kanál 9)](http://go.microsoft.com/fwlink/?LinkId=293418)

- [Mapování zásobníku volání](#MapStack)

- [Vytvoření poznámek o kódu](#MakeNotes)

- [Aktualizace mapy s následujícím zásobníkem volání](#UpdateMap)

- [Přidat související kód do mapy](#AddRelatedCode)

- [Najít chyby pomocí mapy](#FindBugs)

- [Otázka & A](#QA)

  Podrobnosti o příkazech a akcích, které můžete použít při práci s mapami kódu, naleznete v tématu [procházení a změna uspořádání map kódu](../modeling/browse-and-rearrange-code-maps.md).

## <a name="MapStack"></a>Mapování zásobníku volání

1. Spustit ladění. (Klávesnice: **F5**)

2. Jakmile vaše aplikace přejde do režimu přerušení nebo přejdete do funkce, vyberte **Mapa kódu**. (Klávesnice: **Ctrl**  + **SHIFT**  +  **`** )

     ![Zvolit mapu kódu pro začátek mapování zásobníku volání](../debugger/media/debuggermap_choosecodemap.png)

     Aktuální aktuální zásobník volání se zobrazí oranžově na mapě nového kódu:

     ![Zobrazit zásobník volání na mapě kódu](../debugger/media/debuggermap_seeundocallstack.png)

     Mapa se automaticky aktualizuje, když budete pokračovat v ladění. Viz [aktualizace mapy s následujícím zásobníkem volání](#UpdateMap).

## <a name="MakeNotes"></a>Vytvoření poznámek o kódu

 Přidejte komentáře pro sledování, co se děje v kódu. Pokud chcete přidat nový řádek v komentáři, stiskněte **Shift + Return**.

 ![Přidat komentář k zásobníku volání na mapě kódu](../debugger/media/debuggermap_addcomment.png)

## <a name="UpdateMap"></a>Aktualizace mapy s následujícím zásobníkem volání

 Spuštění vaší aplikace na další zarážku nebo krok do funkce. Mapování přidá nový zásobník volání.

 ![Aktualizovat mapu kódu pomocí dalšího zásobníku volání](../debugger/media/debuggermap_addclearcallstack.png)

## <a name="AddRelatedCode"></a>Přidat související kód do mapy

 Teď už máte mapu – co dál? Pokud pracujete s C# nebo Visual Basic, přidejte položky, například pole, vlastnosti a jiné metody, pro sledování, co se děje v kódu.

 Dvojím kliknutím na metodu zobrazte její definici kódu nebo použijte místní nabídku pro metodu. (Klávesnice: Vyberte metodu na mapě a stiskněte klávesu **F12**)

 ![Přejít na definici kódu pro metodu na mapě kódu](../debugger/media/debuggermap_gotocodedefinition.png)

 Přidejte položky, které chcete sledovat na mapě.

 ![Zobrazit pole v metodě v mapě kódu zásobníku volání](../debugger/media/debuggermap_showfields.png)

> [!NOTE]
> Ve výchozím nastavení přidat položky do mapy také přidá uzly nadřazené skupiny, jako je například třída, obor názvů a sestavení. I když je to užitečné, můžete udržet mapu jednoduchou tím, že tuto funkci vypnete pomocí tlačítka **Zahrnout nadřazené prvky** na panelu nástrojů mapa nebo stisknutím klávesy **CTRL** při přidávání položek.

 ![Pole související s metodou v mapě kódu zásobníku volání](../debugger/media/debuggermap_showedfields.png)

 Zde můžete snadno zobrazit metody, které používají stejná pole. Poslední přidané položky se zobrazí zeleně.

 Pokračujte v sestavování mapy, pokud chcete zobrazit další kód.

 ![Viz metody, které používají pole: mapa kódu zásobníku volání](../debugger/media/debuggermap_findallreferences.png)

 ![Metody, které používají pole v mapě kódu zásobníku volání](../debugger/media/debuggermap_foundallreferences.png)

## <a name="FindBugs"></a>Najít chyby pomocí mapy

 Vizualizace kódu můžete nalézt chyby rychleji. Předpokládejme například, že zkoumáte chybu v programu pro kreslení. Když nakreslíte čáru a pokusíte se vrátit akci zpět, nic se nestane, dokud nenakreslíte další čáru.

 Takže můžete nastavit zarážky v metodách `clear`, `undo` a `Repaint`, spustit ladění a vytvořit mapu, jako je tato:

 ![Přidat další zásobník volání do mapy kódu](../debugger/media/debuggermap_addpaintobjectcallstack.png)

 Všimněte si, že všechna gesta uživatele v `Repaint` volání map, s výjimkou `undo`. To může vysvětlit, proč `undo` nefunguje hned.

 Po opravě chyby a pokračování ve spouštění programu Mapa přidá nové volání z `undo` do `Repaint`:

 ![Přidat nové volání metody do zásobníku volání na mapě kódu](../debugger/media/debuggermap_addnewcallforrepaint.png)

## <a name="QA"></a>Otázka & A

- **Ne všechna volání se zobrazí na mapě. Proč?**

   Ve výchozím nastavení se na mapě zobrazí pouze váš vlastní kód. Chcete-li zobrazit externí kód, zapněte ho v okně **zásobník volání** :

   ![Zobrazit externí kód pomocí okna zásobník volání](../debugger/media/debuggermap_callstackmenu.png)

   nebo vypněte možnost **povolit pouze můj kód** v možnostech ladění sady Visual Studio:

   ![Zobrazit externí kód pomocí dialogu Možnosti](../debugger/media/debuggermap_debugoptions.png)

- **Má změna mapy vliv na kód?**

   Změna mapy neovlivní kód jakýmkoli způsobem. Nebojte se přejmenovat, přesunout nebo odebrat cokoli na mapě.

- **Co tato zpráva znamená: "diagram může být založen na starší verzi kódu"?**

   Po poslední aktualizaci mapy mohl být kód změněn. Například volání do mapy nemusí již v kódu existovat. Zavřete zprávu a potom zkuste znovu sestavit řešení před opětovnou aktualizací mapy.

- **Návody ovládací prvek rozložení mapy?**

   Otevřete nabídku **rozložení** na panelu nástrojů mapa:

  - Změňte výchozí rozložení.

  - Chcete-li zastavit přeuspořádání mapy automaticky, vypněte **Automatické rozložení při ladění**.

  - Chcete-li změnit uspořádání mapy co nejméně při přidávání položek, vypněte možnost **přírůstkové rozložení**.

- **Můžu sdílet mapu s ostatními?**

   Můžete exportovat mapu, odeslat ji ostatním uživatelům, pokud máte aplikaci Microsoft Outlook, nebo ji uložit do vašeho řešení, abyste ji mohli vrátit se změnami do správy zdrojového kódu.

   ![Sdílení mapy kódu zásobníku volání s ostatními](../debugger/media/debuggermap_sharewithothers.png)

- **Návody zastavit mapu, aby se automaticky přidaly nové zásobníky volání?**

   Vyberte ![Button &#45; zobrazit zásobník volání na mapě kódu automaticky ](../debugger/media/debuggermap_automaticupdateicon.gif) na panelu nástrojů mapa. Chcete-li ručně přidat aktuální zásobník volání k mapě, stiskněte klávesu **Ctrl**  + **SHIFT**  +  **`** .

   Mapa bude pokračovat ve zvýraznění existujících zásobníků volání na mapě během ladění.

- **Co znamenají ikony a šipky položky?**

   Chcete-li získat další informace o položce, přesuňte ukazatel myši nad něj a podívejte se na popis položky. Můžete si také prohlédnout **legendu** , kde se dozvíte, co každá ikona znamená.

   ![Jak ikony na mapě kódu zásobníku volání znamenají?](../debugger/media/debuggermap_showlegend.png)

  Další informace:

- [Mapování zásobníku volání](#MapStack)

- [Vytvoření poznámek o kódu](#MakeNotes)

- [Aktualizace mapy s následujícím zásobníkem volání](#UpdateMap)

- [Přidat související kód do mapy](#AddRelatedCode)

- [Najít chyby pomocí mapy](#FindBugs)

## <a name="see-also"></a>Viz také:

- [Mapování závislostí napříč vaším řešením](../modeling/map-dependencies-across-your-solutions.md)
- [Použití map kódu k ladění aplikací](../modeling/use-code-maps-to-debug-your-applications.md)
- [Nalezení potenciálních problémů pomocí analyzátorů mapy kódu](../modeling/find-potential-problems-using-code-map-analyzers.md)
- [Procházení a změna uspořádání map kódu](../modeling/browse-and-rearrange-code-maps.md)
