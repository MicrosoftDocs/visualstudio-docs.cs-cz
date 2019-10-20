---
title: 'Postupy: použití návrháře proměnných | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.View.DesignTimeVariable.UI
ms.assetid: 0318dfb0-bf8f-4f92-9b86-ae4c1b2161ad
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4744864824da5efb238e9af1a5a12fcef79ea4ff
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659078"
---
# <a name="how-to-use-the-variable-designer"></a>Postupy: použití návrháře proměnných
Návrhář proměnných se používá k vytvoření proměnných pro použití ve scénářích datové vazby a podmíněných příkazech. K návrháři se dostanete kliknutím na tlačítko **proměnné** v levém dolním rohu plátna návrh. Návrhář obsahuje seznam proměnných, které se zobrazí v tabulkovém formátu, a lze je seřadit podle jednotlivých záhlaví sloupců, s výjimkou **výchozího** sloupce. Každá proměnná obsahuje název, typ proměnné, rozsah a výchozí hodnotu (pokud existuje). Název a výchozí hodnota jsou upravitelná textová pole a typ a rozsah jsou rozevírací seznam. Obor je aktivita, která byla vybrána při vyvolání návrháře proměnných. Pokud proměnnou nelze vytvořit v rámci oboru výběru, bude výchozí hodnota oboru nejbližší předchůdce aktivity výběru, který umožňuje vytvoření proměnných ve svém rozsahu. [!INCLUDE[crabout](../includes/crabout-md.md)] proměnných naleznete v tématu [proměnné a argumenty](https://msdn.microsoft.com/library/d03dbe34-5b2e-4f21-8b57-693ee49611b8).

 Pořadí řazení se nepoužije, dokud uživatel explicitně nepoužije jeden z ovládacích prvků pro řazení, zavře a znovu neotevře Návrhář proměnných nebo vytvoří jinou proměnnou.

### <a name="to-create-a-new-variable"></a>Vytvoření nové proměnné

1. Otevřete pracovní postup nebo řešení aktivity v [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)].

2. Na plátně pro návrh vyberte aktivitu v pracovním postupu.

3. Kliknutím na tlačítko **proměnné** v levém dolním rohu plátna návrhu otevřete návrhář proměnných. Zobrazí se Návrhář proměnných.

4. Klikněte na prázdný řádek označený **Proměnná vytvořit proměnnou**. Tím se přidá nový řádek s novou proměnnou pomocí následujících výchozích hodnot: variablex pro **název** , kde x je celé číslo s počáteční hodnotou 1, která se automaticky zvýší a vytvoří jedinečné názvy proměnných, **řetězec** pro **proměnnou. typ**a **posloupnosti** **oboru**. Pro **výchozí**hodnotu není přidána žádná hodnota. Tyto hodnoty můžete kdykoli změnit během procesu návrhu pracovního postupu.

    > [!NOTE]
    > Pokud chcete proměnnou odstranit, vyberte ji kliknutím na ni a potom stiskněte klávesu **Delete** .

## <a name="see-also"></a>Viz také
 [Použití proměnných Návrhář postupu provádění](../workflow-designer/using-the-workflow-designer.md) [a argumentů](https://msdn.microsoft.com/library/d03dbe34-5b2e-4f21-8b57-693ee49611b8) [: použití návrháře argumentů](../workflow-designer/how-to-use-the-argument-designer.md)