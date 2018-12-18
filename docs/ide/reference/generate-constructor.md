---
title: Generovat konstruktor rychlá akce
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: c6b267bee0c78de19ffa0d443f515375eeae949a
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2018
ms.locfileid: "51295823"
---
# <a name="generate-a-constructor-in-visual-studio"></a>Generovat konstruktor v sadě Visual Studio

Tato generace kód platí pro:

- C#

- Visual Basic

**Co:** umožňuje okamžitě generování kódu pro nový konstruktor třídy.

**Kdy:** zavést nový konstruktor a chcete správně deklarujte ho automaticky, nebo upravte existující konstruktoru.

**Důvod, proč:** můžete deklarovat konstruktor před jeho použití, ale tato funkce bude generovat, s odpovídající parametry automaticky. Kromě toho úprava existující konstruktoru vyžaduje aktualizaci všech callsites, pokud pomocí této funkce lze automaticky aktualizovat.

**Jak:** generovat konstruktor několika způsoby:

   - [Generovat konstruktor a vyberte členy, kteří](#pick)
   - [Generovat konstruktor z vybraných polí](#selection)
   - [Generovat konstruktor nové využití](#usage)
   - [Přidat parametr do konstruktoru existující](#addparameter)
   - [Vytváření a inicializace pole nebo vlastnost z parametru konstruktoru](#create)

## <a id = "pick"></a> Generovat konstruktor a vyberte členy, kteří (C# jenom)

1. Umístěte ukazatel myši v jakékoli prázdný řádek ve třídě:

   ![Kurzor v prázdném řádku](media/constructor1-highlight-cs.png)

1. Dále proveďte jednu z následujících akcí:

   - **Klávesnice**
      - Stisknutím klávesy **Ctrl**+**.** aktivační událost **rychlé akce a Refaktoringy** nabídky.
   - **Myši**
      - Klikněte pravým tlačítkem a vyberte **rychlé akce a Refaktoringy** nabídky.
      - Klikněte na ![Žárovka](media/bulb-cs.png) ikona, která se zobrazí u levého okraje, pokud textový kurzor na prázdný řádek ve třídě.

   ![Generovat konstruktor ve verzi preview](media/constructor1-preview-cs.png)

1. Vyberte **generovat konstruktor** z rozevírací nabídky.

   **Vyberte členy, kteří** zobrazí se dialogové okno.

1. Vyberte členy, které chcete zahrnout jako parametry konstruktoru. Můžete uspořádat pomocí nahoru a dolů šipkami. Zvolte **OK**.

   ![Dialogové okno Výběr členů](media/constructor1-dialog-cs.png)

   > [!TIP]
   > Můžete zkontrolovat **přidat kontroly hodnot null** zaškrtávací políčko a automaticky generovat kontroly hodnoty null pro parametry konstruktoru.

   Konstruktor je vytvořen se zadanými parametry.

   ![Generovat konstruktor výsledek](media/constructor1-result-cs.png)

## <a id="selection"></a> Generovat konstruktor z vybraných polí (C# jenom)

1. Vyberte členy, které chcete mít v generovaný konstruktor:

   ![Zvýrazněte členy](media/constructor2-highlight-cs.png)

1. Dále proveďte jednu z následujících akcí:

   - **Klávesnice**
      - Stisknutím klávesy **Ctrl**+**.** aktivační událost **rychlé akce a Refaktoringy** nabídky.
   - **Myši**
      - Klikněte pravým tlačítkem a vyberte **rychlé akce a Refaktoringy** nabídky.
      - Klikněte na ![Žárovka](media/bulb-cs.png) ikona, která se zobrazí u levého okraje, pokud textový kurzor na řádek s výběrem.

      ![Generovat konstruktor ve verzi preview](media/constructor2-preview-cs.png)

1. Vyberte **generovat konstruktor 'TypeName(...).**  z rozevírací nabídky.

   Konstruktor je vytvořen s vybraných parametrů.

   ![Generovat konstruktor výsledek](media/constructor2-result-cs.png)

## <a id="usage"></a> Generovat konstruktor nové využití (C# a Visual Basic)

1. Umístěte kurzor na řádek níž se nachází červená vlnovka. Červená vlnovka označuje volání konstruktoru, který ještě neexistuje.

   - C#:

       ![Zvýrazněný kód jazyka C#](media/constructor-highlight-cs.png)

   - Visual Basic:

       ![Zvýrazněný kód jazyka Visual Basic](media/constructor-highlight-vb.png)

2. Dále proveďte jednu z následujících akcí:

   - **Klávesnice**
      - Stisknutím klávesy **Ctrl**+**.** aktivační událost **rychlé akce a Refaktoringy** nabídky.
   - **Myši**
      - Klikněte pravým tlačítkem a vyberte **rychlé akce a Refaktoringy** nabídky.
      - Červená vlnovka ukazatel myši a klikněte ![Žárovka](media/bulb-cs.png) ikona, která se zobrazí.
      - Klikněte na ![Žárovka](media/bulb-cs.png) ikona, která se zobrazí u levého okraje, pokud textový kurzor na řádek s červená vlnovka.

      ![Generovat konstruktor ve verzi preview](media/constructor-preview-cs.png)

3. Vyberte **generovat konstruktor v "*TypeName*"** z rozevírací nabídky.

   > [!TIP]
   > Použití **náhled změn** odkaz v dolní části okna náhledu [zobrazíte všechny změny](../../ide/preview-changes.md) , který bude proveden před zvolení požadované možnosti.

   Konstruktor je vytvořen s parametry odvodit z jeho využití.

   - C#:

       ![Generovat výsledek metody jazyka C#](media/constructor-result-cs.png)

   - Visual Basic:

       ![Generovat výsledek metody VB](media/constructor-result-vb.png)

## <a id="addparameter"></a> Přidání parametru do existující konstruktoru (C# jenom)

1. Přidání parametru k existující volání konstruktoru.

2. Umístěte kurzor na řádek níž se nachází červená vlnovka, která jste použili konstruktor, který ještě neexistuje.

    ![Generovat konstruktor zvýraznění](media/constructor4-highlight-cs.png)

3. Dále proveďte jednu z následujících akcí:

   - **Klávesnice**
      - Stisknutím klávesy **Ctrl**+**.** aktivační událost **rychlé akce a Refaktoringy** nabídky.
   - **Myši**
      - Klikněte pravým tlačítkem a vyberte **rychlé akce a Refaktoringy** nabídky.
      - Červená vlnovka ukazatel myši a klikněte ![Žárovka](media/bulb-cs.png) ikona, která se zobrazí.
      - Klikněte na ![Žárovka](media/bulb-cs.png) ikona, která se zobrazí u levého okraje, pokud textový kurzor na řádek s červená vlnovka.

      ![Generovat konstruktor ve verzi preview](media/constructor4-preview-cs.png)

4. Vyberte **přidat parametr "TypeName(...).**  z rozevírací nabídky.

   Parametr se přidá do konstruktoru, s jeho typ odvozený z jeho využití.

   ![Generovat konstruktor výsledek](media/constructor4-result-cs.png)

Můžete také přidat parametr do existující metodu. Další informace najdete v tématu [přidání parametru k metodě](add-parameter.md).

## <a id="create"></a> Vytváření a inicializace pole nebo vlastnost z parametru konstruktoru (C# jenom)

1. Najděte existující konstruktor a přidejte parametr:

   ![Generovat konstruktor zvýraznění](media/constructor5-highlight-cs.png)

1. Umístěte ukazatel myši v nově přidaném parametru.

1. Dále proveďte jednu z následujících akcí:

   - **Klávesnice**
      - Stisknutím klávesy **Ctrl**+**.** aktivační událost **rychlé akce a Refaktoringy** nabídky.
   - **Myši**
      - Klikněte pravým tlačítkem a vyberte **rychlé akce a Refaktoringy** nabídky.
      - Klikněte na ![Žárovka](media/bulb-cs.png) ikona, která se zobrazí u levého okraje, pokud textový kurzor na řádek s přidání parametru.

   ![Generovat konstruktor ve verzi preview](media/constructor5-preview-cs.png)

1. Vyberte **vytvořit a inicializovat vlastnost** nebo **vytvořit a inicializovat pole** z rozevírací nabídky.

   Pole nebo vlastnost je deklarovaný a automaticky pojmenovali, aby odpovídala typů. Řádek kódu je také přidán k inicializaci pole nebo vlastnosti v těle konstruktoru.

   ![Generovat konstruktor výsledek](media/constructor5-result-cs.png)

## <a name="see-also"></a>Viz také:

- [Generování kódu](../code-generation-in-visual-studio.md)
- [Náhled změn](../../ide/preview-changes.md)