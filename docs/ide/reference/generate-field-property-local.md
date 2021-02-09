---
title: Generovat pole, vlastnost, místní proměnná
description: Naučte se, jak pomocí nabídky rychlé akce a refaktoringy vygenerovat kód pro dříve nedeklarované pole, vlastnost nebo místní.
ms.custom: SEO-VS-2020
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 57e6490b9375e3f59e0d214ae3f5300f2276964d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914901"
---
# <a name="generate-a-field-property-or-local-variable-in-visual-studio"></a>Generování pole, vlastnosti nebo místní proměnné v aplikaci Visual Studio

Tato generace kódu platí pro:

- C#

- Visual Basic

**Co:** Umožňuje hned vygenerovat kód pro dříve nedeklarované pole, vlastnost nebo místní.

**Když:** Při psaní můžete zavést nové pole, vlastnost nebo místní, a to tak, aby je bylo možné správně deklarovat automaticky.

**Proč:** Je možné deklarovat pole, vlastnost nebo místní před použitím, ale tato funkce vygeneruje deklaraci a typ automaticky.

## <a name="how-to"></a>Postupy

1. Umístěte kurzor na řádek, kde je červená vlnovka. Červená vlnovka indikuje pole, místní nebo vlastnost, která ještě neexistuje.

   - C#:

       ![Zvýrazněný kód C #](media/field-highlight-cs.png)

   - Visual Basic:

       ![Zvýrazněný kód VB](media/field-highlight-vb.png)

2. Dále proveďte jednu z následujících akcí:

   - **Klávesnice**
      - Stiskněte klávesu **CTRL** + **.** pro aktivaci nabídky **rychlé akce a refaktoringy** .
   - **Myš**
      - Klikněte pravým tlačítkem a vyberte nabídku **rychlé akce a refaktoring** .
      - Najeďte myší na červenou vlnovkou a klikněte na ![žárovka chyby](media/error-bulb.png) ikona, která se zobrazí.
      - Klikněte na ![žárovka chyby](media/error-bulb.png) ikona, která se zobrazí na levém okraji, pokud se na řádku již nachází textový kurzor s červenou vlnovkou

      ![Generovat pole/vlastnost/místní náhled](media/field-preview-cs.png)

3. V rozevírací nabídce vyberte jednu z možností generování.

   > [!TIP]
   > Pomocí odkazu **Náhled změn** v dolní části okna Preview [zobrazíte všechny změny](../../ide/preview-changes.md) , které budou provedeny před provedením výběru.

   Vytvoří se pole, vlastnost nebo místní typ s typem odvozeným z jeho využití.

   - C#:

       ![Generovat výsledek metody C #](media/field-result-cs.png)

   - Visual Basic:

       ![Generovat výsledek metody VB](media/field-result-vb.png)

## <a name="see-also"></a>Viz také

- [Generování kódu](../code-generation-in-visual-studio.md)
- [Náhled změn](../../ide/preview-changes.md)
