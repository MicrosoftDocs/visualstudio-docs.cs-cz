---
title: Generovat rychlou akci konstruktoru
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 3c8259841af4511bd782bca1be222353634638f5
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "79301809"
---
# <a name="generate-a-constructor-in-visual-studio"></a>Generování konstruktoru v sadě Visual Studio

Toto generování kódu se vztahuje na:

- C#

- Visual Basic

**Co:** Umožňuje okamžitě vygenerovat kód pro nový konstruktor ve třídě.

**Kdy:** Zavedete nový konstruktor a chcete správně deklarovat automaticky nebo upravit existující konstruktor.

**Proč:** Před použitím můžete deklarovat konstruktor, ale tato funkce jej automaticky vygeneruje se správnými parametry. Kromě toho úprava existujícíkonstruktor vyžaduje aktualizaci všech callsites, pokud použít tuto funkci k jejich automatické aktualizaci.

**Jak:** Existuje několik způsobů, jak generovat konstruktor:

- [Generovat členy konstruktoru a vyskladnění](#pick)
- [Generovat konstruktor z vybraných polí](#selection)
- [Generovat konstruktor z nového použití](#usage)
- [Přidat parametr do existujícího konstruktoru](#addparameter)
- [Vytvoření a inicializaci pole/vlastnosti z parametru konstruktoru](#create)

## <a name="generate-constructor-and-pick-members-c-only"></a><a id = "pick"></a>Generovat členy konstruktoru a vyskladnění (pouze c#

1. Umístěte kurzor na libovolný prázdný řádek ve třídě:

   ![Kurzor v prázdném řádku](media/constructor1-highlight-cs.png)

1. Dále proveďte jeden z následujících akcí:

   - **Klávesnice**
      - Stiskněte **klávesu Ctrl**+**.** spouštět nabídku **Rychlé akce a Refaktorings.**
   - **Myš**
      - Klikněte pravým tlačítkem myši a vyberte nabídku **Rychlé akce a Refaktoringy.**
      - Klikněte na ![Šroubovák](media/screwdriver.png) ikona, která se zobrazí na levém okraji, pokud je textový kurzor již na prázdném řádku ve třídě.

   ![Generovat náhled konstruktoru](media/constructor1-preview-cs.png)

1. V rozevírací nabídce vyberte **Generovat konstruktor.**

   Otevře se dialogové okno **Vybrat členy.**

1. Vyberte členy, které chcete zahrnout jako parametry konstruktoru. Můžete si je objednat pomocí šipek nahoru a dolů. Vyberte **OK**.

   ![Dialogové okno Vybrat členy](media/constructor1-dialog-cs.png)

   > [!TIP]
   > Můžete zaškrtnout políčko **Přidat nulové kontroly** a automaticky generovat nulové kontroly parametrů konstruktoru.

   Konstruktor je vytvořen se zadanými parametry.

   ![Generovat výsledek konstruktoru](media/constructor1-result-cs.png)

## <a name="generate-constructor-from-selected-fields-c-only"></a><a id="selection"></a>Generovat konstruktor z vybraných polí (pouze C# )

1. Zvýrazněte členy, které chcete mít ve vašem generovaném konstruktoru:

   ![Zvýraznit členy](media/constructor2-highlight-cs.png)

1. Dále proveďte jeden z následujících akcí:

   - **Klávesnice**
      - Stiskněte **klávesu Ctrl**+**.** spouštět nabídku **Rychlé akce a Refaktorings.**
   - **Myš**
      - Klikněte pravým tlačítkem myši a vyberte nabídku **Rychlé akce a Refaktoringy.**
      - Klikněte na ![Šroubovák](media/screwdriver.png) se zobrazí na levém okraji, pokud je textový kurzor již na řádku s výběrem.

      ![Generovat náhled konstruktoru](media/constructor2-preview-cs.png)

1. V rozevírací nabídce vyberte **Generovat konstruktor TypeName(...).**

   Konstruktor je vytvořen s vybranými parametry.

   ![Generovat výsledek konstruktoru](media/constructor2-result-cs.png)

## <a name="generate-constructor-from-new-usage-c-and-visual-basic"></a><a id="usage"></a>Generovat konstruktor z nového použití (C# a Visual Basic)

1. Umístěte kurzor na čáru, kde je červená vlnovka. Červená vlnovka označuje volání konstruktoru, který ještě neexistuje.

   - C#:

       ![Zvýrazněný kód C #](media/constructor-highlight-cs.png)

   - Visual Basic:

       ![Zvýrazněný kód VB](media/constructor-highlight-vb.png)

2. Dále proveďte jeden z následujících akcí:

   - **Klávesnice**
      - Stiskněte **klávesu Ctrl**+**.** spouštět nabídku **Rychlé akce a Refaktorings.**
   - **Myš**
      - Klikněte pravým tlačítkem myši a vyberte nabídku **Rychlé akce a Refaktoringy.**
      - Najeďte přes červenou vlnovku a klikněte na ![chybová žárovka](media/error-bulb.png) ikona, která se zobrazí.
      - Klikněte na ![chybová žárovka](media/error-bulb.png) se zobrazí na levém okraji, pokud je textový kurzor již na řádku s červenou vlnovkou.

      ![Generovat náhled konstruktoru](media/constructor-preview-cs.png)

3. V rozevírací nabídce vyberte **Generovat konstruktor v '*TypeName*'.**

   > [!TIP]
   > Pomocí odkazu **Náhled změn** v dolní části okna náhledu [zobrazíte všechny změny,](../../ide/preview-changes.md) které budou provedeny před provedením výběru.

   Konstruktor je vytvořen, s všechny parametry odvozené z jeho použití.

   - C#:

       ![Generovat výsledek metody C #](media/constructor-result-cs.png)

   - Visual Basic:

       ![Generovat výsledek metody VB](media/constructor-result-vb.png)

## <a name="add-parameter-to-existing-constructor-c-only"></a><a id="addparameter"></a>Přidat parametr do existujícího konstruktoru (pouze C#

1. Přidejte parametr do volání existujícího konstruktoru.

2. Umístěte kurzor na čáru, kde je červená vlnovka označující, že jste použili konstruktor, který ještě neexistuje.

    ![Generovat zvýraznění konstruktoru](media/constructor4-highlight-cs.png)

3. Dále proveďte jeden z následujících akcí:

   - **Klávesnice**
      - Stiskněte **klávesu Ctrl**+**.** spouštět nabídku **Rychlé akce a Refaktorings.**
   - **Myš**
      - Klikněte pravým tlačítkem myši a vyberte nabídku **Rychlé akce a Refaktoringy.**
      - Najeďte přes červenou vlnovku a klikněte na ![chybová žárovka](media/error-bulb.png) ikona, která se zobrazí.
      - Klikněte na ![chybová žárovka](media/error-bulb.png) se zobrazí na levém okraji, pokud je textový kurzor již na řádku s červenou vlnovkou.

      ![Generovat náhled konstruktoru](media/constructor4-preview-cs.png)

4. V rozevírací nabídce vyberte Přidat **parametr do typename(...).**

   Parametr je přidán do konstruktoru, s jeho typem odvodit z jeho použití.

   ![Generovat výsledek konstruktoru](media/constructor4-result-cs.png)

Můžete také přidat parametr do existující metody. Další informace naleznete v tématu [Add parameter to a method](add-parameter.md).

## <a name="create-and-initialize-a-field-or-property-from-a-constructor-parameter-c-only"></a><a id="create"></a>Vytvoření a inicializaci pole nebo vlastnosti z parametru konstruktoru (pouze C#

1. Najděte existující konstruktor a přidejte parametr:

   ![Generovat zvýraznění konstruktoru](media/constructor5-highlight-cs.png)

1. Umístěte kurzor do nově přidaného parametru.

1. Dále proveďte jeden z následujících akcí:

   - **Klávesnice**
      - Stiskněte **klávesu Ctrl**+**.** spouštět nabídku **Rychlé akce a Refaktorings.**
   - **Myš**
      - Klikněte pravým tlačítkem myši a vyberte nabídku **Rychlé akce a Refaktoringy.**
      - Klikněte na ![Šroubovák](media/screwdriver.png) se zobrazí na levém okraji, pokud je textový kurzor již na řádku s přidaným parametrem.

   ![Generovat náhled konstruktoru](media/constructor5-preview-cs.png)

1. V rozevírací nabídce vyberte **Vytvořit a inicializovat vlastnost** nebo Vytvořit a **inicializovat pole.**

   Pole nebo vlastnost je deklarována a automaticky pojmenována tak, aby odpovídala vašim typům. Řádek kódu je také přidán k inicializaci pole nebo vlastnosti v těle konstruktoru.

   ![Generovat výsledek konstruktoru](media/constructor5-result-cs.png)

## <a name="see-also"></a>Viz také

- [Generování kódu](../code-generation-in-visual-studio.md)
- [Náhled změn](../../ide/preview-changes.md)
