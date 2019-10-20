---
title: Vlastnosti tříd domény | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, domain class
ms.assetid: a3993995-19e7-4761-a972-b1de89131a1b
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 91599e17fc132001de9fbb1a62a62918321a2dea
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651998"
---
# <a name="properties-of-domain-classes"></a>Vlastnosti tříd domény
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Třídy domény mají vlastnosti v následující tabulce. Informace o třídách domény najdete v tématu [porozumění modelům, třídám a vztahům](../modeling/understanding-models-classes-and-relationships.md). Další informace o tom, jak tyto vlastnosti používat, najdete v tématu [přizpůsobení a rozšíření jazyka specifického pro doménu](../modeling/customizing-and-extending-a-domain-specific-language.md).

|Vlastnost|Popis|Výchozí|
|--------------|-----------------|-------------|
|Modifikátor přístupu|Úroveň přístupu doménové třídy (`public` nebo `internal`).|`public`|
|Vlastní atributy|Slouží k přidání atributů do třídy zdrojového kódu, která je vygenerována z této doménové třídy.|\<none >|
|Generuje dvojitou odvozenou|Pokud `True`, bude vygenerována jak základní třída, tak i částečná třída (pro podporu přizpůsobení prostřednictvím přepsání). Další informace naleznete v tématu [přepsání a rozšíření vygenerovaných tříd](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|
|Má vlastní konstruktor|Pokud `True`, bude ve zdrojovém kódu k dispozici vlastní konstruktor. Další informace naleznete v tématu [přepsání a rozšíření vygenerovaných tříd](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|
|Modifikátor dědičnosti|Popisuje druh dědění třídy zdrojového kódu, který je generován z třídy domény (`none`, `abstract` nebo `sealed`).|`none`|
|Základní třída|Pokud je tato doménová Třída odvozena, název základní třídy.|\<none >|
|Name|Název této doménové třídy|Aktuální název|
|Obor názvů|Obor názvů této doménové třídy|Aktuální obor názvů|
|Poznámky|Neformální poznámky, které jsou spojeny s touto doménovou třídou.|\<none >|
|Popis|Popis, který se používá k dokumentaci uživatelského rozhraní vygenerovaného návrháře.|\<none >|
|Zobrazované jméno|Název, který se zobrazí ve vygenerovaném návrháři pro tuto doménovou třídu.|\<none >|
|Klíčové slovo Help|Volitelné klíčové slovo, které se používá k indexování Nápověda F1 pro tuto doménovou třídu.|\<none >|

## <a name="see-also"></a>Viz také
 [Glosář Nástroje DSL](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
