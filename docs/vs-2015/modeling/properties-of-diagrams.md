---
title: Vlastnosti diagramů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.dsltools.dsldesigner.dsldiagram
helpviewer_keywords:
- Domain-Specific Language, diagram
ms.assetid: 00bba4b8-6aa6-4027-96cb-4f4c41a77d3c
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 9db932bb5e19cdc10dde3cd8330c4a57208a0c2d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49280901"
---
# <a name="properties-of-diagrams"></a>Vlastnosti diagramů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete nastavit vlastnosti, které určují, jak diagramy se zobrazí ve vygenerovaném návrháři. Můžete například zadat výchozí barva textu v diagramu.  
  
 Další informace najdete v tématu [jak se definuje jazyk specifický pro doménu](../modeling/how-to-define-a-domain-specific-language.md). Další informace o tom, jak pomocí těchto vlastností najdete v tématu [přizpůsobení a rozšíření jazyka specifického pro doménu](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
 V následující tabulce jsou uvedeny vlastnosti diagramů.  
  
|Vlastnost|Popis|Výchozí|  
|--------------|-----------------|-------------|  
|Barva výplně|Barva výplně diagramu.|Prázdné|  
|Barva textu|Barva textu, který se zobrazí v diagramu.|Černá|  
|Modifikátor přístupu|Modifikátor přístupu třídy (veřejné nebo interní).|Public|  
|Vlastní atributy|Umožňuje přidat atributy vytvořené třídě kódu.|\<žádné >|  
|Generuje Double odvozené|Pokud `True`, se vygeneruje základní třídu a částečné třídy (pro podporu přizpůsobení pomocí přepisů). Další informace najdete v tématu [přepisování a rozšiřování třídy generované v](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Má vlastní konstruktor|Pokud `True`, poskytneme vám vlastního konstruktoru ve zdrojovém kódu. Další informace najdete v tématu [přepisování a rozšiřování třídy generované v](../modeling/overriding-and-extending-the-generated-classes.md)...|False|  
|Modifikátor dědičnosti|Popisuje druh dědičnosti třídy zdrojový kód, který je generován z diagramu (`none`, `abstract` nebo `sealed`).|Žádné|  
|Základní Diagram|Základní třída tento diagram.|(žádné)|  
|Název|Název tohoto diagramu.|Aktuální název|  
|Obor názvů|Obor názvů, který je přidružený tento diagram.|Aktuální obor názvů|  
|Reprezentovaná třída|Kořenová třída domény, který představuje tento diagram.|Pokud je k dispozici aktuální kořenová třída|  
|Poznámky|Neformální poznámky, které jsou spojeny s tímto elementem.|\<žádné >|  
|Barva výplně zveřejní jako vlastnost|Pokud `True`, může uživatel nastavit barvu výplně diagramu vygenerovaného návrháře. Nastavit, klikněte pravým tlačítkem myši na obrazec diagram a klikněte na tlačítko **přidat Explosed**.|False|  
|Zpřístupní barvu textu jako vlastnost|Pokud `True`, může uživatel nastavit barvu textu diagramu ve vygenerovaném návrháři. Nastavit, klikněte pravým tlačítkem myši na obrazec diagram a klikněte na tlačítko **přidat Explosed**.|False|  
|Popis|Popis, který se používá k dokumentu vygenerovaného návrháře.|\<žádné >|  
|Zobrazovaný název|Název, který se zobrazí ve vygenerovaném návrháři u tohoto diagramu.|\<žádné >|  
|Klíčové slovo nápovědy|Klíčové slovo, je použít k indexování nápovědy klávesy F1 pro tento diagram.|\<žádné >|  
  
## <a name="see-also"></a>Viz také  
 [Glosář nástrojů jazyka specifického pro doménu](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)



