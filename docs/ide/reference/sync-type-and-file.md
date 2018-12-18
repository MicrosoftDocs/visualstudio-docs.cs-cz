---
title: Přejmenujte název souboru tak, aby odpovídaly typu
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: bfc1a88091fa30bceea15a3f8e1b78df5cc7a87c
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53054784"
---
# <a name="sync-a-type-to-a-filename-or-a-filename-to-a-type-refactoring"></a>Synchronizace typu název souboru nebo název souboru pro typ refaktoring

Tento refaktoring platí pro:

- C#

- Visual Basic

**Co:** umožňuje přejmenujte typ tak, aby odpovídaly názvu souboru, nebo název souboru tak, aby odpovídaly typ obsahuje.

**Kdy:** přejmenování souboru nebo typu a ještě neprovedli aktualizaci na odpovídající soubor nebo typ k porovnání.

**Důvod, proč:** umístění typu v souboru s jiným názvem, nebo naopak je obtížné najít, co hledáte. Přejmenováním tento typ nebo název souboru bude kód čitelnější a přehlednější a díky tomu.

## <a name="how-to"></a>Postupy

1. Zvýrazněte nebo umístěte kurzor text mezi název typu pro synchronizaci:

   - C#:

       ![Zvýrazněný kód:C#](media/synctype-highlight-cs.png)

   - Visual Basic:

       ![Zvýrazněný kód – Visual Basic](media/synctype-highlight-vb.png)

2. Dále proveďte jednu z následujících akcí:

   - **Klávesnice**
      - Stisknutím klávesy **Ctrl**+**.** aktivační událost **rychlé akce a Refaktoringy** nabídky a vybereme **přejmenování souboru *TypeName*.cs** z místní nabídka okna ve verzi Preview, kde *TypeName* je název vybraného typu.
      - Stisknutím klávesy **Ctrl**+**.** aktivační událost **rychlé akce a Refaktoringy** nabídky a vybereme **Přejmenovat typ na _Filename_**  z místní nabídka okna ve verzi Preview, kde *Filename* je název aktuálního souboru.
   - **Myši**
      - Klikněte pravým tlačítkem na kód, vyberte **rychlé akce a Refaktoringy** nabídky a vybereme **přejmenování souboru *TypeName*.cs** z místní nabídka okna ve verzi Preview, ve kterém *TypeName* je název vybraného typu.
      - Klikněte pravým tlačítkem na kód, vyberte **rychlé akce a Refaktoringy** nabídky a vybereme **Přejmenovat typ na _Filename_**  z místní nabídka okna ve verzi Preview, ve kterém  *Název souboru* je název aktuálního souboru.

   Přejmenování nebo typu souboru.

   - C#: V příkladu níže, soubor **MyClass.cs** se přejmenoval na **MyNewClass.cs** tak, aby odpovídaly názvu typu.

       ![Vložené výsledekC#](media/synctype-result-cs.png)

   - Jazyka Visual Basic: V příkladu níže, soubor **Employee.vb** se přejmenoval na **Person.vb** tak, aby odpovídaly názvu typu.

       ![Vložené výsledek jazyka Visual Basic](media/synctype-result-vb.png)

> ! [POZNÁMKA] Tento refaktoring ještě není k dispozici pro projekty .NET Standard a .NET Core.

## <a name="see-also"></a>Viz také:

- [Refactoring](../refactoring-in-visual-studio.md)
