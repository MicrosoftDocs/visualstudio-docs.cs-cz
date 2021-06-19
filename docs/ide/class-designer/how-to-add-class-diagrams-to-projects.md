---
title: Přidání diagramů tříd do projektů (Návrhář tříd)
description: Naučte se navrhovat, upravovat a refaktorovat třídy a další typy, přidávat diagram tříd do projektu C#, Visual Basic nebo C++.
ms.custom: SEO-VS-2020
ms.date: 05/08/2018
ms.topic: how-to
helpviewer_keywords:
- class diagrams, creating
- Class Designer [Visual Studio], opening
ms.assetid: 0eac1b54-2711-4e4b-9654-a0c429c08c8f
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0af2717efec7cab8594f193c06e8813bd556b01f
ms.sourcegitcommit: c3713f284c4fe10b10996d5eb67077ddd8641424
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112375783"
---
# <a name="how-to-add-class-diagrams-to-projects"></a>Postupy: Přidání diagramů tříd do projektů

Pokud chcete navrhovat, upravovat a refaktorovat třídy a další typy, přidejte diagram tříd do projektu C#, Visual Basic nebo C++. Pokud chcete vizualizovat různé části kódu v projektu, přidejte do projektu více diagramů tříd.

Diagramy tříd nemůžete vytvářet z projektů, které sdílejí kód napříč více aplikacemi. Chcete-li vytvořit diagramy tříd UML, naleznete v [části Create UML modeling projects and diagrams](https://devblogs.microsoft.com/devops/uml-designers-have-been-removed-layer-designer-now-supports-live-architectural-analysis/).

## <a name="install-the-class-designer-component"></a>Instalace komponenty Návrhář tříd

Pokud jste ještě nenainstalujete **komponentu Návrhář tříd,** nainstalujte ji podle těchto kroků.

1. Otevřete **Instalační program pro Visual Studio** na webu Windows nabídka Start nebo výběrem možnosti Nástroje Získat nástroje a funkce z řádku nabídek v  >   Visual Studio.

   **Instalační program pro Visual Studio** se okno.

1. Vyberte kartu **Jednotlivé komponenty** a pak se posuňte dolů do **kategorie Nástroje** kódu.

1. Vyberte **Návrhář tříd** a pak vyberte **Upravit.**

   ![Návrhář tříd komponenty v Instalační program pro Visual Studio](media/class-designer-component.png)

   Komponenta **Návrhář tříd** se spustí.

## <a name="add-a-blank-class-diagram-to-a-project"></a>Přidání prázdného diagramu tříd do projektu

1. V Průzkumník řešení klikněte pravým tlačítkem na uzel projektu **a** pak zvolte **Přidat**  >  **novou položku.** Nebo stiskněte **Ctrl** + **Shift** + **A.**

   Otevře **se dialogové okno Přidat** novou položku.

2. Rozbalte **položku Běžné** položky Obecné a pak ze seznamu šablon  >  vyberte Diagram tříd.  Pokud Visual C++ projekty, vyhledejte  šablonu Diagram tříd v **kategorii Nástroj.**

   > [!NOTE]
   > Pokud šablonu diagramu  tříd nevidíte, [](#install-the-class-designer-component) postupujte podle pokynů k instalaci komponenty **Návrhář tříd** pro Visual Studio.

   Diagram tříd se otevře v Návrhář tříd a zobrazí se jako soubor s příponou *.cd* v **Průzkumník řešení**. Tvary a čáry můžete do diagramu přetáhnout z panelu **nástrojů**.

Chcete-li přidat více diagramů tříd, opakujte kroky v tomto postupu.

## <a name="add-a-class-diagram-based-on-existing-types"></a>Přidání diagramu tříd na základě existujících typů

V **Průzkumník řešení** místní nabídku souboru třídy (klikněte na něj pravým tlačítkem) a zvolte **Zobrazit diagram tříd.**

-nebo-

V **Zobrazení tříd** otevřete místní nabídku oboru názvů nebo typu a pak zvolte **Zobrazit diagram tříd.**

> [!TIP]
> Pokud **Zobrazení tříd** otevřený, otevřete **Zobrazení tříd** v **nabídce Zobrazení.**

## <a name="to-display-the-contents-of-a-complete-project-in-a-class-diagram"></a>Zobrazení obsahu kompletního projektu v diagramu tříd

V **Průzkumník řešení** nebo Zobrazení tříd klikněte pravým tlačítkem na projekt, zvolte **Zobrazení** a pak zvolte Zobrazit **diagram tříd.**

Vytvoří se diagram automaticky naplněné třídy.

> [!NOTE]
> Návrhář tříd není k dispozici v projektech .NET Core.

## <a name="see-also"></a>Viz také

- [Postupy: Vytváření typů pomocí Návrhář tříd](how-to-create-types.md)
- [Postupy: Zobrazení existujících typů](how-to-view-existing-types.md)
- [Návrh a zobrazení tříd a typů](designing-and-viewing-classes-and-types.md)
