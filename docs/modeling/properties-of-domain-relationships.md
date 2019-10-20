---
title: Vlastnosti vztahů domény
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, domain relationships
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 26de877643e25413168d074d85a2aeab0794adc1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658195"
---
# <a name="properties-of-domain-relationships"></a>Vlastnosti vztahů domény
Vlastnosti v následující tabulce jsou spojeny s doménovým vztahem. Informace o doménových relacích najdete v tématu [porozumění modelům, třídám a vztahům](../modeling/understanding-models-classes-and-relationships.md). Další informace o tom, jak tyto vlastnosti používat, najdete v tématu [přizpůsobení a rozšíření jazyka specifického pro doménu](../modeling/customizing-and-extending-a-domain-specific-language.md).

|Vlastnost|Popis|Výchozí|
|-|-|-|
|Modifikátor přístupu|Úroveň přístupu k doménovým vztahům (`public` nebo `internal`).|`public`|
|Vlastní atributy|Slouží k přidání atributů do třídy zdrojového kódu, která je vygenerována z doménového vztahu.|\<none >|
|Generuje dvojitou odvozenou|Pokud `True`, je vygenerována jak základní třída, tak částečná třída (pro podporu přizpůsobení prostřednictvím přepsání). Další informace naleznete v tématu [přepsání a rozšíření vygenerovaných tříd](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|
|Má vlastní konstruktor|Pokud `True`, označuje, že vlastní konstruktor je k dispozici ve zdrojovém kódu. Další informace naleznete v tématu [přepsání a rozšíření vygenerovaných tříd](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|
|Modifikátor dědičnosti|Popisuje druh dědění třídy zdrojového kódu, který je generován z doménového vztahu (`none`, `abstract` nebo `sealed`).|\<none >|
|Povoluje duplicity|V případě `True` lze mezi stejnými dvěma prvky vytvořit duplicitní propojení doménových vztahů.|`False`|
|Základní vztahy|Pokud je vztah domény odvozený, základní vztah doménového vztahu.|\<none >|
|Je vkládání|Pokud je `True`, doménovým vztahem je vztah vložení. Pokud je `False`, jedná se o vztah odkazu.|\<both >|
|Name|Název doménového vztahu.|Aktuální název|
|Obor názvů|Obor názvů, který je přidružený k doménovým vztahům.|Aktuální obor názvů|
|Poznámky|Neformální poznámky, které jsou spojeny s doménovým vztahem.|\<none >|
|Popis|Popis, který se používá k dokumentu kódu a který se používá v uživatelském rozhraní vygenerovaného návrháře.|\<none >|
|Zobrazované jméno|Název, který se zobrazí ve vygenerovaném návrháři doménového vztahu.|\<none >|
|Klíčové slovo Help|Volitelné klíčové slovo, které se používá k indexování Nápověda F1 pro doménový vztah.|\<none >|

## <a name="see-also"></a>Viz také

- [Glosář Nástroje DSL](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)