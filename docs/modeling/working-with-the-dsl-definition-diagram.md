---
title: Práce s diagramem definice DSL
description: Seznamte se s tím, že diagram definice nástrojů DSL je důležitým nástrojem pro definování jazyka specifického pro doménu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.dsltools.dsldesigner.diagram
- vs.dsltools.dsldesigner.dsldiagram
helpviewer_keywords:
- Domain-Specific Language Tools, diagram
- Domain-Specific Language Tools, Split Tree
- Domain-Specific Language Tools, Show Map Lines
- Domain-Specific Language Tools, Show As Class
- Domain-Specific Language Tools, Bring Tree Here
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d489bfde8b095e35bc652f1cdb7588b07458e48e
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/12/2020
ms.locfileid: "97362831"
---
# <a name="working-with-the-dsl-definition-diagram"></a>Práce s diagramem definice DSL
Diagram [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] definice je důležitým nástrojem pro definování jazyka specifického pro doménu. Můžete přidat prvky do doménového modelu a definovat relace v diagramu a upravit rozložení diagramu, aby bylo čitelnější.

## <a name="the-layout-of-the-diagram"></a>Rozložení diagramu
 [!INCLUDE[dsl](../modeling/includes/dsl_md.md)]Diagram definice obsahuje dva oddíly, oddíly **a** segmenty oddílů a **prvky diagramu** . Oddíl **třídy a vztahy** zobrazuje doménové třídy, doménové vztahy a dědičnost. Oddíl **prvky diagramu** znázorňuje třídy tvarů, třídy konektoru, třídy plaveckých drah a generovaný diagram návrháře.

 Třídy domény se mohou objevit ve více umístěních v oddílech **třídy a vztahů** . Definice doménové třídy zobrazí strom dědičnosti, pokud se jedná o základní třídu pro jiné třídy domény a strom vztahů, pokud se jedná o zdroj vztahů vložení nebo odkazů. Zástupné symboly doménové třídy se zobrazí jako cíle vztahů vložení nebo odkazů. Ve výchozím nastavení se prvky zástupného textu zobrazují se sbaleným oddílem **vlastnosti domény** . Neukazují dědičnost ani vztahy mezi vložením nebo odkazem.

 Když přidáte doménovou třídu, zobrazí se v dolní části oddílu **třídy a relace** . Když přidáte relaci vložení nebo odkazu, je vykreslena pod a napravo od zdrojové třídy domény.

 Při přidávání doménových tříd a relací může být obtížné najít konkrétní doménovou třídu. Doménovou třídu můžete najít tak, že na ni kliknete pravým tlačítkem v **Průzkumníku DSL** a pak kliknete na **najít v diagramu**.

 Následující části popisují, jak můžete změnit vzhled diagramu, aby se usnadnilo jeho čtení.

## <a name="copying-elements"></a>Kopírování elementů
 Můžete použít kopírování, vyjmutí a vložení prvků v diagramu definice DSL.

## <a name="zooming-in-or-out-on-the-diagram"></a>Přiblížení nebo oddálení v diagramu
 K nastavení úrovně přiblížení můžete v diagramu použít panel nástrojů **Návrháře DSL** k přiblížení nebo oddálení.

## <a name="hiding-map-lines"></a>Skrytí čar mapy
 Čáry mapy jsou řádky, které jsou vykresleny mezi doménovou třídou nebo doménovým vztahem a obrazcem nebo konektorem, ke kterému je namapován. Kliknutím na tlačítko **Zobrazit čáry mapy** na panelu nástrojů **Návrháře DSL** můžete skrýt čáry mapy. Chcete-li zobrazit řádky, klikněte znovu na tlačítko.

## <a name="changing-the-diagram-layout"></a>Změna rozložení diagramu
 Rozložení **tříd a vztahů** oddílu můžete změnit následujícím způsobem.

### <a name="expandcollapse"></a>Rozbalit/sbalit
 Velikost prvku obrazce oddílu reprezentujícího doménovou třídu nebo tvar můžete zmenšit tak, že na něj kliknete pravým tlačítkem myši a pak kliknete na **sbalit**. Tím se skryje oddíl **vlastnosti domény** daného tvaru. Pokud chcete znovu zobrazit oddíl **vlastnosti domény** , klikněte na něj pravým tlačítkem myši a pak klikněte na **Rozbalit**.

### <a name="move-updown"></a>Přesunout nahoru/dolů
 Můžete přesunout prvek doménové třídy nebo diagramu nahoru nebo dolů v oddílu tak, že kliknete pravým tlačítkem na prvek a potom kliknete na **Přesunout nahoru** nebo **Přesunout dolů**. Pokud přesunete zástupný prvek, který je zobrazen jako cíl relace vložení nebo odkazu, bude se tento vztah přesouvat s ním.

### <a name="expandcollapse-relationships-tree"></a>Rozbalit nebo sbalit strom vztahů
 Pokud doménová třída přehraje zdrojovou roli v relaci vložení nebo odkazu s jinými doménovými třídami, můžete relace skrýt kliknutím pravým tlačítkem myši na definici doménové třídy a následným kliknutím na **sbalit strom vztahů**. Chcete-li zobrazit relace, klikněte pravým tlačítkem myši na prvek definice a potom klikněte na **položku Rozbalit strom vztahů**.

### <a name="expandcollapse-inheritance-tree"></a>Rozbalit nebo sbalit strom dědičnosti
 Pokud je doménová třída základní třídou dalších tříd domény, můžete skrýt strom dědičnosti kliknutím pravým tlačítkem myši na definici doménové třídy a následným kliknutím na **sbalit strom dědičnosti**. Chcete-li zobrazit strom dědičnosti, klikněte pravým tlačítkem myši na prvek definice a potom klikněte na **položku Rozbalit strom dědičnosti**.

### <a name="bring-tree-here"></a>vložení stromu zde
 Diagram můžete sloučit tak, že kliknete pravým tlačítkem myši na zástupnou doménovou třídu a potom kliknete na **přenést strom**. Zástupná Třída domény se stal prvkem definice a zobrazuje stromy dědičnosti a vztahů. Předchozí prvek definice se zobrazí jako zástupný prvek, pokud je cílem vztahu nebo podřízenosti ve vztahu dědičnosti. v opačném případě zmizí.

### <a name="split-tree"></a>rozdělit strom
 Stromové struktury dědičnosti nebo vztahů můžete přerušit kliknutím pravým tlačítkem myši na definici doménové třídy, která je zobrazí, a následným kliknutím na možnost **rozdělit strom**. Prvek definice se stal zástupným elementem a doménovou třídou definice, která je spolu s jeho stromy dědičnosti a relace, se teď zobrazuje v dolní části oddílu.

### <a name="show-as-class"></a>zobrazit jako třídu
 Pokud relace domény má odvozené relace nebo pokud má relace vložení nebo odkazu s ostatními doménami, můžete relaci zobrazit jako třídu tak, že kliknete pravým tlačítkem na vztah a potom kliknete na tlačítko **Zobrazit jako třídu**. Relace se zobrazí s oddílem **vlastnosti domény** a zobrazí se stromy dědičnosti a vztahů.

## <a name="see-also"></a>Viz také:

- [Glosář Nástroje DSL](/previous-versions/bb126564(v=vs.100))