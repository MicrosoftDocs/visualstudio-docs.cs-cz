---
title: 'Návrhář postupu provádění-postupy: použití návrháře proměnných'
description: Zjistěte, jak můžete pomocí návrháře proměnných vytvořit proměnné pro použití ve scénářích datové vazby a podmíněných příkazech.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- System.Activities.Presentation.View.DesignTimeVariable.UI
ms.assetid: 0318dfb0-bf8f-4f92-9b86-ae4c1b2161ad
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e8dc5e402fcf3bedabe2b0f7fe606dfe807525ab
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/10/2020
ms.locfileid: "94437824"
---
# <a name="how-to-use-the-variable-designer"></a>Postupy: Používání návrháře proměnných

Návrhář proměnných se používá k vytvoření proměnných pro použití ve scénářích datové vazby a podmíněných příkazech. K návrháři se dostanete kliknutím na tlačítko **proměnné** v levém dolním rohu plátna návrh. Návrhář obsahuje seznam proměnných, které se zobrazí v tabulkovém formátu, a lze je seřadit podle jednotlivých záhlaví sloupců, s výjimkou **výchozího** sloupce. Každá proměnná obsahuje název, typ proměnné, rozsah a výchozí hodnotu (pokud existuje). Název a výchozí hodnota jsou upravitelná textová pole a typ a rozsah jsou rozevírací seznam. Obor je aktivita, která byla vybrána při vyvolání návrháře proměnných. Pokud proměnnou nelze vytvořit v rámci oboru výběru, bude výchozí hodnota oboru nejbližší předchůdce aktivity výběru, který umožňuje vytvoření proměnných ve svém rozsahu. Další informace naleznete v tématu [proměnné a argumenty (.NET)](/dotnet/framework/windows-workflow-foundation/variables-and-arguments).

 Pořadí řazení se nepoužije, dokud uživatel explicitně nepoužije jeden z ovládacích prvků pro řazení, zavře a znovu neotevře Návrhář proměnných nebo vytvoří jinou proměnnou.

## <a name="to-create-a-new-variable"></a>Vytvoření nové proměnné

1. Otevřete pracovní postup nebo řešení aktivity v aplikaci Visual Studio.

2. Na plátně pro návrh vyberte aktivitu v pracovním postupu.

3. Kliknutím na tlačítko **proměnné** v levém dolním rohu plátna návrhu otevřete návrhář proměnných. Zobrazí se Návrhář proměnných.

4. Klikněte na prázdný řádek označený **Proměnná vytvořit proměnnou**. Tím se přidá nový řádek s novou proměnnou pomocí následujících výchozích hodnot: variablex pro **název** , kde x je celé číslo s počáteční hodnotou 1, která se automaticky zvyšuje, aby se vytvořil jedinečný název proměnné, **řetězec** pro **typ proměnné** a **sekvence** pro daný **obor**. Pro **výchozí** hodnotu není přidána žádná hodnota. Tyto hodnoty můžete kdykoli změnit během procesu návrhu pracovního postupu.

    > [!NOTE]
    > Pokud chcete proměnnou odstranit, vyberte ji kliknutím na ni a potom stiskněte klávesu **Delete** .

## <a name="see-also"></a>Viz také

- [Použití návrháře postupu provádění](developing-applications-with-the-workflow-designer.md)
- [Proměnné a argumenty](/dotnet/framework/windows-workflow-foundation/variables-and-arguments)
- [Postupy: Používání návrháře argumentů](../workflow-designer/how-to-use-the-argument-designer.md)
