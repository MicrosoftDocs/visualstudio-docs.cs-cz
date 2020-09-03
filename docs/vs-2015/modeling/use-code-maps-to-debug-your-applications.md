---
title: Použití map kódu k ladění aplikací | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 33f8d583c369ae365b8d7063a7b0c1d6353a3c56
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659470"
---
# <a name="use-code-maps-to-debug-your-applications"></a>Použití map kódu k ladění aplikací
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Mapy kódu vám mohou přispět k tomu, abyste se ztratili v rozsáhlých základech kódu, neznámém kódu nebo starším kódu. Při ladění bude například pravděpodobně nutné ověřit kód v mnoha souborech a projektech. Pomocí map kódu se můžete pohybovat v jednotlivých částech kódu a pochopit vztahy mezi nimi. Tímto způsobem není nutné sledovat tento kód ve vaší hlavě nebo nakreslit samostatný diagram. Takže když dojde k přerušení práce, mapy kódu vám pomůžou aktualizovat vaši paměť o kódu, se kterým pracujete.

 ![Mapa kódu &#45; relace map v kódu](../modeling/media/codemapstoryboardpaint.png "CodeMapStoryboardPaint")

 **Zelená šipka ukazuje, kde se kurzor zobrazuje v editoru.**

 Podrobnosti o příkazech a akcích, které můžete použít při práci s mapami kódu, naleznete v tématu [procházení a změna uspořádání map kódu](../modeling/browse-and-rearrange-code-maps.md).

## <a name="understand-the-problem"></a>Pochopení problému
 Předpokládejme, že je chyba v programu kreslení, na kterém právě pracujete. Chcete-li reprodukování chyby, otevřete řešení v aplikaci Visual Studio a stisknutím klávesy **F5** spusťte ladění.

 Když nakreslíte čáru a kliknete na tlačítko **vrátit poslední tah**, nic se nestane, dokud nebudete kreslit další řádek.

 ![Mapa kódu &#45; chyba reprodukci](../modeling/media/codemapstoryboardpaint0.png "CodeMapStoryboardPaint0")

 Takže spustíte šetření pomocí hledání `Undo` metody. Najdete ho ve `PaintCanvas` třídě.

 ![Mapa kódu &#45; najít kód](../modeling/media/codemapstoryboardpaint1.png "CodeMapStoryboardPaint1")

## <a name="start-mapping-the-code"></a>Spuštění mapování kódu
 Nyní spusťte mapování `undo` metody a jejích vztahů. V editoru kódu přidejte `undo` metodu a pole, na která odkazuje, na novou mapu kódu. Když vytvoříte nové mapování, může zaindexování kódu trvat nějakou dobu. To pomáhá rychlejšímu běhu pozdějších operací.

 ![Mapa kódu &#45; zobrazit metodu a související pole](../modeling/media/codemapstoryboardpaint3.png "CodeMapStoryboardPaint3")

> [!TIP]
> Zelené zvýraznění zobrazí poslední položky, které byly přidány do mapy. Zelená šipka ukazuje pozici kurzoru v kódu. Šipky mezi položkami představují různé vztahy. Můžete získat další informace o položkách v mapě přesunutím myši na ně a prozkoumáním jejich popisků.

 ![Mapa kódu &#45; zobrazit popisy tlačítek](../modeling/media/codemapstoryboardpaint4.png "CodeMapStoryboardPaint4")

## <a name="navigate-and-examine-code-from-the-map"></a>Procházení a zkoumání kódu z mapy
 Chcete-li zobrazit definici kódu pro každé pole, dvakrát klikněte na pole na mapě nebo vyberte pole a stiskněte klávesu **F12**. Zelená šipka se přesune mezi položkami na mapě. Kurzor v editoru kódu se také přesune automaticky.

 ![Mapování kódu &#45; kontrole definice pole](../modeling/media/codemapstoryboardpaint5.png "CodeMapStoryboardPaint5")

 ![Mapování kódu &#45; kontrole definice pole](../modeling/media/codemapstoryboardpaint5a.png "CodeMapStoryboardPaint5A")

> [!TIP]
> Zelenou šipku na mapě můžete také přesunout přesunutím kurzoru v editoru kódu.

## <a name="understand-relationships-between-pieces-of-code"></a>Pochopení vztahů mezi částmi kódu
 Nyní chcete zjistit, který jiný kód komunikuje s poli `history` a `paintObjects` . Můžete do mapy přidat všechny metody, které odkazují na tato pole. To lze provést z mapy nebo z editoru kódu.

 ![Mapa kódu &#45; najít všechny odkazy](../modeling/media/codemapstoryboardpaint6.png "CodeMapStoryboardPaint6")

 ![Otevření mapy kódu z editoru kódu](../modeling/media/codemapstoryboardpaint6a.PNG "CodeMapStoryboardPaint6A")

> [!NOTE]
> Pokud přidáte položky z projektu, který je sdílen mezi více aplikacemi, například Windows Phone nebo Windows Store, pak se tyto položky vždy zobrazí s aktuálně aktivním projektem aplikace na mapě. Takže pokud změníte kontext na jiný projekt aplikace, pak kontext na mapě také změní všechny nově přidané položky ze sdíleného projektu. Operace, které provádíte s položkou na mapě, se vztahují pouze na ty položky, které sdílejí stejný kontext.

 Změňte rozložení a uspořádejte tak tok vztahů a usnadněte čtení z mapy. Položky kolem mapy lze také přesunout přetažením.

 ![Mapa kódu &#45; změnit rozložení](../modeling/media/codemapstoryboardpaint7a.png "CodeMapStoryboardPaint7A")

> [!TIP]
> Ve výchozím nastavení je **přírůstkové rozložení** zapnuté. To při přidání nových položek mění uspořádání mapy co nejméně. Chcete-li změnit uspořádání celé mapy při každém přidání nových položek, vypněte **přírůstkové rozložení**.

 ![Mapa kódu &#45; změnit rozložení](../modeling/media/codemapstoryboardpaint7.png "CodeMapStoryboardPaint7")

 Podívejme se na tyto metody. Na mapě poklikejte na metodu **PaintCanvas** , nebo vyberte tuto metodu a stiskněte klávesu **F12**. Zjistíte, že tato metoda vytváří `history` a `paintObjects` jako prázdné seznamy.

 ![Mapování kódu &#45; kontrole definice metody](../modeling/media/codemapstoryboardpaint8.png "CodeMapStoryboardPaint8")

 Nyní opakujte stejný postup, abyste prozkoumali `clear` definici metody. Naučíte se, že `clear` provádí některé úkoly s `paintObjects` a `history` . Pak zavolá `Repaint` metodu.

 ![Mapování kódu &#45; kontrole definice metody](../modeling/media/codemapstoryboardpaint9.png "CodeMapStoryboardPaint9")

 Teď si Projděte `addPaintObject` definici metody. Provádí také některé úlohy s `history` a `paintObjects` . Volá také `Repaint` .

 ![Mapování kódu &#45; kontrole definice metody](../modeling/media/codemapstoryboardpaint10.png "CodeMapStoryboardPaint10")

## <a name="find-the-problem-by-examining-the-map"></a>Nalezení příčiny problému prozkoumáním mapy
 Zdá se, že všechny metody, které mění `history` a `paintObjects` volají `Repaint` . `undo`Metoda sice ale nevolá `Repaint` , i když `undo` mění stejná pole. Proto si myslíte, že tento problém můžete vyřešit voláním `Repaint` z `undo` .

 ![Mapa kódu &#45; najít chybějící volání metody](../modeling/media/codemapstoryboardpaint11.png "CodeMapStoryboardPaint11")

 Pokud by nebyla nastavena mapa k zobrazení tohoto chybějícího volání, mohlo by být nalezení tohoto problému obtížnější, zejména u složitějšího kódu.

## <a name="share-your-discovery-and-next-steps"></a>Sdílení zjištění a další kroky
 Předtím, než vy nebo někdo jiný tuto chybu vyřeší, si můžete dělat na mapě poznámky o problému a způsobu jeho řešení.

 ![Mapa kódu &#45; komentáře a označení položek pro další zpracování](../modeling/media/codemapstoryboardpaint12.png "CodeMapStoryboardPaint12")

 Můžete například přidat komentáře do mapy a označit položky pomocí barev.

 ![Mapa kódu &#45; v komentářích a položkách označených příznakem](../modeling/media/codemapstoryboardpaint12a.png "CodeMapStoryboardPaint12A")

 Pokud máte nainstalovanou aplikaci Microsoft Outlook, můžete mapu e-mailem odeslat ostatním. Mapu taky můžete exportovat jako obrázek nebo jiný formát.

 ![Mapa kódu &#45; sdílet, exportovat, poštu](../modeling/media/codemapstoryboardpaint13.png "CodeMapStoryboardPaint13")

## <a name="fix-the-problem-and-show-what-you-did"></a>Vyřešení problému a zobrazení provedené činnosti
 Chcete-li tuto chybu vyřešit, přidejte volání pro `Repaint` do `undo` .

 ![Mapa kódu &#45; přidat chybějící volání metody](../modeling/media/codemapstoryboardpaint14.png "CodeMapStoryboardPaint14")

 Chcete-li potvrdit svou opravu, restartujte relaci ladění a zkuste chybu reprodukovat. Nyní volba **vrátit zpět poslední tah** funguje podle očekávání a potvrdí, že jste provedli správnou opravu.

 ![Mapa kódu &#45; potvrdit opravu kódu](../modeling/media/codemapstoryboardpaint15.png "CodeMapStoryboardPaint15")

 Můžete aktualizovat mapu, aby zobrazovala provedené opravy.

 ![Mapa kódu &#45; aktualizovat mapu s chybějícím voláním metody](../modeling/media/codemapstoryboardpaint16.png "CodeMapStoryboardPaint16")

 Vaše mapa nyní zobrazuje propojení mezi **akcemi zpět** a **repaint**.

 ![Mapa kódu &#45; aktualizovat mapu pomocí volání metody](../modeling/media/codemapstoryboardpaint17.png "CodeMapStoryboardPaint17")

> [!NOTE]
> Při aktualizaci mapy se může zobrazit zpráva, že byl aktualizován index kódu použitý k vytvoření mapy. To znamená, že někdo změnil kód, což způsobilo, že se vaše mapa neshoduje s aktuálním kódem. To vám nezabrání v aktualizaci mapy, ale chcete-li ověřit, že mapa odpovídá kódu, pravděpodobně ji budete muset znovu vytvořit.

 Nyní je vaše šetření hotovo. Úspěšně jste našli a opravili problém pomocí mapování kódu. Máte k dispozici také mapu, která usnadňuje navigaci v rámci kódu, zapamatuje si, co jste se naučili, a zobrazí kroky, které jste provedli v zájmu vyřešení problému.

## <a name="see-also"></a>Viz také
 [Mapování metod v zásobníku volání při ladění](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md) [kódu vizualizace](../modeling/visualize-code.md)
