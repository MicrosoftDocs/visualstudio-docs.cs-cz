---
title: 'Postupy: Přidání diagramů tříd do projektů (návrhář tříd)'
ms.date: 05/08/2018
ms.topic: conceptual
helpviewer_keywords:
- class diagrams, creating
- Class Designer [Visual Studio], opening
ms.assetid: 0eac1b54-2711-4e4b-9654-a0c429c08c8f
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 87a6c1e996d820724138b6bf38c6440193a4c26b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75588834"
---
# <a name="how-to-add-class-diagrams-to-projects"></a>Postup: Přidání diagramů tříd do projektů

Chcete-li navrhnout, upravit a refaktorovat třídy a další typy, přidejte diagram tříd do projektu Jazyka C#, Visual Basic nebo C++. Chcete-li vizualizovat různé části kódu v projektu, přidejte do projektu více diagramů tříd.

Diagramy tříd nelze vytvářet z projektů, které sdílejí kód ve více aplikacích. Pokud chcete vytvořit diagramy tříd UML, [přečtěte si informace o vytváření projektů modelování A diagramů UML](../../modeling/what-s-new-for-design-in-visual-studio.md).

## <a name="install-the-class-designer-component"></a>Instalace komponenty Návrhář e-class

Pokud jste nenainstalovali komponentu **Návrhář e-up,** nainstalujte ji následujícím postupem.

1. Otevřete **Instalační službu sady Visual Studio** z nabídky Start systému Windows nebo výběrem **možnosti Nástroje** > **získat nástroje a funkce** z panelu nabídek v sadě Visual Studio.

   **Otevře se instalační program sady Visual Studio.**

1. Vyberte kartu **Jednotlivé součásti** a pak přejděte dolů do kategorie **Nástroje kód.**

1. Vyberte **Návrhář evidence a** pak **vyberte Změnit**.

   ![Součást Návrháře tříd v Instalační službě sady Visual Studio](media/class-designer-component.png)

   Komponenta **Návrhář tříd** y se spustí.

## <a name="add-a-blank-class-diagram-to-a-project"></a>Přidání prázdného diagramu třídy do projektu

1. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na uzel projektu a pak zvolte **Přidat** > **novou položku**. Nebo stiskněte **kombinaci kláves Ctrl**+**Shift**+**A**.

   Otevře se dialogové okno **Přidat novou položku.**

2. Rozbalte **obecné běžné položky** > **General**a ze seznamu šablon vyberte **Diagram tříd.** U projektů visual c++ vyhledejte šablonu **Diagram tříd** v kategorii **Utility.**

   > [!NOTE]
   > Pokud šablonu Diagram **tříd** nevidíte, nainstalujte komponentu **Návrhář e-up pro** Visual Studio [podle pokynů.](#install-the-class-designer-component)

   Diagram třídy se otevře v Návrháři tříd a zobrazí se jako soubor s příponou *CD* v **Průzkumníku řešení**. Obrazce a čáry můžete přetáhnout do diagramu z **panelu nástrojů**.

Chcete-li přidat více diagramů tříd, opakujte kroky v tomto postupu.

## <a name="add-a-class-diagram-based-on-existing-types"></a>Přidání diagramu třídy na základě existujících typů

V **Průzkumníku řešení**otevřete místní nabídku souboru třídy (klepněte pravým tlačítkem myši) a pak zvolte **Zobrazit diagram tříd**.

-nebo-

V **zobrazení tříd**otevřete kontextovou nabídku oboru názvů nebo typu a zvolte Zobrazit diagram **tříd**.

> [!TIP]
> Pokud **zobrazení tříd** není otevřené, otevřete zobrazení tříd **z** nabídky **Zobrazení.**

## <a name="to-display-the-contents-of-a-complete-project-in-a-class-diagram"></a>Zobrazení obsahu celého projektu v diagramu třídy

V **Průzkumníku řešení** nebo zobrazení tříd klepněte pravým tlačítkem myši na projekt a zvolte **Zobrazit**a pak zvolte Zobrazit **diagram tříd**.

Je vytvořen diagram automaticky vyplněných tříd.

> [!NOTE]
> Návrhář tříd není k dispozici v projektech .NET Core.

## <a name="see-also"></a>Viz také

- [Postup: Vytváření typů pomocí Návrháře tříd](how-to-create-types.md)
- [Postup: Zobrazení existujících typů](how-to-view-existing-types.md)
- [Návrh a zobrazení tříd a typů](designing-and-viewing-classes-and-types.md)
