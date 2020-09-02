---
title: 'Postupy: Přidání diagramů tříd do projektů (Návrhář tříd) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- class diagrams, creating
- Class Designer [Visual Studio], opening
ms.assetid: 0eac1b54-2711-4e4b-9654-a0c429c08c8f
caps.latest.revision: 43
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f1a0d10dabdace7ef7ab3805a59b892548cf6556
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72645521"
---
# <a name="how-to-add-class-diagrams-to-projects-class-designer"></a>Postupy: Přidání diagramů tříd do projektů (návrhář tříd)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Chcete-li navrhovat, upravovat a Refaktorovat třídy a jiné typy, přidejte diagram tříd do projektu Visual C# .NET, Visual Basic .NET nebo C++. Chcete-li vizualizovat různé části kódu v projektu, přidejte do projektu více diagramů tříd.

 Diagramy tříd nemůžete vytvářet z projektů, které sdílejí kód napříč více aplikacemi. Chcete-li vytvořit diagramy tříd UML, přečtěte si téma [vytváření projektů a diagramů modelování UML](../modeling/create-uml-modeling-projects-and-diagrams.md).

### <a name="to-add-a-blank-class-diagram-to-a-project"></a>Přidání prázdného diagramu tříd do projektu

1. V Průzkumníku řešení klikněte pravým tlačítkem myši na název projektu. Pak zvolte **Přidat novou položku** nebo **Přidat**, **Nová položka**.

2. V seznamu šablon vyberte **Diagram tříd**. U Visual C++ projektů vyhledejte v části **šablony**a potom v části **Nástroj** Najděte tuto šablonu.

     Diagram tříd se otevře v Návrháři tříd a zobrazí se jako soubor s příponou .cd v hierarchii projektu v Průzkumníku řešení. Pomocí sady nástrojů Návrháře tříd přetáhněte do diagramu tvary a čáry.

3. Chcete-li přidat více diagramů tříd, opakujte kroky v tomto postupu.

### <a name="to-add-a-class-diagram-based-on-existing-types"></a>Přidání diagramu tříd založeného na existujících typech

1. V Průzkumník řešení otevřete místní nabídku soubor třídy a zvolte možnost **Zobrazit diagram tříd**.

     -nebo-

     V **zobrazení tříd**otevřete místní nabídku obor názvů nebo typ a pak zvolte možnost **Zobrazit diagram tříd**.

### <a name="to-display-the-contents-of-a-complete-project-in-a-class-diagram"></a>Zobrazení obsahu kompletního projektu v diagramu tříd

1. V Průzkumník řešení nebo Zobrazení tříd klikněte pravým tlačítkem myši na projekt a zvolte možnost **Zobrazit**a pak zvolte možnost **Zobrazit diagram tříd**.

     Vytvoří se automaticky vyplněný diagram tříd.

## <a name="see-also"></a>Viz také
 [Postupy: vytváření typů pomocí Návrhář tříd](../ide/how-to-create-types-by-using-class-designer.md) [Postupy: zobrazení existujících typů (návrhář tříd)](../ide/how-to-view-existing-types-class-designer.md) [navrhování tříd a typů (návrhář tříd)](../ide/designing-classes-and-types-class-designer.md) [zobrazení typů a vztahů (návrhář tříd)](../ide/viewing-types-and-relationships-class-designer.md) [pro práci s diagramy tříd (návrhář tříd)](../ide/working-with-class-diagrams-class-designer.md)
