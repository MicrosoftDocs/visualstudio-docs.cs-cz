---
title: Vlastnosti diagramů
description: Přečtěte si o diagramech a o tom, jak můžete nastavit vlastnosti, které určují, jak se budou diagramy zobrazovat ve vygenerované návrháři.
ms.custom: SEO-VS-2020
ms.date: 10/31/2018
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.dsldiagram
helpviewer_keywords:
- Domain-Specific Language, diagram
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8a060c79866d1746135f8a29aef15ca96dd51f63
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390669"
---
# <a name="properties-of-diagrams"></a>Vlastnosti diagramů
Můžete nastavit vlastnosti, které určují, jak se budou diagramy zobrazovat ve vygenerované návrháři. Můžete například zadat výchozí barvu textu v diagramu.

 Další informace najdete v [tématu Definování jazyka specifického pro doménu.](../modeling/how-to-define-a-domain-specific-language.md) Další informace o použití těchto vlastností najdete v tématu Přizpůsobení a rozšíření jazyka [specifického pro doménu.](../modeling/customizing-and-extending-a-domain-specific-language.md)

 Následující tabulka uvádí vlastnosti diagramů.

|Vlastnost|Popis|Výchozí|
|-|-|-|
|Barva výplně|Barva výplně diagramu|White|
|Barva textu|Barva textu, který se zobrazí v diagramu.|Black|
|Modifikátor přístupu|Modifikátor přístupu třídy (veřejné nebo interní).|Veřejná|
|Vlastní atributy|Slouží k přidání atributů do třídy generovaného kódu.|\<none>|
|Vygeneruje dvojitě odvozený|Pokud `True` , bude vygenerována základní i částečná třída (pro podporu přizpůsobení prostřednictvím přepsání). Další informace najdete v tématu [Přepsání a rozšíření vygenerované třídy](../modeling/overriding-and-extending-the-generated-classes.md).|Ne|
|Má vlastní konstruktor|Pokud , bude ve zdrojovém `True` kódu k dispozici vlastní konstruktor. Další informace najdete v tématu [Přepsání a rozšíření vygenerované třídy](../modeling/overriding-and-extending-the-generated-classes.md).|Ne|
|Modifikátor dědičnosti|Popisuje druh dědičnosti třídy zdrojového kódu, která je generována z diagramu ( `none` `abstract` , nebo `sealed` ).|Žádná|
|Základní diagram|Základní třída tohoto diagramu.|(žádná)|
|Name|Název tohoto diagramu.|Aktuální název|
|Obor názvů|Obor názvů přidružený k tomuto diagramu.|Aktuální obor názvů|
|Reprezentované třídy|Třída kořenové domény, kterou tento diagram představuje.|Aktuální kořenová třída (pokud je k–li křesílná)|
|Poznámky|Neformální poznámky, které jsou přidruženy k tomuto prvku.|\<none>|
|Zpřístupňuje vlastnost Barva výplně jako|Pokud `True` , může uživatel nastavit barvu výplně diagramu generovaného návrháře. Pokud chcete tuto vlastnost nastavit, klikněte pravým tlačítkem na obrazec diagramu a pak klikněte na **Add Exposed (Přidat vystavený).**|Ne|
|Zpřístupňuje barvu textu jako vlastnost|Pokud `True` , uživatel může nastavit barvu textu diagramu ve vygenerované návrháři. Pokud chcete tuto vlastnost nastavit, klikněte pravým tlačítkem na obrazec diagramu a pak klikněte na **Add Exposed (Přidat vystavený).**|Ne|
|Description|Popis, který se používá k zdokumentování generovaného návrháře.|\<none>|
|Zobrazovaný název|Název, který se zobrazí ve vygenerované návrháři pro tento diagram.|\<none>|
|Klíčové slovo nápovědy|Klíčové slovo , které se používá k indexování nápovědy F1 pro tento diagram.|\<none>|

## <a name="see-also"></a>Viz také

[Glosář jazykových nástrojů specifických pro doménu](/previous-versions/bb126564(v=vs.100))