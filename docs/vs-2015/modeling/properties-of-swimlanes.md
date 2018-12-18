---
title: Vlastnosti plaveckých drah | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.dsltools.dsldesigner.swimlane
helpviewer_keywords:
- Domain-Specific Language, swimlane
ms.assetid: 47edbc2d-09e4-48ac-b4d1-5268a06a27e6
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: c914703d4cbe48e516d1d4e1aa48afb20c9e1cfe
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49189929"
---
# <a name="properties-of-swimlanes"></a>Vlastnosti drah
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Plaveckých drah můžete přidat do diagramu. Plaveckých drah rozdělit svislý nebo vodorovný oblasti diagramu. Můžete definovat další obrazce, která se zobrazí uvnitř plaveckých drah. Další informace najdete v tématu [jak se definuje jazyk specifický pro doménu](../modeling/how-to-define-a-domain-specific-language.md). Další informace o tom, jak pomocí těchto vlastností najdete v tématu [přizpůsobení a rozšíření jazyka specifického pro doménu](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
 Plaveckých drah mít vlastnosti, které jsou uvedeny v následující tabulce.  
  
|Vlastnost|Popis|Výchozí|  
|--------------|-----------------|-------------|  
|Barva výplně těla|Barva výplně těla plavecké.|Prázdné|  
|Barva výplně záhlaví|Barva výplně záhlaví plavecké.|DarkGray|  
|Barva oddělovače|Barva oddělovací čáry.|LightGray|  
|Styl oddělovací čáry|Styl oddělovací čáry (`Solid`, `Dash`, `Dot`, `DashDot`, `DashDotDot`, nebo `Custom`).|`Dash`|  
|Tloušťka oddělovací|Tloušťka oddělovací čáry v palcích.|0.03125|  
|Barva textu|Barva, která je použitá pro dekoratéry textu přidružené k této plavecké dráhy.|Černá|  
|Modifikátor přístupu|Úroveň přístupu třídy (`public` nebo `internal`).|Public|  
|Vlastní atributy|Použít k přidání atributů do třídy kód, který je generován z této plavecké dráhy.|\<žádné >|  
|Generuje Double odvozené|Pokud `True`, se vygeneruje základní třídu a částečné třídy (pro podporu přizpůsobení pomocí přepisů). Další informace najdete v tématu [přepisování a rozšiřování třídy generované v](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Má vlastní konstruktor|Pokud `True`, poskytneme vám vlastního konstruktoru ve zdrojovém kódu. Další informace najdete v tématu [přepisování a rozšiřování třídy generované v](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Modifikátor dědičnosti|Popisuje druh dědičnosti třídy zdrojový kód, který je generován z plavecké (`none`, `abstract` nebo `sealed`).|žádná|  
|Základní Plavecká dráha|Základní třída této plavecké dráhy.|(žádné)|  
|Název|Název této plavecké dráhy.|Aktuální název|  
|Obor názvů|Obor názvů, který je přidružen k této plavecké dráhy.|Aktuální obor názvů|  
|Popis typu|Jak je definován popisek (`fixed`, `variable`, nebo `none`). Pokud `fixed`, pak hodnota `Fixed Tooltip Text` vlastnost se používá; Pokud `variable`, pak je popis definovaný ve vlastním kódu.|\<žádné >|  
|Poznámky|Neformální poznámky přidružené k této plavecké dráhy.|\<žádné >|  
|Zarovnání|Vodorovné nebo svislé zarovnání.|Svisle|  
|Počáteční výška|Počáteční výška této plavecké dráhy v palcích. Vztahuje se jenom u vodorovných plaveckých drah.|0|  
|Počáteční šířka|Počáteční šířka této plavecké dráhy v palcích. Vztahuje se jenom u svislých plaveckých drah.|0|  
|Zpřístupní barvu textu|Pokud `True`, může uživatel nastavit barvu plaveckou dráhou ve vygenerovaném návrháři. Nastavit, klikněte pravým tlačítkem myši na obrazec plavecké dráhy a klikněte na tlačítko **přidat vystavený**.|False|  
|Popis|Používá se k dokumentu vygenerovaného návrháře.|\<žádné >|  
|Zobrazovaný název|Název, který se zobrazí ve vygenerovaném návrháři k odkazování na této plavecké dráhy třídy.|\<žádné >|  
|Pevný Text popisu tlačítka|Text, který se používá pro pevný popis.|\<žádné >|  
|Klíčové slovo nápovědy|Klíčové slovo, je použít k indexování nápovědy klávesy F1 pro této plavecké dráhy.|\<žádné >|  
  
## <a name="see-also"></a>Viz také  
 [Glosář nástrojů jazyka specifického pro doménu](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)



