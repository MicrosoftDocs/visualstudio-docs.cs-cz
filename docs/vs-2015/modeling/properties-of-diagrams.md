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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
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
|Barva textu|Barva textu, který se zobrazí v diagramu.|Black|
|Modifikátor přístupu|Modifikátor přístupu třídy (veřejné nebo interní).|Veřejná|
|Vlastní atributy|Slouží k přidání atributů do generované třídy kódu.|\<none>|
|Generuje dvojitou odvozenou|Pokud `True` bude vygenerována jak základní třída, tak částečná třída (pro podporu přizpůsobení prostřednictvím přepsání). Další informace naleznete v tématu [přepsání a rozšíření vygenerovaných tříd](../modeling/overriding-and-extending-the-generated-classes.md).|Ne|
|Má vlastní konstruktor|Pokud se `True` vlastní konstruktor poskytne ve zdrojovém kódu. Další informace naleznete v tématu [přepsání a rozšíření vygenerovaných tříd](../modeling/overriding-and-extending-the-generated-classes.md)..|Ne|
|Modifikátor dědičnosti|Popisuje druh dědění třídy zdrojového kódu, který je generován z diagramu ( `none` `abstract` nebo `sealed` ).|Žádné|
|Základní diagram|Základní třída tohoto diagramu|(žádná)|
|Název|Název tohoto diagramu|Aktuální název|
|Obor názvů|Obor názvů, který je přidružen k tomuto diagramu.|Aktuální obor názvů|
|Reprezentovaná třída|Kořenová třída domény, kterou tento diagram představuje.|Aktuální kořenová třída, pokud je k dispozici|
|Poznámky|Neformální poznámky, které jsou spojeny s tímto elementem.|\<none>|
|Zpřístupňuje barvu výplně jako vlastnost.|Pokud `True` uživatel může nastavit barvu výplně diagramu vygenerovaného návrháře. To můžete nastavit tak, že kliknete pravým tlačítkem myši na obrazec diagramu a kliknete na **Přidat explosed**.|Ne|
|Zpřístupňuje barvu textu jako vlastnost|Pokud `True` uživatel může nastavit barvu textu diagramu ve vygenerovaném návrháři. To můžete nastavit tak, že kliknete pravým tlačítkem myši na obrazec diagramu a kliknete na **Přidat explosed**.|Ne|
|Popis|Popis, který se používá k dokumentování vygenerovaného návrháře.|\<none>|
|Zobrazovaný název|Název, který se zobrazí ve vygenerovaném návrháři pro tento diagram.|\<none>|
|Klíčové slovo Help|Klíčové slovo, které se používá k indexování Nápověda F1 pro tento diagram.|\<none>|

## <a name="see-also"></a>Viz také
 [Glosář Nástroje DSL](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
