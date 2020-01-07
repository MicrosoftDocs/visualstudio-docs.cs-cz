---
title: Implementovat abstraktní třídu
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 6fcfdc06a055df28159f9d1ddc440aaf113f3264
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75568903"
---
# <a name="implement-an-abstract-class-in-visual-studio"></a>Implementace abstraktní třídy v sadě Visual Studio

Tato generace kód platí pro:

- C#

- Visual Basic

**Co:** umožňuje okamžitě generovat kód potřebný k implementaci abstraktní třídu.

**Kdy:** chcete dědí z abstraktní třídy.

**Důvod, proč:** ručně může implementovat všechny abstraktní členy jeden po druhém, ale tato funkce automaticky vygeneruje všechny podpisy metod.

## <a name="how-to"></a>Postupy

1. Umístěte kurzor na řádek níž se nachází červená vlnovka, která určuje mají dědí z abstraktní třídy, ale neimplementovali všechny požadované členy.

   - C#:

       ![Zvýrazněný kód jazyka C#](media/abstract-highlight-cs.png)

   - Visual Basic:

       ![Zvýrazněný kód jazyka Visual Basic](media/abstract-highlight-vb.png)

2. Dále proveďte jednu z následujících akcí:

   - **Klávesnice**
      - Stisknutím klávesy **Ctrl**+**.** aktivační událost **rychlé akce a Refaktoringy** nabídky.
   - **Myši**
      - Klikněte pravým tlačítkem a vyberte **rychlé akce a Refaktoringy** nabídky.
      - Červená vlnovka ukazatel myši a klikněte ![žárovka chyby](media/error-bulb.png) ikona, která se zobrazí.
      - Klikněte na ![žárovka chyby](media/error-bulb.png) ikona, která se zobrazí u levého okraje, pokud textový kurzor na řádek s červená vlnovka.

   ![Implementace třídy ve verzi preview](media/abstract-preview-cs.png)

3. Vyberte **implementace abstraktní třídy** z rozevírací nabídky.

   > [!TIP]
   > - Použití **náhled změn** odkaz v dolní části okna náhledu [zobrazíte všechny změny](../../ide/preview-changes.md) , který bude proveden před zvolení požadované možnosti.
   > - Použití **dokumentu**, **projektu**, a **řešení** odkazy v dolní části okna ve verzi preview vytvořit správnou metodu podpisy v rámci více tříd, které dědí vlastnosti z abstraktní třídy.

   Abstraktní metoda podpisy jsou vytvořeny a jsou připravené k implementaci.

   - C#:

       ![Implementace třídy výsledekC#](media/abstract-result-cs.png)

   - Visual Basic:

       ![Implementace třídy výsledek VB](media/abstract-result-vb.png)

## <a name="see-also"></a>Viz také:

- [Generování kódu](../code-generation-in-visual-studio.md)
- [Náhled změn](../../ide/preview-changes.md)
