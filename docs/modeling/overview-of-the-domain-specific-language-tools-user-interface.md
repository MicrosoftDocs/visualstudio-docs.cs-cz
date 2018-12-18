---
title: Přehled uživatelského rozhraní Jazykových nástrojů specifických pro doménu
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.dsltools.dsldesigner.editor
helpviewer_keywords:
- Domain-Specific Language Tools, user interface
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: d54ba969e06f3bd951556f8d8f347977419fc015
ms.sourcegitcommit: 768d7877fe826737bafdac6c94c43ef70bf45076
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/02/2018
ms.locfileid: "50966489"
---
# <a name="overview-of-the-domain-specific-language-tools-user-interface"></a>Přehled uživatelského rozhraní Jazykových nástrojů specifických pro doménu
Při prvním otevření nástroje jazyka specifického pro doménu (DSL Tools) řešení v sadě Visual Studio, uživatelské rozhraní bude vypadat podobně jako na následujícím obrázku.

 ![Návrhář DSL](../modeling/media/dsl_designer.png)

 Následující tabulka vysvětluje, jak se používají částí uživatelského rozhraní.

|**Element**|**Definice**|
|-|-|
|diagram|Diagram zobrazuje doménový model.<br /><br /> Diagram má dvě strany. Jedna strana definuje typy prvků ve vašich modelech. Druhé straně definuje, jak vaše modely se zobrazí na obrazovce.|
|Sada nástrojů|Přetáhněte nástroje z panelu nástrojů přidejte doménovými třídami a obrazce typy do diagramu. Chcete-li přidat vztahy, konektory a mapy obrazců, klikněte na nástroje a pak klikněte na zdrojový uzel v diagramu a cílový uzel.|
|Průzkumník modelu DSL|**Průzkumník modelu DSL** se zobrazí, když je aktivní okno Definice DSL. Jako strom zobrazuje DSL. Průzkumník modelu DSL umožňuje upravit funkce modelu, které nejsou zobrazeny v diagramu. Například můžete přidat položky panelu nástrojů a přepnout na proces ověření pomocí **Průzkumník DSL**.|
|Okno podrobností DSL|**Podrobnosti DSL** okno zobrazuje vlastnosti domény prvky modelu, které umožňují řídit způsob zobrazení prvků, a jak jsou prvky zkopírovat a odstranit.<br /><br /> – Ve výchozím nastavení **podrobnosti DSL** okna se zobrazí vedle **seznam chyb** a **výstup** systému windows.|

## <a name="the-domain-model-diagram"></a>Diagram modelu domény
 Diagram modelu domény je rozdělena na dva oddíly. Straně diagram zobrazuje prvky a vztahy v modelu. Druhé straně ukazuje, jak je model, který se má zobrazit a zahrnuje tvary, které se používají k zobrazení prvky a vlastnosti diagramu modelu. Následující obrázek ukazuje prvky diagramu.

 ![Návrhář DSL s plavecké dráhy](../modeling/media/dsl_desinger.png)

 Následující tabulka popisuje některé prvky diagramu modelu domény.

|**Termín**|**Definice**|
|-|-|
|Doménová třída|Doménové třídy jsou typy prvků ve vašich modelech.<br /><br /> Doménová třída může objevit více než jednou v diagramu, pokud je cílem více než jedna relace.<br /><br /> Chcete-li přidat doménovou třídou, přetáhněte nástroj třídy domény z **nástrojů** k **třídám a vztahům** diagramu vedle sebe.|
|Doménový vztah|Doménové vztahy jsou typy odkazů mezi prvky ve vašich modelů.<br /><br /> *Vztah obsažení* označuje, že cílový element je ve vlastnictví nebo obsažená v tomto elementu zdroje a zobrazí se jako plná čára. Každý prvek v modelu by měla být cílem jeden vztah obsažení, tak, aby model tvoří strom. A *odkazovat na relaci* označuje obecné propojení prvků modelu a zobrazí se bude zobrazovat jako přerušovaná čára. Libovolný prvek může mít libovolný počet referenční odkazy.<br /><br /> Vytvoření relace po kliknutí na nástroj **nástrojů**, kliknutím na zdrojové doménové třídy a pak levým na cílové třídy.|
|Obrazců a konektorů|Tvary určit, jak mají být zobrazeny prvky modelu na diagram DSL., konektory určit řádky v diagramu DSL, který slouží k zobrazení relací.<br /><br /> Chcete-li vytvořit obrazec nebo spojnici, přetáhněte nástroj, který **elementů diagramu** diagramu vedle sebe.|
|Mapy obrazců|Mapa obrazce se zobrazí jako řádek na diagram modelu domény propojení doménová třída, která se zobrazí obrazec nebo spojnici na doménový vztah, který se zobrazí.|

## <a name="see-also"></a>Viz také

- [Přehled Nástrojů DSL](../modeling/overview-of-domain-specific-language-tools.md)
- [Glosář nástrojů jazyka specifického pro doménu](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
- [Přizpůsobení a rozšíření jazyka specifického pro doménu](../modeling/customizing-and-extending-a-domain-specific-language.md)