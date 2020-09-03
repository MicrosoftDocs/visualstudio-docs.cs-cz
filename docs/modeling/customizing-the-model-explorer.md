---
title: Přizpůsobení Průzkumníka modelů
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.dsltools.dsldesigner.explorerbehavior
helpviewer_keywords:
- Domain-Specific Language Tools, Domain-Specific Language Explorer
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 625ba0d592d0dbdaa8cb910c366852fe32c5f220
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85548366"
---
# <a name="customizing-the-model-explorer"></a>Přizpůsobení Průzkumníka modelů
Vzhled a chování Průzkumníka pro návrháře jazyka specifického pro doménu můžete změnit následujícím způsobem:

- Změňte název okna.

- Změňte ikonu karty.

- Změňte ikony uzlů.

- Skrytí uzlů.

## <a name="changing-the-window-title"></a>Změna názvu okna
 Chcete-li změnit název okna vygenerovaného Průzkumníka, vyberte **chování Průzkumníka** v **Průzkumníkovi DSL**a potom v okně **vlastnosti** nastavte vlastnost **title** na požadovaný název.

## <a name="changing-the-tab-icon"></a>Změna ikony karty
 Chcete-li změnit ikonu karty Průzkumníka, použijte ikonu 16x16 pixelů v souboru. bmp. Umístěte soubor ikony do složky \DslPackage\Resources\ a potom změňte název souboru na **ModelExplorerToolWindowBitmaps.bmp**. Můžete třeba změnit soubor ikony Setup. ico sady Visual Studio na formát. bmp a přejmenovat ho na **DSLLanguageName\DslPackage\Resources\ModelExplorerToolWindowBitmaps.bmp**. Vygenerovaný Návrhář zobrazí tuto ikonu na kartě v Průzkumníkovi, pokud je ukotven spolu s **Průzkumník řešení**.

## <a name="setting-custom-icons-on-explorer-nodes"></a>Nastavení vlastních ikon na uzlech Průzkumníka
 Můžete přizpůsobit uzly v Průzkumníkovi pomocí nastavení uzlu Průzkumníka. Následující postup ukazuje, jak přidat ikonu na uzel.

#### <a name="to-add-an-icon-to-an-explorer-node"></a>Přidání ikony do uzlu Průzkumníka

1. Vytvořte [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] řešení pomocí šablony řešení Flow úlohy.

2. Vložte soubor. bmp, který obsahuje ikonu 16x16 pixelů ve složce **Dsl\Resources** v řešení.

3. V **Průzkumníku DSL**klikněte pravým tlačítkem myši na **chování Průzkumníka** a pak klikněte na **Přidat nové nastavení uzlu Průzkumníka**.

    Uzel **ExplorerNodeSettings** se zobrazí v uzlu **nastavení vlastního uzlu** .

4. Vyberte **ExplorerNodeSettings**a potom v okně **vlastnosti** nastavte **třídu** na **actor**.

5. Nastavte **ikonu pro zobrazení** na cestu k souboru ikony.

6. Transformujte všechny šablony a pak Sestavte a spusťte řešení.

7. Ve vygenerovaném návrháři otevřete vzorový diagram.

    V Průzkumníkovi by se měl zobrazit tři uzly objektu **actor** , které mají vaši ikonu.

> [!NOTE]
> Pokud jste nastavili ikonu uzlu pro libovolný prvek, který se zobrazí ve vygenerované Průzkumníkovi, zobrazí se ikona všechny uzly Průzkumníka. Pokud není nastavená žádná ikona, v uzlech se zobrazí výchozí ikona.

## <a name="changing-the-name-displayed-on-an-explorer-node"></a>Změna názvu zobrazeného v uzlu Průzkumníka
 Můžete změnit způsob zobrazení názvů prvků modelu v Průzkumníku. Následující postup ukazuje, jak zobrazit název **úkolu** , na který odkazuje **Komentář** v uzlu Comment.

#### <a name="to-display-a-property"></a>Zobrazení vlastnosti

1. Otevřete řešení, které jste vytvořili v předchozím postupu.

2. Ujistěte se, že **Komentář** odkazuje pouze na jednu doménovou třídu nastavením násobnosti role s názvem vlastnosti **subjektům** na hodnotu 0.. 1. Název vlastnosti by měl být **předmětný**a název relace by měl být **CommentReferencesSubject**.

3. V **Průzkumníku DSL**klikněte pravým tlačítkem myši na **chování Průzkumníka** a pak klikněte na **Přidat nové nastavení uzlu Průzkumníka**.

     Uzel **ExplorerNodeSettings** se zobrazí v uzlu **nastavení vlastního uzlu** .

4. Vyberte **ExplorerNodeSettings**a potom v okně **vlastnosti** nastavte **třídu** na **komentovat**.

5. Klikněte pravým tlačítkem na uzel **Komentáře** a pak klikněte na **Přidat novou cestu k vlastnosti**.

     Zobrazí se nový uzel s názvem **zobrazená vlastnost**.

6. Vyberte **zobrazenou vlastnost**a potom v okně **vlastnosti** klikněte na pole hodnota **cesta k vlastnosti**. Vyberte **Komentář**a pak **CommentReferencesSubject**a pak **FlowElement**. Výsledná cesta by měla být podobná **CommentReferencesSubject. Subject/! Předmět**.

7. V poli hodnota **vlastnosti**vyberte možnost **název**.

8. Transformujte všechny šablony a potom Sestavte a spusťte vaše řešení.

9. Ve vygenerovaném návrháři otevřete vzorový diagram.

10. Nakreslete **konektor komentáře** mezi element komentáře a element **Task1** v diagramu.

     Uzel Průzkumníka by měl zobrazit komentář jako **Task1**.

## <a name="hiding-nodes"></a>Skrytí uzlů
 Uzel v Průzkumníkovi můžete skrýt přidáním cesty k uzlu **skryté uzly** v **Průzkumníkovi DSL**. Následující postup ukazuje, jak skrýt uzly **komentářů** .

#### <a name="to-hide-an-explorer-node"></a>Skrytí uzlu Průzkumníka

1. Otevřete řešení, které jste vytvořili v předchozím postupu.

2. V **Průzkumníku DSL**klikněte pravým tlačítkem myši na **chování Průzkumníka** a pak klikněte na **Přidat novou cestu k doméně**.

     V části **skryté uzly**se zobrazí uzel **cesta k doméně** .

3. Vyberte možnost **cesta k doméně**a potom v okně **vlastnosti** klikněte na pole hodnota **definice cesty**. Vyberte **FlowGraph**a pak **FlowGraphHasComments**. Výsledná cesta by měla vypadat podobně jako **FlowGraphHasComments. Comments**

4. Transformujte všechny šablony a potom Sestavte a spusťte vaše řešení.

5. Ve vygenerovaném návrháři otevřete vzorový diagram.

     Průzkumník by měl zobrazit pouze uzel **Actors** a neměl by zobrazovat uzel **Komentáře** .

## <a name="see-also"></a>Viz také

- [Glosář Nástroje DSL](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
