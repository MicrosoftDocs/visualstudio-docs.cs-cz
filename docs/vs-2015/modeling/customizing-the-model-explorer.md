---
title: Přizpůsobení Průzkumníka modelů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.dsltools.dsldesigner.explorerbehavior
helpviewer_keywords:
- Domain-Specific Language Tools, Domain-Specific Language Explorer
ms.assetid: d2926444-9408-41d8-a27e-3fd0c416f9ac
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 77999eea0a76088368ff5e7ee66f9088dc45efa5
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49175939"
---
# <a name="customizing-the-model-explorer"></a>Přizpůsobení Průzkumníka modelů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Je můžete změnit vzhled a chování Průzkumníka pro návrháře jazyka specifického pro doménu následujícím způsobem:  
  
-   Změňte název okna.  
  
-   Změníte ikonu karty.  
  
-   Změňte ikony pro uzly.  
  
-   Skrytí uzlů.  
  
## <a name="changing-the-window-title"></a>Změna záhlaví okna  
 Chcete-li změnit název okna Průzkumníka vygenerovaný, vyberte **chování Průzkumníka** v **Průzkumník DSL**a pak v **vlastnosti** okno, nastavte  **Název** vlastnost na název, který chcete.  
  
## <a name="changing-the-tab-icon"></a>Změna ikony kartu  
 Chcete-li změnit ikonu kartu pro Průzkumníka, použijte ikonu rozměr 16 × 16 pixelů v souboru BMP. Umístěte soubor ikony ve složce \DslPackage\Resources\ a potom změňte název souboru **ModelExplorerToolWindowBitmaps.bmp**. Například můžete změnit [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] setup.ico Ikona soubor formátu BMP a přejmenujte ho na **DSLLanguageName\DslPackage\Resources\ModelExplorerToolWindowBitmaps.bmp**. Vygenerovaného návrháře se zobrazí tato ikona na kartě aplikace explorer, když je ukotveno spolu s **Průzkumníka řešení**.  
  
## <a name="setting-custom-icons-on-explorer-nodes"></a>Nastavení vlastní ikony na uzly Průzkumníka  
 Uzly v Průzkumníku lze přizpůsobit pomocí nastavení uzlu Průzkumníka. Následující postup ukazuje, jak přidat ikonu k uzlu.  
  
#### <a name="to-add-an-icon-to-an-explorer-node"></a>Přidání ikony k uzlu Průzkumníka  
  
1.  Vytvoření [!INCLUDE[dsl](../includes/dsl-md.md)] řešení pomocí šablony toku úkolů řešení.  
  
2.  Umístění souboru .bmp, který obsahuje ikonu rozměr 16 × 16 pixelů v **Dsl\Resources** složky v řešení.  
  
3.  V **Průzkumník DSL**, klikněte pravým tlačítkem na **chování Průzkumníka** a potom klikněte na tlačítko **přidat nové nastavení uzlu Průzkumníka**.  
  
     **ExplorerNodeSettings** uzel se zobrazí v části **vlastní nastavení uzlu** uzlu.  
  
4.  Vyberte **ExplorerNodeSettings**a pak v **vlastnosti** okno, nastavte **třídy** k **objektu Actor**.  
  
5.  Nastavte **ikonu k zobrazení** na cestu k souboru ikony.  
  
6.  Transformovat všechny šablony a potom sestavíte a spustíte řešení.  
  
7.  Ve vygenerovaném návrháři Otevřete diagram vzorku.  
  
     V Průzkumníku by se měla zobrazit tři **objektu Actor** uzly, které mají vaší ikony.  
  
> [!NOTE]
>  Pokud jste nastavili uzel ikona pro libovolný element, který se zobrazí v Průzkumníku vygenerovaný, všechny uzly Průzkumníka se zobrazí ikona. Pokud byla nastavena žádná ikona, uzly se zobrazí ikona výchozí.  
  
## <a name="changing-the-name-displayed-on-an-explorer-node"></a>Změna názvu, zobrazí v uzlu Průzkumníka  
 Můžete změnit způsob zobrazení názvy prvků modelu v Průzkumníku. Následující postup ukazuje, jak zobrazit název **úloh** , na který odkazuje **komentář** v uzel komentáře.  
  
#### <a name="to-display-a-property"></a>Chcete-li zobrazit vlastnosti  
  
1.  Otevřete řešení, které jste vytvořili v předchozím kroku.  
  
2.  Ujistěte se, že **komentář** odkazuje jenom jednu doménovou třídu nastavením násobnost role s názvem vlastnosti **Predmety** k 0..1. Název vlastnosti by měla být **subjektu**, a název relace by měla být **CommentReferencesSubject**.  
  
3.  V **Průzkumník DSL**, klikněte pravým tlačítkem na **chování Průzkumníka** a potom klikněte na tlačítko **přidat nové nastavení uzlu Průzkumníka**.  
  
     **ExplorerNodeSettings** uzel se zobrazí v části **vlastní nastavení uzlu** uzlu.  
  
4.  Vyberte **ExplorerNodeSettings**a pak v **vlastnosti** okno, nastavte **třídy** k **komentář**.  
  
5.  Klikněte pravým tlačítkem **komentář** uzel a potom klikněte na **přidat novou cestu vlastnosti**.  
  
     Zobrazí se nový uzel s názvem **zobrazena vlastnost**.  
  
6.  Vyberte **zobrazena vlastnost**a pak v **vlastnosti** okna, klikněte na pole hodnoty z **cesta k vlastnosti**. Vyberte **komentář**, pak **CommentReferencesSubject**, pak **FlowElement**. Výsledná cesta by měla vypadat podobně jako **CommentReferencesSubject.Subject/! Předmět**.  
  
7.  V poli hodnota **vlastnost**vyberte **název**.  
  
8.  Transformovat všechny šablony a potom sestavíte a spustíte vašeho řešení.  
  
9. Ve vygenerovaném návrháři Otevřete diagram vzorku.  
  
10. Vykreslení **komentář konektor** mezi elementu komentář a **Task1** prvku v diagramu.  
  
     Komentář, jako by se zobrazit uzlu Průzkumníka **Task1**.  
  
## <a name="hiding-nodes"></a>Skrytí uzlů  
 Uzel můžete skrýt v Průzkumníku tak, že přidáte jeho cesta k **skryté uzly** uzlu **Průzkumník DSL**. Následující postup ukazuje, jak skrýt **komentář** uzly.  
  
#### <a name="to-hide-an-explorer-node"></a>Chcete-li skrýt uzlu Průzkumníka  
  
1.  Otevřete řešení, které jste vytvořili v předchozím kroku.  
  
2.  V **Průzkumník DSL**, klikněte pravým tlačítkem na **chování Průzkumníka** a potom klikněte na tlačítko **přidat novou cestu domény**.  
  
     A **doménové cestě** uzel se zobrazí v části **skryté uzly**.  
  
3.  Vyberte **doménová cesta**a pak v **vlastnosti** okna, klikněte na pole hodnoty z **cesta definice**. Vyberte **FlowGraph**, pak **FlowGraphHasComments**. Výsledná cesta by měla vypadat podobně jako **FlowGraphHasComments.Comments**  
  
4.  Transformovat všechny šablony a potom sestavíte a spustíte vašeho řešení.  
  
5.  Ve vygenerovaném návrháři Otevřete diagram vzorku.  
  
     V Průzkumníku by měl zobrazit pouze **Actors** uzel a by neměl zobrazit **komentáře** uzlu.  
  
## <a name="see-also"></a>Viz také  
 [Glosář nástrojů jazyka specifického pro doménu](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)



