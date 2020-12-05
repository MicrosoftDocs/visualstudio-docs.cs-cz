---
title: Generovat třídu nebo typ
description: Naučte se, jak pomocí nabídky rychlé akce a refaktoring hned vygenerovat kód pro třídu nebo typ.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: fe38cacf9f33acfac6b1634b6be6a8a3e45de820
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2020
ms.locfileid: "96617536"
---
# <a name="generate-a-class-or-type-in-visual-studio"></a>Generování třídy nebo typu v aplikaci Visual Studio

Tato generace kódu platí pro:

- C#

- Visual Basic

**Co:** Umožňuje ihned vygenerovat kód pro třídu nebo typ.

**Když:** Zavádíte novou třídu nebo typ a chcete ji správně deklarovat automaticky.

**Proč:** Můžete deklarovat třídu nebo typ před použitím, ale tato funkce vygeneruje třídu nebo typ automaticky.

## <a name="how-to"></a>Postupy

1. Umístěte kurzor na řádek, kde je červená vlnovka. Červená vlnovka indikuje třídu, která ještě neexistuje.

   - C#:

       ![Zvýrazněný kód C #](media/class-highlight-cs.png)

   - Visual Basic:

       ![Zvýrazněný kód VB](media/class-highlight-vb.png)

2. Dále proveďte jednu z následujících akcí:

   - **Klávesnice**
      - Stiskněte klávesu **CTRL** + **.** pro aktivaci nabídky **rychlé akce a refaktoringy** .
   - **Myš**
      - Klikněte pravým tlačítkem a vyberte nabídku **rychlé akce a refaktoring** .
      - Najeďte myší na červenou vlnovkou a klikněte na ![žárovka chyby](media/error-bulb.png) ikona, která se zobrazí.
      - Klikněte na ![žárovka chyby](media/error-bulb.png) ikona, která se zobrazí na levém okraji, pokud se na řádku již nachází textový kurzor s červenou vlnovkou

      ![Vygenerovat náhled třídy](media/class-preview-cs.png)

3. Vyberte jednu z možností z rozevírací nabídky:

   - Při generování třídy '*TypeName*' v novém souboru se &mdash; vytvoří třída s názvem *TypeName* v souboru s názvem *TypeName*. cs/. vb
   - Při generování třídy *TypeName* se &mdash; v aktuálním souboru vytvoří třída s názvem *TypeName* .
   - Vygenerovat vnořenou *TypeName* třídu TypeName &mdash; vytvoří třídu s názvem *TypeName* vnořenou uvnitř aktuální třídy.
   - Generovat nový typ... &mdash; Vytvoří novou třídu nebo strukturu se všemi zadanými vlastnostmi.

   > [!TIP]
   > Pomocí odkazu **Náhled změn** v dolní části okna Preview [zobrazíte všechny změny](../../ide/preview-changes.md) , které budou provedeny před provedením výběru.

4. Pokud jste vybrali možnost **Generovat novou položku typu** , otevře se dialogové okno **generovat typ** . Nakonfigurujte přístupnost, druh a umístění nového typu.

   ![Generovat typ](media/class-newtype-cs.png)

   Výběr | Popis
   --- | ---
   Access | Nastavte typ na *výchozí*, *interní* nebo *veřejný* přístup.
   Druh | To lze nastavit jako *třídu* nebo *strukturu*.
   Název | Tato změna se nedá změnit a bude to název, který jste už zadali.
   Project | Pokud je ve vašem řešení více projektů, můžete zvolit, kde má být třída/struktura živá.
   Název souboru | Můžete vytvořit nový soubor nebo můžete přidat typ do existujícího souboru.

Třída nebo struktura je vytvořena. V jazyce C# je vytvořen i konstruktor.

- C#

   ![Generovat výsledek třídy C #](media/class-result-cs.png)

- Visual Basic

   ![Generovat výsledek třídy VB](media/class-result-vb.png)

## <a name="see-also"></a>Viz také

- [Generování kódu](../code-generation-in-visual-studio.md)
- [Náhled změn](../../ide/preview-changes.md)
