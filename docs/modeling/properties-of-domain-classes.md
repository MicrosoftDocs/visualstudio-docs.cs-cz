---
title: Vlastnosti tříd domény
description: Seznamte se s různými vlastnostmi tříd domény, jako jsou modifikátor přístupu, vlastní atributy a generování dvojitých odvozených tříd.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, domain class
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: eaaae0028d574a521319ae045cdb4f7f1bdafaa2
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390005"
---
# <a name="properties-of-domain-classes"></a>Vlastnosti tříd domény
Doménové třídy mají vlastnosti uvedené v následující tabulce. Informace o třídách domén najdete v tématu [Vysvětlení modelů, tříd](../modeling/understanding-models-classes-and-relationships.md)a relací . Další informace o použití těchto vlastností naleznete v tématu [Customizing and Extending a Domain-Specific Language](../modeling/customizing-and-extending-a-domain-specific-language.md).

|Vlastnost|Popis|Výchozí|
|-|-|-|
|Modifikátor přístupu|Úroveň přístupu třídy domény ( `public` nebo `internal` ).|`public`|
|Vlastní atributy|Slouží k přidání atributů do třídy zdrojového kódu, která je generována z této třídy domény.|\<none>|
|Vygeneruje dvojitě odvozený|Pokud `True` , bude vygenerována základní i částečná třída (pro podporu přizpůsobení prostřednictvím přepsání). Další informace najdete v tématu [Přepsání a rozšíření vygenerované třídy](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|
|Má vlastní konstruktor|Pokud , bude ve zdrojovém `True` kódu k dispozici vlastní konstruktor. Další informace najdete v tématu [Přepsání a rozšíření vygenerované třídy](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|
|Modifikátor dědičnosti|Popisuje druh dědičnosti třídy zdrojového kódu, která je generována z třídy domény ( `none` , `abstract` nebo `sealed` ).|`none`|
|Základní třída|Pokud je tato třída domény odvozena, název základní třídy.|\<none>|
|Name|Název této třídy domény.|Aktuální název|
|Obor názvů|Obor názvů této třídy domény.|Aktuální obor názvů|
|Poznámky|Neformální poznámky, které jsou přidruženy k této třídě domény.|\<none>|
|Description|Popis, který se používá k dokumentování uživatelského rozhraní generovaného návrháře.|\<none>|
|Zobrazovaný název|Název, který se zobrazí ve vygenerované návrháři pro tuto třídu domény.|\<none>|
|Klíčové slovo nápovědy|Volitelné klíčové slovo, které se používá k indexování nápovědy F1 pro tuto třídu domény.|\<none>|

## <a name="see-also"></a>Viz také

- [Nástroje DSL glosář](/previous-versions/bb126564(v=vs.100))