---
title: Přehled uživatelského rozhraní Jazykových nástrojů specifických pro doménu
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.dsltools.dsldesigner.editor
helpviewer_keywords:
- Domain-Specific Language Tools, user interface
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8aacaa43dc9a95faee886440623fb4238abf9be5
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748358"
---
# <a name="overview-of-the-domain-specific-language-tools-user-interface"></a>Přehled uživatelského rozhraní Jazykových nástrojů specifických pro doménu
Při prvním otevření řešení Nástroje DSL (DSL Tools) v aplikaci Visual Studio bude uživatelské rozhraní vypadat podobně jako na následujícím obrázku.

 ![Návrhář DSL](../modeling/media/dsl_designer.png)

 Následující tabulka vysvětluje, jak se používají části uživatelského rozhraní.

|**Element**|**Definition**|
|-|-|
|diagram|Diagram zobrazuje doménový model.<br /><br /> Diagram má dvě strany. Jedna strana definuje typy prvků ve vašich modelech. Druhá strana definuje, jak se budou vaše modely zobrazovat na obrazovce.|
|Sada nástrojů|Přetáhněte nástroje ze sady nástrojů a přidejte do diagramu třídy domény a typy tvarů. Chcete-li přidat relace, konektory a mapy obrazců, klikněte na nástroj, potom klikněte na zdrojový uzel v diagramu a pak na cílový uzel.|
|Průzkumník modelu DSL|**Průzkumník DSL** se zobrazí, když je definice DSL aktivním oknem. Zobrazuje jako stromovou hodnotu DSL. Průzkumník DSL umožňuje upravovat funkce modelu, které se nezobrazuje v diagramu. Můžete například přidat položky sady nástrojů a přepnout na proces ověřování pomocí programu **DSL Explorer**.|
|Okno Podrobnosti DSL|V okně **Podrobnosti DSL** se zobrazí vlastnosti prvků doménového modelu, které vám umožní řídit, jak se prvky zobrazují a jak se zkopírují a odstraňují prvky.<br /><br /> – Ve výchozím nastavení se vedle **Seznam chyb** a **výstupních** oken zobrazí okno **Podrobnosti DSL** .|

## <a name="the-domain-model-diagram"></a>Diagram doménového modelu
 Diagram doménového modelu je rozdělen do dvou částí. Jedna strana diagramu zobrazuje prvky a vztahy v modelu. Druhá strana ukazuje, jak se má model zobrazit, a obsahuje tvary, které jsou použity k zobrazení prvků a vlastností diagramu modelu. Následující obrázek znázorňuje prvky diagramu.

 ![Návrhář DSL s plaveckou dráhou](../modeling/media/dsl_desinger.png)

 Následující tabulka popisuje některé prvky diagramu doménového modelu.

|**Doby**|**Definition**|
|-|-|
|Domain – třída|Třídy domény jsou typy prvků ve vašich modelech.<br /><br /> Doménová třída se může v diagramu objevit více než jednou, pokud je cílem více než jednoho vztahu.<br /><br /> Chcete-li přidat doménovou třídu, přetáhněte nástroj doménová třída z **panelu nástrojů** na stranu **třídy a vztahy** na straně diagramu.|
|Doménový vztah|Doménové vztahy jsou typy propojení mezi prvky ve vašich modelech.<br /><br /> *Vztah vložení* indikuje, že cílový element je vlastněn nebo obsažený ve zdrojovém elementu a zobrazuje se jako plná čára. Každý prvek v modelu by měl být cílem jednoho vztahu vložení, takže model vytvoří stromovou strukturu. *Vztah odkazu* označuje obecné propojení mezi prvky modelu a zobrazí se jako přerušovaná čára. Libovolný prvek může mít libovolný počet odkazů na odkazy.<br /><br /> Vytvořte relaci kliknutím na nástroj na **panelu nástrojů**, kliknutím na zdrojová doménová třída a potom kliknutím na cílovou třídu.|
|Tvary a konektory|Tvary určují, jak se mají prvky modelu zobrazovat na diagramu DSL. konektory určují čáry na diagramu DSL, které se dají použít k zobrazení vztahů.<br /><br /> Chcete-li vytvořit tvar nebo spojnici, přetáhněte nástroj na **prvky diagramu** na straně diagramu.|
|Mapy obrazců|Mapa obrazce se zobrazí jako čára v diagramu doménového modelu, propojuje obrazec s doménovou třídou, kterou zobrazuje, nebo konektor k doménovým vztahům, které zobrazuje.|

## <a name="see-also"></a>Viz také:

- [Přehled Nástrojů DSL](../modeling/overview-of-domain-specific-language-tools.md)
- [Glosář Nástroje DSL](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
- [Přizpůsobení a rozšíření jazyka specifického pro doménu](../modeling/customizing-and-extending-a-domain-specific-language.md)