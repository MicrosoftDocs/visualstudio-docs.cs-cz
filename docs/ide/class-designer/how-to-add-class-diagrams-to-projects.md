---
title: 'Postupy: Přidání diagramů tříd do projektů (návrhář tříd)'
ms.date: 05/08/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- class diagrams, creating
- Class Designer [Visual Studio], opening
ms.assetid: 0eac1b54-2711-4e4b-9654-a0c429c08c8f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 133f15f6c160e9ec48b1db4ab8713023e492cbae
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/24/2018
ms.locfileid: "42901295"
---
# <a name="how-to-add-class-diagrams-to-projects"></a>Postupy: Přidání diagramů tříd do projektů

Návrh, upravit a Refaktorovat třídy a další typy, přidání diagramu tříd do projektu C#, Visual Basic nebo C++. Pokud chcete vizualizovat různé části kódu v projektu, přidáte více diagramů tříd do projektu.

Diagramy tříd nelze vytvořit z projektů, které sdílejí kód mezi více aplikacemi. Vytvoření diagramů tříd UML, najdete v tématu [vytvořit modelování projektů a diagramů UML](../../modeling/create-uml-modeling-projects-and-diagrams.md).

## <a name="install-the-class-designer-component"></a>Nainstalovat součást návrháře tříd

Pokud používáte Visual Studio 2017 a jste dosud nenainstalovali **návrhář tříd** komponenty, postupujte podle těchto kroků k její instalaci.

1. Otevřít **instalační program sady Visual Studio** v nabídce Windows Start nebo tak, že vyberete **nástroje** > **stažení nástrojů a funkcí** z řádku nabídek v sadě Visual Studio.

   **Instalační program sady Visual Studio** otevře.

1. Vyberte **jednotlivé komponenty** kartu a potom přejděte dolů k položce **kódu nástroje** kategorie.

1. Vyberte **návrhář tříd** a pak vyberte **změnit**.

   ![Třídy součástí návrháře v instalačním programu Visual Studio](media/class-designer-component.png)

   **Návrhář tříd** komponenta spustí instalaci.

## <a name="add-a-blank-class-diagram-to-a-project"></a>Přidání prázdného diagramu tříd do projektu

1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na uzel projektu a klikněte na tlačítko **přidat** > **nová položka**. Také můžete stisknout klávesu **Ctrl**+**Shift**+**A**.

   **Přidat novou položku** otevře se dialogové okno.

2. Rozbalte **společné položky** > **Obecné**a pak vyberte **Diagram tříd** ze seznamu šablon. Pro projekty Visual C++, podívejte **nástroj** kategorií se najít **Diagram tříd** šablony.

   > [!NOTE]
   > Pokud se nezobrazí **Diagram tříd** šablony, [postupujte podle kroků](#install-the-class-designer-component) k instalaci **návrhář tříd** komponentu sady Visual Studio.

   Diagram tříd se otevře v Návrháři tříd a zobrazí se jako soubor, který má *.cd* rozšíření v **Průzkumníka řešení**. Tvary a čáry můžete přetáhnout do diagramu z **nástrojů**.

Chcete-li přidat více diagramů tříd, opakujte kroky v tomto postupu.

## <a name="add-a-class-diagram-based-on-existing-types"></a>Přidání diagramu tříd založeného na existujících typech

V **Průzkumníka řešení**, otevřete místní nabídku souboru třídy (klikněte pravým tlačítkem) a klikněte na tlačítko **zobrazit Diagram tříd**.

-nebo-

V **zobrazení tříd**, otevřete kontextovou nabídku obor názvů nebo typ a klikněte na tlačítko **zobrazit Diagram tříd**.

> [!TIP]
> Pokud **zobrazení tříd** není otevřený, otevřete **zobrazení tříd** z **zobrazení** nabídky.

## <a name="to-display-the-contents-of-a-complete-project-in-a-class-diagram"></a>Chcete-li zobrazit obsah dokončený projekt v diagramu tříd

V **Průzkumníka řešení** nebo v zobrazení tříd, klikněte pravým tlačítkem na projekt a zvolte **zobrazení**, klikněte na tlačítko **zobrazit Diagram tříd**.

Vytvoření diagramu třídy vyplní automaticky.

## <a name="see-also"></a>Viz také:

- [Postupy: vytváření typů pomocí návrháře tříd](how-to-create-types.md)
- [Postupy: zobrazení existujících typů](how-to-view-existing-types.md)
- [Návrh a zobrazení tříd a typů](designing-and-viewing-classes-and-types.md)
- [Zobrazení typů a vztahů](viewing-types-and-relationships.md)
- [Práce s diagramy tříd](working-with-class-diagrams.md)
