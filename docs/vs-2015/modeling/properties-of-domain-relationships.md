---
title: Vlastnosti vztahů domény | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, domain relationships
ms.assetid: 9ccb3dc2-b80c-4585-932f-3c5f87bafbcd
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 48af74aa470f195c1cfbd49ffbabb37e2461251d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49263728"
---
# <a name="properties-of-domain-relationships"></a>Vlastnosti vztahů domény
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vlastnosti v následující tabulce jsou spojeny s doménovým vztahem. Informace o vztahy domén najdete v tématu [porozumění modelům, třídám a vztahům](../modeling/understanding-models-classes-and-relationships.md). Další informace o tom, jak pomocí těchto vlastností najdete v tématu [přizpůsobení a rozšíření jazyka specifického pro doménu](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
|Vlastnost|Popis|Výchozí|  
|--------------|-----------------|-------------|  
|Modifikátor přístupu|Úroveň přístupu doménového vztahu (`public` nebo `internal`).|`public`|  
|Vlastní atributy|Použít k přidání atributů do třídy zdrojový kód, který je generován z doménového vztahu.|\<žádné >|  
|Generuje Double odvozené|Pokud `True`, se vygeneruje základní třídu a částečné třídy (pro podporu přizpůsobení pomocí přepisů). Další informace najdete v tématu [přepisování a rozšiřování třídy generované v](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|  
|Má vlastní konstruktor|Pokud `True`, označuje, že vlastního konstruktoru je poskytována ve zdrojovém kódu. Další informace najdete v tématu [přepisování a rozšiřování třídy generované v](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|  
|Modifikátor dědičnosti|Popisuje druh dědičnosti třídy zdrojový kód, který je generován z doménového vztahu (`none`, `abstract` nebo `sealed`).|\<žádné >|  
|Umožňuje duplicitní položky|Pokud `True`, mohou být vytvořeny duplicitní odkazy tohoto doménového vztahu mezi dvěma stejnými elementy.|`False`|  
|Základní relace|Pokud domény vztah je odvozený, základní vztah doménového vztahu.|\<žádné >|  
|Je vložení|Pokud `True`, je vztah obsažení doménového vztahu. Pokud `False`, je relace vztah odkazu.|\<obě >|  
|Název|Název doménového vztahu.|Aktuální název|  
|Obor názvů|Obor názvů, který je přidružen k doménového vztahu.|Aktuální obor názvů|  
|Poznámky|Neformální poznámky, které jsou spojeny s doménového vztahu.|\<žádné >|  
|Popis|Popis, který se používá k dokumentaci kódu a používá se v uživatelském rozhraní vygenerovaného návrháře.|\<žádné >|  
|Zobrazovaný název|Název, který se zobrazí ve vygenerovaném návrháři u doménového vztahu.|\<žádné >|  
|Klíčové slovo nápovědy|Nepovinné klíčové slovo, je použít k indexování nápovědy klávesy F1 pro doménový vztah.|\<žádné >|  
  
## <a name="see-also"></a>Viz také  
 [Glosář nástrojů jazyka specifického pro doménu](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)



