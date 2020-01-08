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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75588834"
---
# <a name="how-to-add-class-diagrams-to-projects"></a>Postupy: Přidání diagramů tříd do projektů

Chcete-li navrhovat, upravovat a Refaktorovat třídy a jiné typy, přidejte diagram tříd do C#Visual Basic nebo C++ projektu. Chcete-li vizualizovat různé části kódu v projektu, přidejte do projektu více diagramů tříd.

Diagramy tříd nemůžete vytvářet z projektů, které sdílejí kód napříč více aplikacemi. Chcete-li vytvořit diagramy tříd UML, přečtěte si téma [vytváření projektů a diagramů modelování UML](../../modeling/what-s-new-for-design-in-visual-studio.md).

## <a name="install-the-class-designer-component"></a>Instalace součásti Návrhář tříd

Pokud jste nenainstalovali součást **Návrhář tříd** , nainstalujte ji podle těchto kroků.

1. Otevřete **instalační program pro Visual Studio** z nabídky Start systému Windows nebo výběrem **nástrojů** > **získat nástroje a funkce** z panelu nabídek v aplikaci Visual Studio.

   **Instalační program pro Visual Studio** se otevře.

1. Vyberte kartu **jednotlivé komponenty** a potom se posuňte dolů ke kategorii **nástroje kódu** .

1. Vyberte **Návrhář tříd** a pak vyberte **Upravit**.

   ![Součást Návrhář tříd v Instalační program pro Visual Studio](media/class-designer-component.png)

   Spustí se instalace součásti **Návrhář tříd** .

## <a name="add-a-blank-class-diagram-to-a-project"></a>Přidání prázdného diagramu tříd do projektu

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na uzel projektu a vyberte možnost **Přidat** > **novou položku**. Případně stiskněte **kombinaci kláves Ctrl**+**SHIFT**+**A**.

   Otevře se dialogové okno **Přidat novou položku** .

2. Rozbalte položku **běžné položky** > **Obecné**a potom v seznamu šablon vyberte možnost **Diagram tříd** . V případě C++ vizuálních projektů vyhledejte šablonu **diagramu tříd** v kategorii **nástrojů** .

   > [!NOTE]
   > Pokud nevidíte šablonu **diagramu tříd** , [postupujte podle kroků](#install-the-class-designer-component) pro instalaci součásti **Návrhář tříd** pro Visual Studio.

   Diagram tříd se otevře v Návrhář tříd a zobrazí se jako soubor s příponou *. CD* v **Průzkumník řešení**. Obrazce a čáry lze přetáhnout do diagramu ze **sady nástrojů**.

Chcete-li přidat více diagramů tříd, opakujte kroky v tomto postupu.

## <a name="add-a-class-diagram-based-on-existing-types"></a>Přidání diagramu tříd založeného na existujících typech

V **Průzkumník řešení**otevřete místní nabídku souboru třídy (klikněte pravým tlačítkem myši) a pak zvolte **Zobrazit diagram tříd**.

-nebo-

V **zobrazení tříd**otevřete místní nabídku obor názvů nebo typ a zvolte možnost **Zobrazit diagram tříd**.

> [!TIP]
> Pokud **zobrazení tříd** není otevřený, otevřete **zobrazení tříd** v nabídce **zobrazení** .

## <a name="to-display-the-contents-of-a-complete-project-in-a-class-diagram"></a>Zobrazení obsahu kompletního projektu v diagramu tříd

V **Průzkumník řešení** nebo zobrazení tříd klikněte pravým tlačítkem myši na projekt a zvolte možnost **Zobrazit**a pak zvolte možnost **Zobrazit diagram tříd**.

Vytvoří se automaticky vyplněný diagram tříd.

> [!NOTE]
> Návrhář tříd není v projektech .NET Core k dispozici.

## <a name="see-also"></a>Viz také:

- [Postupy: vytváření typů pomocí Návrhář tříd](how-to-create-types.md)
- [Postupy: zobrazení existujících typů](how-to-view-existing-types.md)
- [Návrh a zobrazení tříd a typů](designing-and-viewing-classes-and-types.md)
