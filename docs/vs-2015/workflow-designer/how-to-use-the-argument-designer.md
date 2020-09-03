---
title: 'Postupy: použití návrháře argumentů | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.View.ArgumentDesigner.UI
- System.Activities.Presentation.View.DesignTimeArgument.UI
ms.assetid: 64813fd5-1ea1-499a-98b4-ab2a44b7ee5e
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a436d33bbb7c791f3f192357fded779fa77d148d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659118"
---
# <a name="how-to-use-the-argument-designer"></a>Postupy: Používání návrháře argumentů
V porovnání s předchozími verzemi [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] Návrhář argumentů usnadňuje, aby se data mohla přesměrovat do aktivity a z ní. K návrháři se dostanete kliknutím na tlačítko **argumenty** v levém dolním rohu plátna návrh. Návrhář obsahuje seznam argumentů, které se zobrazí v tabulkovém formátu a lze je seřadit podle jednotlivých záhlaví sloupců, s výjimkou sloupce **Výchozí hodnota** . Každý argument obsahuje název, typ/výstup/výstup/vlastnost, typ a výchozí hodnotu výrazu (pokud existuje). Název a výchozí hodnota výrazu jsou upravitelná textová pole a typ a směr jsou rozevírací. [!INCLUDE[crabout](../includes/crabout-md.md)] argumenty naleznete v tématu [proměnné a argumenty](https://msdn.microsoft.com/library/d03dbe34-5b2e-4f21-8b57-693ee49611b8).

### <a name="to-create-a-new-argument"></a>Vytvoření nového argumentu

1. Otevřete pracovní postup nebo řešení aktivit v [!INCLUDE[vs2010](../includes/vs2010-md.md)] .

2. Kliknutím na tlačítko **argumenty** v levém dolním rohu plátna návrhu otevřete návrhář argumentů. Zobrazí se Návrhář argumentů.

3. Klikněte na prázdný řádek označený jako **argument Create**. Tím se přidá nový řádek s novým argumentem pomocí následujících výchozích hodnot: Argumentx pro **název** , kde x je celé číslo s počáteční hodnotou 1, která se automaticky zvýší a vytvoří jedinečné názvy argumentů, **v** pro **směr**a **řetězec** pro **typ argumentu**. Pro **výchozí hodnotu**se nepřidá žádná hodnota. Tyto hodnoty můžete kdykoli změnit během procesu návrhu pracovního postupu.

    > [!NOTE]
    > Pokud chcete odstranit argument, vyberte ho kliknutím na něj a potom stiskněte klávesu **Delete** .

## <a name="see-also"></a>Viz také
 [Použití proměnných Návrhář postupu provádění](../workflow-designer/using-the-workflow-designer.md) [a argumentů](https://msdn.microsoft.com/library/d03dbe34-5b2e-4f21-8b57-693ee49611b8)