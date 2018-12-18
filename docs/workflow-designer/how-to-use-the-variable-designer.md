---
title: 'Návrhář postupu provádění - postupy: použití návrháře proměnné'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Presentation.View.DesignTimeVariable.UI
ms.assetid: 0318dfb0-bf8f-4f92-9b86-ae4c1b2161ad
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dc180df4a9be83c0f0b755bffd7ed40009b41497
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
ms.locfileid: "31970096"
---
# <a name="how-to-use-the-variable-designer"></a>Postupy: použití návrháře proměnné

Proměnné návrháře se používá k vytvoření proměnné pro použití v scénáře datových vazeb a podmíněné příkazy. Návrhář přistupuje kliknutím **proměnné** tlačítko v levém horním rohu na plátno návrhu. Návrhář obsahuje seznam proměnných, které jsou uvedeny ve formě tabulky a lze seřadit podle jednotlivých záhlaví sloupců, s výjimkou **výchozí** sloupce. Každá proměnná obsahuje název, typ proměnné, oboru a výchozí hodnota (pokud existuje). Název a výchozí hodnotou jsou upravitelných textových polí a typu a rozsahu rozevírací seznamy. Rozsah je aktivita, která byla vybrána, když byl vyvolán návrháře proměnné. Pokud proměnnou nelze vytvořit v rámci oboru výběru, bude výchozí oboru pro nejbližší nadřazený aktivitu výběru, která umožňuje proměnné, které chcete vytvořit ve svém oboru. Další informace najdete v tématu [proměnné a argumenty (.NET)](/dotnet/framework/windows-workflow-foundation/variables-and-arguments).

 Pořadí řazení není použita, dokud uživatel explicitně používá jednu řazení ovládacích prvků, zavře a znovu otevře návrháře proměnné nebo vytvoří jiné proměnné.

## <a name="to-create-a-new-variable"></a>Chcete-li vytvořit nové proměnné

1.  Otevřete řešení pracovního postupu nebo aktivity v sadě Visual Studio.

2.  Na plátně návrhu vyberte aktivitu v pracovním postupu.

3.  Otevřete návrháře proměnné kliknutím **proměnné** tlačítko v levém horním rohu na plátno návrhu. Zobrazí se Návrhář proměnné.

4.  Klikněte na prázdný řádek označený **vytvoření proměnné**. Přidá nový řádek s nové proměnné pomocí následující výchozí hodnoty: variablex pro **název** tam, kde x je celočíselná a má počáteční hodnotu 1, který se automaticky zvýší k vytvoření jedinečné názvy proměnných,  **Řetězec** pro **typ proměnné**, a **pořadí** pro **oboru**. Přidá se žádná hodnota pro **výchozí**. Tyto hodnoty můžete změnit kdykoli během procesu návrhu pracovního postupu.

    > [!NOTE]
    > Chcete-li odstranit proměnnou, kliknutím vyberte proměnnou a stiskněte klávesu **odstranit** klíč.

## <a name="see-also"></a>Viz také

- [Používání návrháře postupu provádění](../workflow-designer/using-the-workflow-designer.md)
- [Proměnné a argumenty](/dotnet/framework/windows-workflow-foundation/variables-and-arguments)
- [Postupy: Používání návrháře argumentů](../workflow-designer/how-to-use-the-argument-designer.md)