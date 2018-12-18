---
title: Použití map kódu k ladění aplikací | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio Ultimate, visualizing code
- Visual Studio Ultimate, navigating code visually
- Visual Studio Ultimate, understanding code
- Visual Studio Ultimate, mapping code relationships
- Visual Studio Ultimate, code maps
- mapping code relationships
- code maps
- mapping relationships in code
ms.assetid: 9fd0c9a2-d351-40c8-be88-0749788264bf
caps.latest.revision: 51
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: af5f34b307f94f1bae4c913421acbe0a934ed113
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51743834"
---
# <a name="use-code-maps-to-debug-your-applications"></a>Použití map kódu k ladění aplikací
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Mapy kódu vám umožňují předcházet ztrátě orientace v rozsáhlých kódech, neznámém kódu nebo starším kódu. Při ladění bude například pravděpodobně nutné ověřit kód v mnoha souborech a projektech. Použití map kódu k navigaci v části kódu a pochopení vztahů mezi nimi. Díky tomu není nutné udržovat přehled o tento kód v hlavě nebo kreslit samostatné diagramu. Ano když dojde k přerušení svou práci, mapy kódu vám pomohou připomenout paměti ke kódu, který právě pracujete.  
  
 ![Mapy kódu &#45; mapujte vztahy v kódu](../modeling/media/codemapstoryboardpaint.png "CodeMapStoryboardPaint")  
  
 **Zelená šipka ukazuje, kde se zobrazí kurzor v editoru**  
  
 Podrobnosti příkazů a akcí, které můžete použít při práci s mapami kódu najdete v tématu [Procházet a uspořádání map kódu](../modeling/browse-and-rearrange-code-maps.md).  
  
## <a name="understand-the-problem"></a>Pochopení problému  
 Předpokládejme, že je chyba v programu kreslení, na kterém právě pracujete. Chcete-li reprodukovat chybu, otevřete řešení v sadě Visual Studio a stiskněte klávesu **F5** pro spuštění ladění.  
  
 Když nakreslíte čáru a zvolte **vrátit zpět poslední tah**, nic se nestane, dokud nenakreslíte další čáru.  
  
 ![Mapy kódu &#45; reprodukci chyb](../modeling/media/codemapstoryboardpaint0.png "CodeMapStoryboardPaint0")  
  
 Takže začnete zjišťovat hledáním `Undo` metody. Najdete ho ve `PaintCanvas` třídy.  
  
 ![Mapy kódu &#45; vyhledávání kódu](../modeling/media/codemapstoryboardpaint1.png "CodeMapStoryboardPaint1")  
  
## <a name="start-mapping-the-code"></a>Spuštění mapování kódu  
 Nyní spusťte mapování `undo` metoda a jejích vztahů. V editoru kódu přidejte `undo` metody a pole, která odkazují na mapu s novým kódem. Když vytvoříte nové mapování, může zaindexování kódu trvat nějakou dobu. To pomáhá rychlejšímu běhu pozdějších operací.  
  
 ![Mapy kódu &#45; zobrazit metody a související pole](../modeling/media/codemapstoryboardpaint3.png "CodeMapStoryboardPaint3")  
  
> [!TIP]
>  Zelené zvýraznění zobrazí poslední položky, které byly přidány do mapy. Zelená šipka ukazuje pozici kurzoru v kódu. Šipky mezi položkami představují různé vztahy. Na mapě můžete získat další informace o položkách hýbání myší nad nimi a Prozkoumáním jejich popisků.  
  
 ![Mapy kódu &#45; zobrazit popisy tlačítek](../modeling/media/codemapstoryboardpaint4.png "CodeMapStoryboardPaint4")  
  
## <a name="navigate-and-examine-code-from-the-map"></a>Procházení a zkoumání kódu z mapy  
 Chcete-li zobrazit definici kódu pro každé pole, poklepejte na pole na mapě nebo vyberte pole a stiskněte klávesu **F12**. Zelená šipka se přesune mezi položkami na mapě. Kurzor v editoru kódu se také přesune automaticky.  
  
 ![Mapy kódu &#45; Zkontrolujte definici pole](../modeling/media/codemapstoryboardpaint5.png "CodeMapStoryboardPaint5")  
  
 ![Mapy kódu &#45; Zkontrolujte definici pole](../modeling/media/codemapstoryboardpaint5a.png "CodeMapStoryboardPaint5A")  
  
> [!TIP]
>  Zelenou šipku na mapě můžete také přesunout přesunutím kurzoru v editoru kódu.  
  
## <a name="understand-relationships-between-pieces-of-code"></a>Pochopení vztahů mezi částmi kódu  
 Nyní chcete vědět, jaký další kód spolupracuje s `history` a `paintObjects` pole. Můžete do mapy přidat všechny metody, které odkazují na tato pole. Můžete to provést z mapy nebo z editoru kódu.  
  
 ![Mapy kódu &#45; najít všechny odkazy](../modeling/media/codemapstoryboardpaint6.png "CodeMapStoryboardPaint6")  
  
 ![Spustit nástroj Mapa kódu z editoru kódu](../modeling/media/codemapstoryboardpaint6a.PNG "CodeMapStoryboardPaint6A")  
  
> [!NOTE]
>  Pokud chcete přidat položky z projektu, který je sdílen mezi více aplikacemi, jako jsou Windows Phone nebo Windows Store, pak tyto položky vždy se zobrazí s aktuálně aktivním projektem aplikace na mapě. Ano Pokud změníte kontext na jiný projekt aplikace, pak kontext na mapě změní také pro všechny nově přidané položky ze sdíleného projektu. Operace, které provádíte s položkou na mapě, se vztahují pouze na ty položky, které sdílejí stejný kontext.  
  
 Změňte rozložení a uspořádejte tak tok vztahů a usnadněte čtení z mapy. Položky kolem mapy lze také přesunout přetažením.  
  
 ![Mapy kódu &#45; změnit rozložení](../modeling/media/codemapstoryboardpaint7a.png "CodeMapStoryboardPaint7A")  
  
> [!TIP]
>  Ve výchozím nastavení **Inkrementální rozložení** zapnutý. To při přidání nových položek mění uspořádání mapy co nejméně. Chcete-li uspořádat celou mapu při každém přidání nových položek, vypněte **Inkrementální rozložení**.  
  
 ![Mapy kódu &#45; změnit rozložení](../modeling/media/codemapstoryboardpaint7.png "CodeMapStoryboardPaint7")  
  
 Podívejme se na tyto metody. Na mapě dvakrát klikněte **PaintCanvas** metodu, nebo zvolte tuto metodu a stiskněte klávesu **F12**. Zjistíte, že tato metoda vytvoří `history` a `paintObjects` jako prázdný seznam.  
  
 ![Mapy kódu &#45; prozkoumání definice metody](../modeling/media/codemapstoryboardpaint8.png "CodeMapStoryboardPaint8")  
  
 Nyní opakujte stejný postup k prozkoumání `clear` definice metody. Zjistíte, že `clear` několik úloh pomocí provádí `paintObjects` a `history`. Poté zavolá `Repaint` metody.  
  
 ![Mapy kódu &#45; prozkoumání definice metody](../modeling/media/codemapstoryboardpaint9.png "CodeMapStoryboardPaint9")  
  
 Nyní prozkoumejte `addPaintObject` definice metody. Provádí také některé úlohy s `history` a `paintObjects`. Volá také `Repaint`.  
  
 ![Mapy kódu &#45; prozkoumání definice metody](../modeling/media/codemapstoryboardpaint10.png "CodeMapStoryboardPaint10")  
  
## <a name="find-the-problem-by-examining-the-map"></a>Nalezení příčiny problému prozkoumáním mapy  
 Zdá se, že všechny metody, které mění `history` a `paintObjects` volání `Repaint`. Přesto `undo` nevolá metodu `Repaint`, i když `undo` mění stejná pole. Takže si myslíte, že tento problém můžete vyřešit voláním `Repaint` z `undo`.  
  
 ![Mapy kódu &#45; najít chybějící volání metody](../modeling/media/codemapstoryboardpaint11.png "CodeMapStoryboardPaint11")  
  
 Pokud by nebyla nastavena mapa k zobrazení tohoto chybějícího volání, mohlo by být nalezení tohoto problému obtížnější, zejména u složitějšího kódu.  
  
## <a name="share-your-discovery-and-next-steps"></a>Sdílení zjištění a další kroky  
 Předtím, než vy nebo někdo jiný tuto chybu vyřeší, si můžete dělat na mapě poznámky o problému a způsobu jeho řešení.  
  
 ![Mapy kódu &#45; komentář a označit položky pro zpracování](../modeling/media/codemapstoryboardpaint12.png "CodeMapStoryboardPaint12")  
  
 Můžete například přidat komentáře do mapy a označit položky pomocí barev.  
  
 ![Mapy kódu &#45; komentářem a položky s příznakem](../modeling/media/codemapstoryboardpaint12a.png "CodeMapStoryboardPaint12A")  
  
 Pokud máte nainstalovanou aplikaci Microsoft Outlook, můžete mapu e-mailem odeslat ostatním. Mapu taky můžete exportovat jako obrázek nebo jiný formát.  
  
 ![Mapy kódu &#45; sdílené složky, export, zajišťujeme e-mailu](../modeling/media/codemapstoryboardpaint13.png "CodeMapStoryboardPaint13")  
  
## <a name="fix-the-problem-and-show-what-you-did"></a>Vyřešení problému a zobrazení provedené činnosti  
 Chcete-li vyřešit tuto chybu, přidejte volání pro `Repaint` k `undo`.  
  
 ![Mapy kódu &#45; přidat chybějící volání metody](../modeling/media/codemapstoryboardpaint14.png "CodeMapStoryboardPaint14")  
  
 Chcete-li potvrdit svou opravu, restartujte relaci ladění a zkuste chybu reprodukovat. Nyní volba **vrátit zpět poslední tah** funguje podle očekávání a potvrdí provedení správné opravy.  
  
 ![Mapy kódu &#45; potvrdit opravu kódu](../modeling/media/codemapstoryboardpaint15.png "CodeMapStoryboardPaint15")  
  
 Můžete aktualizovat mapu, aby zobrazovala provedené opravy.  
  
 ![Mapy kódu &#45; aktualizace mapy s chybějící volání metody](../modeling/media/codemapstoryboardpaint16.png "CodeMapStoryboardPaint16")  
  
 Mapa nyní zobrazuje spojení mezi **zpět** a **Repaint**.  
  
 ![Mapy kódu &#45; mapy aktualizované pomocí volání metody](../modeling/media/codemapstoryboardpaint17.png "CodeMapStoryboardPaint17")  
  
> [!NOTE]
>  Při aktualizaci mapy se může zobrazit zpráva, že byl aktualizován index kódu použitý k vytvoření mapy. To znamená, že někdo změnil kód, což způsobilo, že se vaše mapa neshoduje s aktuálním kódem. To vám nezabrání v aktualizaci mapy, ale chcete-li ověřit, že mapa odpovídá kódu, pravděpodobně ji budete muset znovu vytvořit.  
  
 Nyní je vaše šetření hotovo. Úspěšně jste našli a opravili problém pomocí mapování kódu. Máte k dispozici také mapu, která usnadňuje navigaci v rámci kódu, zapamatuje si, co jste se naučili, a zobrazí kroky, které jste provedli v zájmu vyřešení problému.  
  
## <a name="see-also"></a>Viz také  
 [Mapování metod v zásobníku volání při ladění](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)   
 [Vizualizace kódu](../modeling/visualize-code.md)



