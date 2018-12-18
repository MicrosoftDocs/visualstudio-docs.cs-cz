---
title: 'Postupy: používání návrháře proměnných | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.View.DesignTimeVariable.UI
ms.assetid: 0318dfb0-bf8f-4f92-9b86-ae4c1b2161ad
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 2348fbe0ed51f72ee1218f7ed1ed2006a48a124d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49265141"
---
# <a name="how-to-use-the-variable-designer"></a>Postupy: používání návrháře proměnných
Návrhář proměnných slouží k vytvoření proměnné pro použití v scénáře datových vazeb a podmíněné příkazy. Návrhář přistupuje po kliknutí **proměnné** tlačítko v levém dolním rohu návrhové plátno. Návrhář obsahuje seznam proměnných, které se zobrazí ve formě tabulky a může být řada seřazena podle všech záhlaví sloupců, s výjimkou **výchozí** sloupce. Každá proměnná obsahuje název, typ proměnné, oboru a výchozí hodnota (pokud existuje). Název a výchozí hodnotu nejsou upravitelné textové pole a typu a rozsahu jsou rozevírací seznamy. Obor je aktivita, která byla vybrána při Návrhář proměnných. Pokud proměnnou nelze vytvořit v rámci oboru výběru, bude výchozí obor na nejbližší nadřazenou aktivitou, která umožňuje proměnných vytvořené v jeho oboru výběru. [!INCLUDE[crabout](../includes/crabout-md.md)] proměnné, naleznete v tématu [proměnné a argumenty](http://msdn.microsoft.com/library/d03dbe34-5b2e-4f21-8b57-693ee49611b8).  
  
 Pořadí řazení se nepoužije, dokud uživatel explicitně používá jeden z řazení ovládacích prvků, zavře a znovu neotevře Návrhář proměnných nebo vytvoří jiné proměnné.  
  
### <a name="to-create-a-new-variable"></a>Chcete-li vytvořit nové proměnné  
  
1.  Otevřete řešení pracovního postupu nebo aktivity v [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)].  
  
2.  Na plátně návrhu vyberte aktivitu v pracovním postupu.  
  
3.  Otevřít návrhář proměnných kliknutím **proměnné** tlačítko v levém dolním rohu návrhové plátno. Otevře se Návrhář proměnných.  
  
4.  Klikněte na prázdný řádek označený **vytvořit proměnnou**. Tím se přidá nový řádek pomocí nové proměnné pomocí následující výchozí hodnoty: variablex pro **název** tam, kde x je celé číslo s počáteční hodnotou 1, který je automatický navýšeno vytvořit jedinečné názvy proměnných,  **Řetězec** pro **typ proměnné**, a **pořadí** pro **oboru**. Přidá se žádná hodnota pro **výchozí**. Tyto hodnoty můžete změnit kdykoli během procesu návrhu pracovního postupu.  
  
    > [!NOTE]
    >  Pokud chcete odstranit proměnnou, kliknutím vyberte proměnnou a stiskněte klávesu **odstranit** klíč.  
  
## <a name="see-also"></a>Viz také  
 [Návrhář postupu provádění](../workflow-designer/using-the-workflow-designer.md)   
 [Proměnné a argumenty](http://msdn.microsoft.com/library/d03dbe34-5b2e-4f21-8b57-693ee49611b8)   
 [Postupy: Používání návrháře argumentů](../workflow-designer/how-to-use-the-argument-designer.md)