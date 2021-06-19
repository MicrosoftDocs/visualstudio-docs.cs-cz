---
title: Použití map kódu k ladění aplikací
description: Naučte se používat mapy kódu, které vám pomůžou vyhnout se ztrátě ve velkých základech kódu, neznámém kódu nebo starším kódu.
ms.custom: SEO-VS-2020
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
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 23d05240208c6160968ae0013acfdb9f2a25c973
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388552"
---
# <a name="use-code-maps-to-debug-your-applications"></a>Použití map kódu k ladění aplikací

[Mapy kódu v Visual Studio](../modeling/map-dependencies-across-your-solutions.md) vám můžou pomoct vyhnout se ztrátě ve velkých základech kódu, neznámém kódu nebo starším kódu. Když například ladíte, možná se budete muset podívat na kód v mnoha souborech a projektech. Mapy kódu slouží k procházení částí kódu a pochopení vztahů mezi nimi. Tímto způsobem nemusíte tento kód sledovat v hlavy ani nakreslit samostatný diagram. Když se tedy vaše práce přeruší, mapy kódu vám pomůžou aktualizovat paměť o kódu, na který pracujete.

![Mapování kódu &#45; mapování v kódu](../modeling/media/codemapstoryboardpaint.png)

**Zelená šipka ukazuje, kde se v editoru zobrazuje kurzor**

Podrobnosti o příkazech a akcích, které můžete použít při práci s mapami kódu, najdete v tématu Procházení a [změna uspořádání map kódu.](../modeling/browse-and-rearrange-code-maps.md)

Další informace o [ladění v Visual Studio pomocí nástroje Ladicí program.](../debugger/debugger-feature-tour.md)

> [!NOTE]
> Pokud chcete vytvářet a upravovat mapy kódu, Visual Studio Enterprise edici. V Visual Studio Community a Professional můžete otevřít diagramy vygenerované v edici Enterprise, ale nemůžete je upravovat.

## <a name="understand-the-problem"></a>Pochopení problému
 Předpokládejme, že je chyba v programu kreslení, na kterém právě pracujete. Pokud chcete chybu reprodukovat, otevřete řešení v Visual Studio stisknutím **klávesy F5** spusťte ladění.

 Když nakreslíte čáru a zvolíte **Vrátit zpět poslední tah,** nic se nestane, dokud nenakreslíte další řádek.

 ![Chyba reprodukci &#45; mapování kódu](../modeling/media/codemapstoryboardpaint0.png)

 Začněte s šetřením tak, že vyhledáte `Undo` metodu . Najdete ho ve `PaintCanvas` třídě .

 ![Hledání kódu &#45; kódu](../modeling/media/codemapstoryboardpaint1.png)

## <a name="start-mapping-the-code"></a>Spuštění mapování kódu
 Teď začněte mapovat `undo` metodu a její relace. V editoru kódu přidáte metodu a pole, `undo` na která odkazuje, na novou mapu kódu. Když vytvoříte nové mapování, může zaindexování kódu trvat nějakou dobu. To pomáhá rychlejšímu běhu pozdějších operací.

 ![Mapování kódu &#45; Show method a related fields](../modeling/media/codemapstoryboardpaint3.png)

> [!TIP]
> Zelené zvýraznění zobrazí poslední položky, které byly přidány do mapy. Zelená šipka ukazuje pozici kurzoru v kódu. Šipky mezi položkami představují různé vztahy. Další informace o položkách na mapě získáte tak, že na ně přesunete myš a prozkoumáte jejich popisy.

 ![Zobrazení popisů &#45; kódu](../modeling/media/codemapstoryboardpaint4.png)

## <a name="navigate-and-examine-code-from-the-map"></a>Procházení a zkoumání kódu z mapy
 Pokud chcete zobrazit definici kódu pro jednotlivá pole, dvakrát klikněte na pole na mapě nebo vyberte pole a stiskněte **klávesu F12**. Zelená šipka se přesune mezi položkami na mapě. Kurzor v editoru kódu se také přesune automaticky.

 ![Snímek obrazovky s oknem mapy kódu s vybraným polem historie a oknem editoru kódu, ve kterém jsou zvýrazněné všechny instance historie](../modeling/media/codemapstoryboardpaint5.png)

 ![Snímek obrazovky s oknem mapy kódu s vybraným polem paintObjects a oknem editoru kódu, ve kterém jsou zvýrazněné všechny instance objektů paintObject](../modeling/media/codemapstoryboardpaint5a.png)

> [!TIP]
> Zelenou šipku na mapě můžete také přesunout přesunutím kurzoru v editoru kódu.

## <a name="understand-relationships-between-pieces-of-code"></a>Pochopení vztahů mezi částmi kódu
 Teď chcete vědět, který jiný kód interaguje s `history` poli `paintObjects` a . Můžete do mapy přidat všechny metody, které odkazují na tato pole. Můžete to provést z mapy nebo z editoru kódu.

 ![Mapování kódu &#45; Najít všechny odkazy](../modeling/media/codemapstoryboardpaint6.png)

 ![Otevření mapy kódu z editoru kódu](../modeling/media/codemapstoryboardpaint6a.png)

> [!NOTE]
> Pokud přidáte položky z projektu, který je sdílený mezi více aplikacemi, jako je Windows Phone nebo Windows Store, zobrazí se tyto položky vždy s aktuálně aktivním projektem aplikace na mapě. Pokud tedy změníte kontext na jiný projekt aplikace, kontext na mapě se také změní u všech nově přidaných položek ze sdíleného projektu. Operace, které provádíte s položkou na mapě, se vztahují pouze na ty položky, které sdílejí stejný kontext.

 Změňte rozložení a uspořádejte tak tok vztahů a usnadněte čtení z mapy. Položky kolem mapy lze také přesunout přetažením.

 ![Snímek obrazovky s oknem mapy kódu s otevřenou nabídkou Rozložení a vybraným příkazem Left to Sht](../modeling/media/codemapstoryboardpaint7a.png)

> [!TIP]
> Přírůstkové **rozložení je standardně** zapnuté. To při přidání nových položek mění uspořádání mapy co nejméně. Pokud chcete při každém přidání nových položek změnit uspořádání celé mapy, vypněte **Přírůstkové rozložení**.

 ![Snímek obrazovky s oknem mapy kódu s šipek vztahů mezi poli, která odkazují zleva doprava](../modeling/media/codemapstoryboardpaint7.png)

 Podívejme se na tyto metody. Na mapě poklikejte na **metodu PaintCan dále** nebo vyberte tuto metodu a stiskněte **klávesu F12**. Zjistíte, že tato metoda vytvoří `history` `paintObjects` a jako prázdné seznamy.

 ![Snímek obrazovky s oknem mapy kódu s vybranou metodou PaintCan při výběru a obrázkem fragmentu kódu, který znázorňuje zvýrazněný název metody PainCan na obrázku](../modeling/media/codemapstoryboardpaint8.png)

 Teď zopakujte stejný postup a prozkoumejte `clear` definici metody. Zjistíte, `clear` že provádí některé úlohy pomocí a `paintObjects` `history` . Potom zavolá `Repaint` metodu .

 ![Snímek obrazovky s oknem mapy kódu s vybranou metodou Clear a obrázkem fragmentu kódu znázorňujícím kód pro metodu Clear](../modeling/media/codemapstoryboardpaint9.png)

 Teď prozkoumejte `addPaintObject` definici metody. Provádí také některé úlohy s a `history` `paintObjects` . Volá také `Repaint` .

 ![Snímek obrazovky s oknem mapy kódu s vybranou metodou addPaintObject a obrázkem fragmentu kódu znázorňujícím kód pro metodu addPaintObject](../modeling/media/codemapstoryboardpaint10.png)

## <a name="find-the-problem-by-examining-the-map"></a>Nalezení příčiny problému prozkoumáním mapy
 Zdá se, že všechny metody, které upravovat a `history` `paintObjects` volat `Repaint` . Metoda `undo` ale nevolá `Repaint` , i když upravuje stejná `undo` pole. Takže si myslíte, že tento problém můžete vyřešit voláním `Repaint` z `undo` .

 ![Mapování kódu &#45; Vyhledání chybějícího volání metody](../modeling/media/codemapstoryboardpaint11.png)

 Pokud by nebyla nastavena mapa k zobrazení tohoto chybějícího volání, mohlo by být nalezení tohoto problému obtížnější, zejména u složitějšího kódu.

## <a name="share-your-discovery-and-next-steps"></a>Sdílení zjištění a další kroky
 Předtím, než vy nebo někdo jiný tuto chybu vyřeší, si můžete dělat na mapě poznámky o problému a způsobu jeho řešení.

 ![Položky komentářů a &#45; mapy kódu pro následné sledování](../modeling/media/codemapstoryboardpaint12.png)

 Můžete například přidat komentáře do mapy a označit položky pomocí barev.

 ![Mapování kódu &#45; okomentované a označená položkami](../modeling/media/codemapstoryboardpaint12a.png)

 Pokud máte nainstalovanou aplikaci Microsoft Outlook, můžete mapu e-mailem odeslat ostatním. Mapu taky můžete exportovat jako obrázek nebo jiný formát.

 ![Mapování kódu &#45; Sdílení, export, pošta](../modeling/media/codemapstoryboardpaint13.png)

## <a name="fix-the-problem-and-show-what-you-did"></a>Vyřešení problému a zobrazení provedené činnosti
 Pokud chcete tuto chybu opravit, přidejte volání `Repaint` pro `undo` .

 ![Mapování kódu &#45; Přidání chybějícího volání metody](../modeling/media/codemapstoryboardpaint14.png)

 Chcete-li potvrdit svou opravu, restartujte relaci ladění a zkuste chybu reprodukovat. Teď, když **zvolíte Vrátit zpět poslední tah,** funguje podle očekávání a potvrdíte, že jste provedli správnou opravu.

 ![Potvrzení opravy &#45; kódu v mapě kódu](../modeling/media/codemapstoryboardpaint15.png)

 Můžete aktualizovat mapu, aby zobrazovala provedené opravy.

 ![Mapování kódu &#45; Aktualizace mapy s chybějícím voláním metody](../modeling/media/codemapstoryboardpaint16.png)

 Na mapě se teď zobrazuje odkaz mezi operacemi **zpět** a **Repaint**.

 ![Mapa kódu &#45; Aktualizovaná mapa voláním metody](../modeling/media/codemapstoryboardpaint17.png)

> [!NOTE]
> Při aktualizaci mapy se může zobrazit zpráva, že byl aktualizován index kódu použitý k vytvoření mapy. To znamená, že někdo změnil kód, což způsobilo, že se vaše mapa neshoduje s aktuálním kódem. To vám nezabrání v aktualizaci mapy, ale chcete-li ověřit, že mapa odpovídá kódu, pravděpodobně ji budete muset znovu vytvořit.

 Teď jste s šetřením hotovi. Úspěšně jste našli a opravili problém pomocí mapování kódu. Máte k dispozici také mapu, která usnadňuje navigaci v rámci kódu, zapamatuje si, co jste se naučili, a zobrazí kroky, které jste provedli v zájmu vyřešení problému.

## <a name="see-also"></a>Viz také

- [Mapování metod v zásobníku volání při ladění](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)
- [Vizualizace kódu](../modeling/visualize-code.md)
