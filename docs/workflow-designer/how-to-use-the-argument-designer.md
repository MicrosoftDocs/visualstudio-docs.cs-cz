---
title: 'Návrhář postupu provádění-postupy: použití návrháře argumentů'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- System.Activities.Presentation.View.ArgumentDesigner.UI
- System.Activities.Presentation.View.DesignTimeArgument.UI
ms.assetid: 64813fd5-1ea1-499a-98b4-ab2a44b7ee5e
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2903c69e3cf50f3ed0392239ee8848a79eb50e20
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75584553"
---
# <a name="how-to-use-the-argument-designer"></a>Postupy: použití návrháře argumentů

Návrhář argumentů usnadňuje umožnění toku dat do aktivity a z ní. Kliknutím na tlačítko **argumenty** v levém dolním rohu plátna návrhu získáte přístup k návrháři. Návrhář obsahuje seznam argumentů, které se zobrazí v tabulkovém formátu a lze je seřadit podle jednotlivých záhlaví sloupců, s výjimkou sloupce **Výchozí hodnota** . Každý argument obsahuje název, typ/výstup/výstup/vlastnost, typ a výchozí hodnotu výrazu (pokud existuje). Název a výchozí hodnota výrazu jsou upravitelná textová pole a typ a směr jsou rozevírací. Další informace naleznete v tématu [proměnné a argumenty (.NET)](/dotnet/framework/windows-workflow-foundation/variables-and-arguments).

## <a name="to-create-a-new-argument"></a>Vytvoření nového argumentu

1. Otevřete pracovní postup nebo řešení aktivity v aplikaci Visual Studio.

2. Kliknutím na tlačítko **argumenty** v levém dolním rohu plátna návrhu otevřete návrhář argumentů. Zobrazí se Návrhář argumentů.

3. Klikněte na prázdný řádek označený jako **argument Create**. Tím se přidá nový řádek s novým argumentem pomocí následujících výchozích hodnot: Argumentx pro **název** , kde x je celé číslo s počáteční hodnotou 1, která se automaticky zvýší a vytvoří jedinečné názvy argumentů, **v** pro **směr**a **řetězec** pro **typ argumentu**. Pro **výchozí hodnotu**se nepřidá žádná hodnota. Tyto hodnoty můžete kdykoli změnit během procesu návrhu pracovního postupu.

    > [!NOTE]
    > Pokud chcete odstranit argument, vyberte ho kliknutím na něj a potom stiskněte klávesu **Delete** .

## <a name="see-also"></a>Viz také:

- [Používání návrháře postupu provádění](developing-applications-with-the-workflow-designer.md)
- [Proměnné a argumenty](/dotnet/framework/windows-workflow-foundation/variables-and-arguments)
