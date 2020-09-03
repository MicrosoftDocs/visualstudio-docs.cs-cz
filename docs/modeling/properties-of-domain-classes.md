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
ms.openlocfilehash: 2865e6a6d410d661bc628fd9c7f1947516485018
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544180"
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

- [Glosář Nástroje DSL](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)