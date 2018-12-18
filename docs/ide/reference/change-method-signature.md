---
title: Refaktorujte podpis metody
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
f1_keywords:
- vs.csharp.refactoring.remove
- vs.csharp.refactoring.reorder
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 81f907ae1f7def1ce401990dc505f423aac5a4c1
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53062332"
---
# <a name="change-a-method-signature-refactoring"></a>Změna podpisu metody refaktoring

Tento refaktoring platí pro:

- C#

- Visual Basic

**Co:** umožňuje odebrat nebo změnit pořadí parametrů metod.

**Kdy:** chcete přesunout nebo odeberte parametr metody, která je aktuálně používána v různých umístěních.

**Důvod, proč:** může ručně odebrat a změnit pořadí parametrů a pak najít všechna volání metody a změnit je jeden po druhém, ale které by mohly vést k chybám.  Tento refaktoring nástroj automaticky provede úlohu.

## <a name="how-to"></a>Postupy

1. Zvýrazněte nebo umístěte kurzor text mezi název metody, která upravit, nebo jedno z jeho použití:

   - C#:

       ![Zvýrazněný kód jazyka C#](media/changesignature-highlight-cs.png)

   - VB:

       ![Zvýrazněný kód jazyka Visual Basic](media/changesignature-highlight-vb.png)

2. Dále proveďte jednu z následujících akcí:

   - **Klávesnice**
      - Stisknutím klávesy **Ctrl + R**, pak **Ctrl + V**.  (Všimněte si, že klávesová zkratka může být jiný platformě, na který profil vyberete.)
      - Stisknutím klávesy **Ctrl**+**.** aktivační událost **rychlé akce a Refaktoringy** nabídky a vybereme **změnit signaturu** z automaticky otevíraného okna okno náhledu.
   - **Myši**
      - Vyberte **Upravit > Refaktorovat > pro odebrání parametrů**.
      - Vyberte **Upravit > Refaktorovat > přeskupení parametrů**.
      - Klikněte pravým tlačítkem na kód, vyberte **rychlé akce a Refaktoringy** nabídky a vybereme **změnit signaturu** z automaticky otevíraného okna okno náhledu.

3. V **změnit podpis** dialogového okna, která se otevře, můžete změnit podpis metody můžete pomocí tlačítka na pravé straně:

   ![Změnit podpis dialogového okna](media/changesignature-dialog-cs.png)

   | Tlačítko | Popis
   | ------ | ---
   | **Směrem nahoru nebo dolů** | Přesunout vybraný parametr nahoru a dolů v seznamu
   | **odebrat** | Odebrat vybraný parametr ze seznamu
   | **Obnovení** | Obnovit vybrané, přeškrtnutý parametru do seznamu

   > [!TIP]
   > Použití **náhled změn odkazu** zaškrtávací políčko a [naleznete v tématu co se bude výsledek](../../ide/preview-changes.md) před potvrzením do něj.

4. Až skončíte, stiskněte **OK** tlačítko provést změny.

   - C#:

      ![Změnit podpis výsledek-C#](media/changesignature-result-cs.png)

   - Visual Basic:

      ![Změnit podpis výsledek - jazyka Visual Basic](media/changesignature-result-vb.png)

## <a name="see-also"></a>Viz také:

- [Refactoring](../refactoring-in-visual-studio.md)
- [Náhled změn](../../ide/preview-changes.md)