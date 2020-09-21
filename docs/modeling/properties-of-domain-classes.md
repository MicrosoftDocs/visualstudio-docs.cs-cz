---
title: Vlastnosti tříd domény
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, domain class
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2b3ff1ece9e57239b49c5dcbef5091a14d8b0fa5
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810025"
---
# <a name="properties-of-domain-classes"></a>Vlastnosti tříd domény
Třídy domény mají vlastnosti v následující tabulce. Informace o třídách domény najdete v tématu [porozumění modelům, třídám a vztahům](../modeling/understanding-models-classes-and-relationships.md). Další informace o tom, jak tyto vlastnosti používat, najdete v tématu [přizpůsobení a rozšíření jazyka specifického pro doménu](../modeling/customizing-and-extending-a-domain-specific-language.md).

|Vlastnost|Popis|Výchozí|
|-|-|-|
|Modifikátor přístupu|Úroveň přístupu třídy domény ( `public` nebo `internal` ).|`public`|
|Vlastní atributy|Slouží k přidání atributů do třídy zdrojového kódu, která je vygenerována z této doménové třídy.|\<none>|
|Generuje dvojitou odvozenou|Pokud `True` bude vygenerována jak základní třída, tak částečná třída (pro podporu přizpůsobení prostřednictvím přepsání). Další informace naleznete v tématu [přepsání a rozšíření vygenerovaných tříd](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|
|Má vlastní konstruktor|Pokud se `True` vlastní konstruktor poskytne ve zdrojovém kódu. Další informace naleznete v tématu [přepsání a rozšíření vygenerovaných tříd](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|
|Modifikátor dědičnosti|Popisuje druh dědění třídy zdrojového kódu, který je generován z třídy domény ( `none` `abstract` nebo `sealed` ).|`none`|
|Základní třída|Pokud je tato doménová Třída odvozena, název základní třídy.|\<none>|
|Název|Název této doménové třídy|Aktuální název|
|Obor názvů|Obor názvů této doménové třídy|Aktuální obor názvů|
|Poznámky|Neformální poznámky, které jsou spojeny s touto doménovou třídou.|\<none>|
|Popis|Popis, který se používá k dokumentaci uživatelského rozhraní vygenerovaného návrháře.|\<none>|
|Zobrazovaný název|Název, který se zobrazí ve vygenerovaném návrháři pro tuto doménovou třídu.|\<none>|
|Klíčové slovo Help|Volitelné klíčové slovo, které se používá k indexování Nápověda F1 pro tuto doménovou třídu.|\<none>|

## <a name="see-also"></a>Viz také

- [Glosář Nástroje DSL](/previous-versions/bb126564(v=vs.100))