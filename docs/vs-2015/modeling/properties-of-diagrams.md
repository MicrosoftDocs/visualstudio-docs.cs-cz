---
title: Vlastnosti diagramů | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.dsldiagram
helpviewer_keywords:
- Domain-Specific Language, diagram
ms.assetid: 00bba4b8-6aa6-4027-96cb-4f4c41a77d3c
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 31fb06512457f919b67d41c3fb4096e4c3477426
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652033"
---
# <a name="properties-of-diagrams"></a>Vlastnosti diagramů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete nastavit vlastnosti, které určují, jak se budou diagramy zobrazovat ve vygenerovaném návrháři. Můžete například zadat výchozí barvu textu v diagramu.

 Další informace najdete v tématu [Definování jazyka specifického pro doménu](../modeling/how-to-define-a-domain-specific-language.md). Další informace o tom, jak tyto vlastnosti používat, najdete v tématu [přizpůsobení a rozšíření jazyka specifického pro doménu](../modeling/customizing-and-extending-a-domain-specific-language.md).

 V následující tabulce jsou uvedeny vlastnosti diagramů.

|Vlastnost|Popis|Výchozí|
|--------------|-----------------|-------------|
|Barva výplně|Barva výplně diagramu|White|
|Barva textu|Barva textu, který se zobrazí v diagramu.|zůstane|
|Modifikátor přístupu|Modifikátor přístupu třídy (veřejné nebo interní).|Public|
|Vlastní atributy|Slouží k přidání atributů do generované třídy kódu.|\<none >|
|Generuje dvojitou odvozenou|Pokud `True`, bude vygenerována jak základní třída, tak i částečná třída (pro podporu přizpůsobení prostřednictvím přepsání). Další informace naleznete v tématu [přepsání a rozšíření vygenerovaných tříd](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Má vlastní konstruktor|Pokud `True`, bude ve zdrojovém kódu k dispozici vlastní konstruktor. Další informace naleznete v tématu [přepsání a rozšíření vygenerovaných tříd](../modeling/overriding-and-extending-the-generated-classes.md)..|False|
|Modifikátor dědičnosti|Popisuje druh dědění třídy zdrojového kódu, který je generován z diagramu (`none`, `abstract` nebo `sealed`).|Žádné|
|Základní diagram|Základní třída tohoto diagramu|nTato|
|Name|Název tohoto diagramu|Aktuální název|
|Obor názvů|Obor názvů, který je přidružen k tomuto diagramu.|Aktuální obor názvů|
|Reprezentovaná třída|Kořenová třída domény, kterou tento diagram představuje.|Aktuální kořenová třída, pokud je k dispozici|
|Poznámky|Neformální poznámky, které jsou spojeny s tímto elementem.|\<none >|
|Zpřístupňuje barvu výplně jako vlastnost.|Pokud `True`, uživatel může nastavit barvu výplně diagramu vygenerovaného návrháře. To můžete nastavit tak, že kliknete pravým tlačítkem myši na obrazec diagramu a kliknete na **Přidat explosed**.|False|
|Zpřístupňuje barvu textu jako vlastnost|Pokud `True`, může uživatel nastavit barvu textu diagramu ve vygenerovaném návrháři. To můžete nastavit tak, že kliknete pravým tlačítkem myši na obrazec diagramu a kliknete na **Přidat explosed**.|False|
|Popis|Popis, který se používá k dokumentování vygenerovaného návrháře.|\<none >|
|Zobrazované jméno|Název, který se zobrazí ve vygenerovaném návrháři pro tento diagram.|\<none >|
|Klíčové slovo Help|Klíčové slovo, které se používá k indexování Nápověda F1 pro tento diagram.|\<none >|

## <a name="see-also"></a>Viz také
 [Glosář Nástroje DSL](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
