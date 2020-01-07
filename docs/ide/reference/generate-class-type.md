---
title: Generovat třídy nebo typu
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
f1_keywords:
- vsl.GenerateFromUsage
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 94786ef10e427a0deb4f80471305509124f1638b
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595628"
---
# <a name="generate-a-class-or-type-in-visual-studio"></a>Generovat třídy nebo typu v sadě Visual Studio

Tato generace kód platí pro:

- C#

- Visual Basic

**Co:** umožňuje okamžitě generování kódu pro třídu nebo typu.

**Kdy:** představují nové třídy nebo typu a chcete správně, automaticky deklarovat.

**Důvod, proč:** můžete deklarovat třídy nebo typu než ho začnete využívat, ale tato funkce bude generovat třídy nebo typu automaticky.

## <a name="how-to"></a>Postupy

1. Umístěte kurzor na řádek níž se nachází červená vlnovka. Červená vlnovka Určuje třídu, která ještě neexistuje.

   - C#:

       ![Zvýrazněný kód jazyka C#](media/class-highlight-cs.png)

   - Visual Basic:

       ![Zvýrazněný kód jazyka Visual Basic](media/class-highlight-vb.png)

2. Dále proveďte jednu z následujících akcí:

   - **Klávesnice**
      - Stisknutím klávesy **Ctrl**+ **.** aktivační událost **rychlé akce a Refaktoringy** nabídky.
   - **Myši**
      - Klikněte pravým tlačítkem a vyberte **rychlé akce a Refaktoringy** nabídky.
      - Červená vlnovka ukazatel myši a klikněte ![žárovka chyby](media/error-bulb.png) ikona, která se zobrazí.
      - Klikněte na ![žárovka chyby](media/error-bulb.png) ikona, která se zobrazí u levého okraje, pokud textový kurzor na řádek s červená vlnovka.

      ![Generovat třídy ve verzi preview](media/class-preview-cs.png)

3. Vyberte jednu z možností z rozevírací nabídky:

   - Generovat třídy*TypeName*"v novém souboru&mdash;vytvoří třídu s názvem *TypeName* do souboru s názvem *TypeName*.cs nebo .vb
   - Generovat třídy*TypeName*"&mdash;vytvoří třídu s názvem *TypeName* v aktuálním souboru.
   - Generovat vnořené třídy*TypeName*"&mdash;vytvoří třídu s názvem *TypeName* vnořit do aktuální třídy.
   - Generovat nový typ... &mdash;Vytvoří nové třídy nebo struktury se všemi vlastnosti, které zadáte.

   > [!TIP]
   > Použití **náhled změn** odkaz v dolní části okna náhledu [zobrazíte všechny změny](../../ide/preview-changes.md) , který bude proveden před zvolení požadované možnosti.

4. Pokud jste vybrali **generovat nový typ** položky, **generovat typ** zobrazí se dialogové okno. Nakonfigurujte usnadnění přístupu, typ a umístění nového typu.

   ![Generovat typ](media/class-newtype-cs.png)

   Výběr | Popis
   --- | ---
   Přístup | Nastavit typ, který má být *výchozí*, *interní* nebo *veřejné* přístup.
   Druh | To je možné nastavit jako *třídy* nebo *struktura*.
   Name | To se nedá změnit a bude název, který jste už zadali.
   Projekt | Pokud existuje více projektů v řešení, můžete místo, kam chcete třídě/struktuře TTL.
   Název souboru | Můžete vytvořit nový soubor nebo můžete přidat typ do existujícího souboru.

Vytvoření třídy nebo struktury. Pro C#, se vytvoří také konstruktor.

- C#

   ![Generovat třídy výsledekC#](media/class-result-cs.png)

- Visual Basic

   ![Generovat třídy výsledek VB](media/class-result-vb.png)

## <a name="see-also"></a>Viz také:

- [Generování kódu](../code-generation-in-visual-studio.md)
- [Náhled změn](../../ide/preview-changes.md)
