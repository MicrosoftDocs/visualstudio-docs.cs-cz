---
title: Rychlá akce při generování konstruktoru
ms.date: 01/26/2018
ms.topic: reference
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 41bb9a0e3921495629a10d6783432e8b4999a117
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661740"
---
# <a name="generate-a-constructor-in-visual-studio"></a>Generování konstruktoru v aplikaci Visual Studio

Tato generace kódu platí pro:

- C#

- Visual Basic

**Co:** Umožňuje okamžitě vygenerovat kód pro nový konstruktor třídy.

**Když:** Zavádíte nový konstruktor a chcete jej správně deklarovat, nebo upravíte existující konstruktor.

**Proč:** Je možné deklarovat konstruktor před jeho použitím, ale tato funkce je vygeneruje se správnými parametry automaticky. Navíc Změna existujícího konstruktoru vyžaduje aktualizaci všech callsites, pokud tuto funkci nepoužijete k automatické aktualizaci.

**Jak:** Existuje několik způsobů, jak vytvořit konstruktor:

- [Generovat konstruktor a vybrat členy](#pick)
- [Generovat konstruktor z vybraných polí](#selection)
- [Generovat konstruktor z nového použití](#usage)
- [Přidat parametr do existujícího konstruktoru](#addparameter)
- [Vytvoření a inicializace pole nebo vlastnosti z parametru konstruktoru](#create)

## <a id = "pick"></a>Generovat konstruktor a vybrat členy (C# jenom)

1. Umístěte kurzor do libovolného prázdného řádku ve třídě:

   ![Kurzor v prázdném řádku](media/constructor1-highlight-cs.png)

1. Dále proveďte jednu z následujících akcí:

   - **Kombinace**
      - Stiskněte klávesu **Ctrl** + **.** pro aktivaci nabídky **rychlé akce a refaktoringy** .
   - **Stisknut**
      - Klikněte pravým tlačítkem a vyberte nabídku **rychlé akce a refaktoring** .
      - Klikněte na ![screwdriver](media/screwdriver.png) ikona, která se zobrazí na levém okraji, pokud je textový kurzor již na prázdném řádku ve třídě.

   ![Generovat náhled konstruktoru](media/constructor1-preview-cs.png)

1. V rozevírací nabídce vyberte **vytvořit konstruktor** .

   Otevře se dialogové okno **Vybrat členy** .

1. Vyberte členy, které chcete zahrnout jako parametry konstruktoru. Můžete je seřadit pomocí šipek nahoru a dolů. Klikněte na **tlačítko OK**.

   ![Dialog Vybrat členy](media/constructor1-dialog-cs.png)

   > [!TIP]
   > Zaškrtnutím políčka **přidat hodnoty null** můžete automaticky generovat kontroly hodnot null pro parametry konstruktoru.

   Vytvoří se konstruktor se zadanými parametry.

   ![Generovat výsledek konstruktoru](media/constructor1-result-cs.png)

## <a id="selection"></a>Generovat konstruktor z vybraných polí (C# jenom)

1. Zvýrazněte členy, které chcete mít ve vytvořeném konstruktoru:

   ![Zvýraznit členy](media/constructor2-highlight-cs.png)

1. Dále proveďte jednu z následujících akcí:

   - **Kombinace**
      - Stiskněte klávesu **Ctrl** + **.** pro aktivaci nabídky **rychlé akce a refaktoringy** .
   - **Stisknut**
      - Klikněte pravým tlačítkem a vyberte nabídku **rychlé akce a refaktoring** .
      - Klikněte na ![screwdriver](media/screwdriver.png) ikona, která se zobrazí na levém okraji, pokud je textový kurzor již na řádku s výběrem.

      ![Generovat náhled konstruktoru](media/constructor2-preview-cs.png)

1. V rozevírací nabídce vyberte **Generovat konstruktor TypeName (...)** .

   Vytvoří se konstruktor s vybranými parametry.

   ![Generovat výsledek konstruktoru](media/constructor2-result-cs.png)

## <a id="usage"></a>Generovat konstruktor z nového použití (C# a Visual Basic)

1. Umístěte kurzor na řádek, kde je červená vlnovka. Červená vlnovka indikuje volání konstruktoru, který ještě neexistuje.

   - C#:

       ![Zvýrazněný kódC#](media/constructor-highlight-cs.png)

   - Visual Basic:

       ![Zvýrazněný kód VB](media/constructor-highlight-vb.png)

2. Dále proveďte jednu z následujících akcí:

   - **Kombinace**
      - Stiskněte klávesu **Ctrl** + **.** pro aktivaci nabídky **rychlé akce a refaktoringy** .
   - **Stisknut**
      - Klikněte pravým tlačítkem a vyberte nabídku **rychlé akce a refaktoring** .
      - Najeďte myší na červenou vlnovkou a klikněte na ![žárovka chyby](media/error-bulb.png) ikona, která se zobrazí.
      - Klikněte na ![žárovka chyby](media/error-bulb.png) ikona, která se zobrazí na levém okraji, pokud se na řádku již nachází textový kurzor s červenou vlnovkou

      ![Generovat náhled konstruktoru](media/constructor-preview-cs.png)

3. V rozevírací nabídce vyberte **vytvořit konstruktor v '*TypeName*'** .

   > [!TIP]
   > Pomocí odkazu **Náhled změn** v dolní části okna Preview [zobrazíte všechny změny](../../ide/preview-changes.md) , které budou provedeny před provedením výběru.

   Vytvoří se konstruktor s případnými parametry odvozenými z jeho využití.

   - C#:

       ![Generovat výsledek metodyC#](media/constructor-result-cs.png)

   - Visual Basic:

       ![Generovat výsledek metody VB](media/constructor-result-vb.png)

## <a id="addparameter"></a>Přidat parametr do existujícího konstruktoru (C# pouze)

1. Přidejte parametr do existujícího volání konstruktoru.

2. Umístěte kurzor na řádek, kde je červená vlnovka, což značí, že jste použili konstruktor, který ještě neexistuje.

    ![Vygenerovat zvýraznění konstruktoru](media/constructor4-highlight-cs.png)

3. Dále proveďte jednu z následujících akcí:

   - **Kombinace**
      - Stiskněte klávesu **Ctrl** + **.** pro aktivaci nabídky **rychlé akce a refaktoringy** .
   - **Stisknut**
      - Klikněte pravým tlačítkem a vyberte nabídku **rychlé akce a refaktoring** .
      - Najeďte myší na červenou vlnovkou a klikněte na ![žárovka chyby](media/error-bulb.png) ikona, která se zobrazí.
      - Klikněte na ![žárovka chyby](media/error-bulb.png) ikona, která se zobrazí na levém okraji, pokud se na řádku již nachází textový kurzor s červenou vlnovkou

      ![Generovat náhled konstruktoru](media/constructor4-preview-cs.png)

4. Z rozevírací nabídky vyberte **Přidat parametr do TypeName (...)** .

   Parametr se přidá do konstruktoru s jeho typem odvozeným z jeho využití.

   ![Generovat výsledek konstruktoru](media/constructor4-result-cs.png)

Můžete také přidat parametr do existující metody. Další informace naleznete v tématu [Přidání parametru do metody](add-parameter.md).

## <a id="create"></a>Vytvoření a inicializace pole nebo vlastnosti z parametru konstruktoru (C# pouze)

1. Najděte existující konstruktor a přidejte parametr:

   ![Vygenerovat zvýraznění konstruktoru](media/constructor5-highlight-cs.png)

1. Umístěte kurzor do nově přidaného parametru.

1. Dále proveďte jednu z následujících akcí:

   - **Kombinace**
      - Stiskněte klávesu **Ctrl** + **.** pro aktivaci nabídky **rychlé akce a refaktoringy** .
   - **Stisknut**
      - Klikněte pravým tlačítkem a vyberte nabídku **rychlé akce a refaktoring** .
      - Klikněte na ![screwdriver](media/screwdriver.png) ikona, která se zobrazí na levém okraji, pokud se na řádku již nachází textový kurzor s přidaným parametrem.

   ![Generovat náhled konstruktoru](media/constructor5-preview-cs.png)

1. V rozevírací nabídce vyberte možnost **vytvořit a inicializovat vlastnost** nebo **vytvořit a inicializovat pole** .

   Pole nebo vlastnost jsou deklarovány a automaticky pojmenovány tak, aby odpovídaly vašim typům. Také je přidána řádka kódu pro inicializaci pole nebo vlastnosti v těle konstruktoru.

   ![Generovat výsledek konstruktoru](media/constructor5-result-cs.png)

## <a name="see-also"></a>Viz také:

- [Generování kódu](../code-generation-in-visual-studio.md)
- [Zobrazit náhled změn](../../ide/preview-changes.md)