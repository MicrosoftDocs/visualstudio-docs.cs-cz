---
title: Použití map kódu k ladění aplikací
ms.date: 09/28/2018
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
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 838bf3cab092106140f3aeeaf33c74a13cd23b35
ms.sourcegitcommit: ad5fb20f18b23eb8bd2568717f61edc6b7eee5e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2018
ms.locfileid: "47859663"
---
# <a name="use-code-maps-to-debug-your-applications"></a>Použití map kódu k ladění aplikací

Mapy kódu vám umožňují předcházet ztrátě orientace v rozsáhlých kódech, neznámém kódu nebo starším kódu. Při ladění, budete muset ověřit kód v mnoha souborech a projektech. Použití map kódu k navigaci v části kódu a pochopení vztahů mezi nimi. Díky tomu není nutné udržovat přehled o tento kód v hlavě nebo kreslit samostatné diagramu. Ano když dojde k přerušení svou práci, mapy kódu vám pomohou připomenout paměti ke kódu, který právě pracujete.

![Mapy kódu &#45; mapujte vztahy v kódu](../modeling/media/codemapstoryboardpaint.png)

**Zelená šipka ukazuje, kde se zobrazí kurzor v editoru**

Podrobnosti příkazů a akcí, které můžete použít při práci s mapami kódu najdete v tématu [Procházet a uspořádání map kódu](../modeling/browse-and-rearrange-code-maps.md).

> [!NOTE]
> Vytvářet a upravovat map kódu, je třeba Visual Studio Enterprise edition. Ve Visual Studio Community a Professional edice umožňuje otevírat diagramy, které byly vytvořeny v edici Enterprise, ale nemůžete je upravovat.

## <a name="understand-the-problem"></a>Pochopení problému
 Předpokládejme, že je chyba v programu kreslení, na kterém právě pracujete. Chcete-li reprodukovat chybu, otevřete řešení v sadě Visual Studio a stiskněte klávesu **F5** pro spuštění ladění.

 Když nakreslíte čáru a zvolte **vrátit zpět poslední tah**, nic se nestane, dokud nenakreslíte další čáru.

 ![Mapy kódu &#45; reprodukci chyb](../modeling/media/codemapstoryboardpaint0.png)

 Takže začnete zjišťovat hledáním `Undo` metody. Najdete ho ve `PaintCanvas` třídy.

 ![Mapy kódu &#45; vyhledávání kódu](../modeling/media/codemapstoryboardpaint1.png)

## <a name="start-mapping-the-code"></a>Spuštění mapování kódu
 Nyní spusťte mapování `undo` metoda a jejích vztahů. V editoru kódu přidejte `undo` metody a pole, která odkazují na mapu s novým kódem. Když vytvoříte nové mapování, může zaindexování kódu trvat nějakou dobu. To pomáhá rychlejšímu běhu pozdějších operací.

 ![Mapy kódu &#45; zobrazit metody a související pole](../modeling/media/codemapstoryboardpaint3.png)

> [!TIP]
> Zelené zvýraznění zobrazí poslední položky, které byly přidány do mapy. Zelená šipka ukazuje pozici kurzoru v kódu. Šipky mezi položkami představují různé vztahy. Na mapě můžete získat další informace o položkách hýbání myší nad nimi a Prozkoumáním jejich popisků.

 ![Mapy kódu &#45; zobrazit popisy tlačítek](../modeling/media/codemapstoryboardpaint4.png)

## <a name="navigate-and-examine-code-from-the-map"></a>Procházení a zkoumání kódu z mapy
 Chcete-li zobrazit definici kódu pro každé pole, poklepejte na pole na mapě nebo vyberte pole a stiskněte klávesu **F12**. Zelená šipka se přesune mezi položkami na mapě. Kurzor v editoru kódu se také přesune automaticky.

 ![Mapy kódu &#45; Zkontrolujte definici pole](../modeling/media/codemapstoryboardpaint5.png)

 ![Mapy kódu &#45; Zkontrolujte definici pole](../modeling/media/codemapstoryboardpaint5a.png)

> [!TIP]
> Zelenou šipku na mapě můžete také přesunout přesunutím kurzoru v editoru kódu.

## <a name="understand-relationships-between-pieces-of-code"></a>Pochopení vztahů mezi částmi kódu
 Nyní chcete vědět, jaký další kód spolupracuje s `history` a `paintObjects` pole. Můžete do mapy přidat všechny metody, které odkazují na tato pole. Můžete to provést z mapy nebo z editoru kódu.

 ![Mapy kódu &#45; najít všechny odkazy](../modeling/media/codemapstoryboardpaint6.png)

 ![Spustit nástroj Mapa kódu z editoru kódu](../modeling/media/codemapstoryboardpaint6a.png)

> [!NOTE]
> Pokud chcete přidat položky z projektu, který je sdílen mezi více aplikacemi, jako jsou Windows Phone nebo Windows Store, pak tyto položky vždy se zobrazí s aktuálně aktivním projektem aplikace na mapě. Ano Pokud změníte kontext na jiný projekt aplikace, pak kontext na mapě změní také pro všechny nově přidané položky ze sdíleného projektu. Operace, které provádíte s položkou na mapě, se vztahují pouze na ty položky, které sdílejí stejný kontext.

 Změňte rozložení a uspořádejte tak tok vztahů a usnadněte čtení z mapy. Položky kolem mapy lze také přesunout přetažením.

 ![Mapy kódu &#45; změnit rozložení](../modeling/media/codemapstoryboardpaint7a.png)

> [!TIP]
> Ve výchozím nastavení **Inkrementální rozložení** zapnutý. To při přidání nových položek mění uspořádání mapy co nejméně. Chcete-li uspořádat celou mapu při každém přidání nových položek, vypněte **Inkrementální rozložení**.

 ![Mapy kódu &#45; změnit rozložení](../modeling/media/codemapstoryboardpaint7.png)

 Podívejme se na tyto metody. Na mapě dvakrát klikněte **PaintCanvas** metodu, nebo zvolte tuto metodu a stiskněte klávesu **F12**. Zjistíte, že tato metoda vytvoří `history` a `paintObjects` jako prázdný seznam.

 ![Mapy kódu &#45; prozkoumání definice metody](../modeling/media/codemapstoryboardpaint8.png)

 Nyní opakujte stejný postup k prozkoumání `clear` definice metody. Zjistíte, že `clear` několik úloh pomocí provádí `paintObjects` a `history`. Poté zavolá `Repaint` metody.

 ![Mapy kódu &#45; prozkoumání definice metody](../modeling/media/codemapstoryboardpaint9.png)

 Nyní prozkoumejte `addPaintObject` definice metody. Provádí také některé úlohy s `history` a `paintObjects`. Volá také `Repaint`.

 ![Mapy kódu &#45; prozkoumání definice metody](../modeling/media/codemapstoryboardpaint10.png)

## <a name="find-the-problem-by-examining-the-map"></a>Nalezení příčiny problému prozkoumáním mapy
 Zdá se, že všechny metody, které mění `history` a `paintObjects` volání `Repaint`. Přesto `undo` nevolá metodu `Repaint`, i když `undo` mění stejná pole. Takže si myslíte, že tento problém můžete vyřešit voláním `Repaint` z `undo`.

 ![Mapy kódu &#45; najít chybějící volání metody](../modeling/media/codemapstoryboardpaint11.png)

 Pokud by nebyla nastavena mapa k zobrazení tohoto chybějícího volání, mohlo by být nalezení tohoto problému obtížnější, zejména u složitějšího kódu.

## <a name="share-your-discovery-and-next-steps"></a>Sdílení zjištění a další kroky
 Předtím, než vy nebo někdo jiný tuto chybu vyřeší, si můžete dělat na mapě poznámky o problému a způsobu jeho řešení.

 ![Mapy kódu &#45; komentář a označit položky pro zpracování](../modeling/media/codemapstoryboardpaint12.png)

 Můžete například přidat komentáře do mapy a označit položky pomocí barev.

 ![Mapy kódu &#45; komentářem a položky s příznakem](../modeling/media/codemapstoryboardpaint12a.png)

 Pokud máte nainstalovanou aplikaci Microsoft Outlook, můžete mapu e-mailem odeslat ostatním. Mapu taky můžete exportovat jako obrázek nebo jiný formát.

 ![Mapy kódu &#45; sdílené složky, export, e-mailu](../modeling/media/codemapstoryboardpaint13.png)

## <a name="fix-the-problem-and-show-what-you-did"></a>Vyřešení problému a zobrazení provedené činnosti
 Chcete-li vyřešit tuto chybu, přidejte volání pro `Repaint` k `undo`.

 ![Mapy kódu &#45; přidat chybějící volání metody](../modeling/media/codemapstoryboardpaint14.png)

 Chcete-li potvrdit svou opravu, restartujte relaci ladění a zkuste chybu reprodukovat. Nyní volba **vrátit zpět poslední tah** funguje podle očekávání a potvrdí provedení správné opravy.

 ![Mapy kódu &#45; potvrdit opravu kódu](../modeling/media/codemapstoryboardpaint15.png)

 Můžete aktualizovat mapu, aby zobrazovala provedené opravy.

 ![Mapy kódu &#45; aktualizace mapy s chybějící volání metody](../modeling/media/codemapstoryboardpaint16.png)

 Mapa nyní zobrazuje spojení mezi **zpět** a **Repaint**.

 ![Mapy kódu &#45; mapy aktualizované pomocí volání metody](../modeling/media/codemapstoryboardpaint17.png)

> [!NOTE]
> Při aktualizaci mapy se může zobrazit zpráva, že byl aktualizován index kódu použitý k vytvoření mapy. To znamená, že někdo změnil kód, což způsobilo, že se vaše mapa neshoduje s aktuálním kódem. To vám nezabrání v aktualizaci mapy, ale chcete-li ověřit, že mapa odpovídá kódu, pravděpodobně ji budete muset znovu vytvořit.

 Teď budete hotovi, vaše šetření. Úspěšně jste našli a opravili problém pomocí mapování kódu. Máte k dispozici také mapu, která usnadňuje navigaci v rámci kódu, zapamatuje si, co jste se naučili, a zobrazí kroky, které jste provedli v zájmu vyřešení problému.

## <a name="see-also"></a>Viz také

- [Mapování metod v zásobníku volání při ladění](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)
- [Vizualizace kódu](../modeling/visualize-code.md)
