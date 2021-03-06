---
title: Vlastnosti vztahů domény
description: Přečtěte si o vlastnostech přidružených k doméně relationshop, jako jsou modifikátory přístupu, vlastní atributy a generují Double odvozené.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, domain relationships
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fc92bbc32a454208f3d455734b7697a2e69037b4
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390656"
---
# <a name="properties-of-domain-relationships"></a>Vlastnosti vztahů domény
Vlastnosti v následující tabulce jsou spojeny s doménovým vztahem. Informace o doménových relacích najdete v tématu [porozumění modelům, třídám a vztahům](../modeling/understanding-models-classes-and-relationships.md). Další informace o tom, jak tyto vlastnosti použít, najdete v tématu [přizpůsobení a rozšíření Domain-Specificho jazyka](../modeling/customizing-and-extending-a-domain-specific-language.md).

|Vlastnost|Popis|Výchozí|
|-|-|-|
|Modifikátor přístupu|Úroveň přístupu k doménovým vztahům ( `public` nebo `internal` ).|`public`|
|Vlastní atributy|Slouží k přidání atributů do třídy zdrojového kódu, která je vygenerována z doménového vztahu.|\<none>|
|Generuje dvojitou odvozenou|Pokud `True` je vygenerována jak základní třída, tak částečná třída (pro podporu přizpůsobení prostřednictvím přepsání). Další informace naleznete v tématu [přepsání a rozšíření vygenerovaných tříd](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|
|Má vlastní konstruktor|Pokud `True` znamená, že je ve zdrojovém kódu k dispozici vlastní konstruktor. Další informace naleznete v tématu [přepsání a rozšíření vygenerovaných tříd](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|
|Modifikátor dědičnosti|Popisuje druh dědičnosti třídy zdrojového kódu, která je generována z doménového vztahu ( `none` `abstract` nebo `sealed` ).|\<none>|
|Povoluje duplicity|Pokud `True` je možné vytvořit duplicitní propojení doménových vztahů mezi stejnými dvěma prvky.|`False`|
|Základní vztahy|Pokud je vztah domény odvozený, základní vztah doménového vztahu.|\<none>|
|Je vkládání|Pokud `True` je doménovým vztahem relace vložení. Je-li, jedná se o vztah `False` odkazu.|\<both>|
|Name|Název doménového vztahu.|Aktuální název|
|Obor názvů|Obor názvů, který je přidružený k doménovým vztahům.|Aktuální obor názvů|
|Poznámky|Neformální poznámky, které jsou spojeny s doménovým vztahem.|\<none>|
|Description|Popis, který se používá k dokumentu kódu a který se používá v uživatelském rozhraní vygenerovaného návrháře.|\<none>|
|Zobrazovaný název|Název, který se zobrazí ve vygenerovaném návrháři doménového vztahu.|\<none>|
|Klíčové slovo Help|Volitelné klíčové slovo, které se používá k indexování Nápověda F1 pro doménový vztah.|\<none>|

## <a name="see-also"></a>Viz také

- [Glosář Nástroje DSL](/previous-versions/bb126564(v=vs.100))