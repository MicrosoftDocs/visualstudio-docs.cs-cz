---
title: Přehled uživatelského rozhraní pro Domain-Specific jazykové nástroje
description: Poskytuje přehled o uživatelském rozhraní řešení nástrojů jazyka specifického pro doménu v aplikaci Visual Studio.
ms.date: 11/04/2016
ms.topic: overview
f1_keywords:
- vs.dsltools.dsldesigner.editor
helpviewer_keywords:
- Domain-Specific Language Tools, user interface
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.custom: SEO-VS-2020
ms.workload:
- multiple
ms.openlocfilehash: 4fe826b373ba2ee468bfe511392eb5564234dc68
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390955"
---
# <a name="overview-of-the-domain-specific-language-tools-user-interface"></a>Přehled uživatelského rozhraní Jazykových nástrojů specifických pro doménu
Při prvním otevření řešení Domain-Specific jazykové nástroje (DSL Tools) v aplikaci Visual Studio bude uživatelské rozhraní vypadat podobně jako na následujícím obrázku.

 ![Návrhář DSL](../modeling/media/dsl_designer.png)

 Následující tabulka vysvětluje, jak se používají části uživatelského rozhraní.

|**Prvek**|**Definition**|
|-|-|
|Diagram|Diagram zobrazuje doménový model.<br /><br /> Diagram má dvě strany. Jedna strana definuje typy prvků ve vašich modelech. Druhá strana definuje, jak se budou vaše modely zobrazovat na obrazovce.|
|Sada nástrojů|Přetáhněte nástroje ze sady nástrojů a přidejte do diagramu třídy domény a typy tvarů. Chcete-li přidat relace, konektory a mapy obrazců, klikněte na nástroj, potom klikněte na zdrojový uzel v diagramu a pak na cílový uzel.|
|Průzkumník modelu DSL|**Průzkumník DSL** se zobrazí, když je definice DSL aktivním oknem. Zobrazuje jako stromovou hodnotu DSL. Průzkumník DSL umožňuje upravovat funkce modelu, které se nezobrazuje v diagramu. Můžete například přidat položky sady nástrojů a přepnout na proces ověřování pomocí programu **DSL Explorer**.|
|Okno Podrobnosti DSL|V okně **Podrobnosti DSL** se zobrazí vlastnosti prvků doménového modelu, které vám umožní řídit, jak se prvky zobrazují a jak se zkopírují a odstraňují prvky.<br /><br /> – Ve výchozím nastavení se vedle **Seznam chyb** a **výstupních** oken zobrazí okno **Podrobnosti DSL** .|

## <a name="the-domain-model-diagram"></a>Diagram doménového modelu
 Diagram doménového modelu je rozdělen do dvou částí. Jedna strana diagramu zobrazuje prvky a vztahy v modelu. Druhá strana ukazuje, jak se má model zobrazit, a obsahuje tvary, které jsou použity k zobrazení prvků a vlastností diagramu modelu. Následující obrázek znázorňuje prvky diagramu.

 ![Návrhář DSL s plaveckou dráhou](../modeling/media/dsl_desinger.png)

 Následující tabulka popisuje některé prvky diagramu doménového modelu.

|**Pojem**|**Definition**|
|-|-|
|Domain – třída|Třídy domény jsou typy prvků ve vašich modelech.<br /><br /> Doménová třída se může v diagramu objevit více než jednou, pokud je cílem více než jednoho vztahu.<br /><br /> Chcete-li přidat doménovou třídu, přetáhněte nástroj doménová třída z **panelu nástrojů** na stranu **třídy a vztahy** na straně diagramu.|
|Doménový vztah|Doménové vztahy jsou typy propojení mezi prvky ve vašich modelech.<br /><br /> *Vztah vložení* indikuje, že cílový element je vlastněn nebo obsažený ve zdrojovém elementu a zobrazuje se jako plná čára. Každý prvek v modelu by měl být cílem jednoho vztahu vložení, takže model vytvoří stromovou strukturu. *Vztah odkazu* označuje obecné propojení mezi prvky modelu a zobrazí se jako přerušovaná čára. Libovolný prvek může mít libovolný počet odkazů na odkazy.<br /><br /> Vytvořte relaci kliknutím na nástroj na **panelu nástrojů**, kliknutím na zdrojová doménová třída a potom kliknutím na cílovou třídu.|
|Tvary a konektory|Tvary určují, jak se mají prvky modelu zobrazovat na diagramu DSL. konektory určují čáry na diagramu DSL, které se dají použít k zobrazení vztahů.<br /><br /> Chcete-li vytvořit tvar nebo spojnici, přetáhněte nástroj na **prvky diagramu** na straně diagramu.|
|Mapy obrazců|Mapa obrazce se zobrazí jako čára v diagramu doménového modelu, propojuje obrazec s doménovou třídou, kterou zobrazuje, nebo konektor k doménovým vztahům, které zobrazuje.|

## <a name="see-also"></a>Viz také

- [Přehled Nástrojů DSL](../modeling/overview-of-domain-specific-language-tools.md)
- [Glosář Nástroje DSL](/previous-versions/bb126564(v=vs.100))
- [Přizpůsobení a rozšíření jazyka specifického pro doménu](../modeling/customizing-and-extending-a-domain-specific-language.md)