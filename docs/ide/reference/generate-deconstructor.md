---
title: Generovat rychlou akci dekonstruktoru
description: Naučte se, jak pomocí nabídky rychlé akce a refaktoring hned vygenerovat zástupnou proceduru metody pro nový dekonstruktor.
ms.custom: SEO-VS-2020
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: ff2ac7682eff1c3da0597a95945a6a0b016d9213
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2020
ms.locfileid: "96617250"
---
# <a name="generate-a-deconstructor-in-visual-studio"></a>Generování dekonstruktoru v aplikaci Visual Studio

Tato generace kódu platí pro:

- C#

**Co:** Umožňuje hned vygenerovat zástupnou proceduru metody pro nový dekonstruktor.

**Když:** Chcete typ správně dekonstruovat automaticky.

**Proč:** Můžete ručně zadat dekonstruktor, ale tato funkce vygeneruje pro vás zástupné procedury se správnými parametry out.

## <a name="generate-a-deconstructor"></a>Vygenerovat dekonstruktor

1. Deklarujete nový typ s požadovanými výstupními parametry. Tato deklarace způsobí chybu, pokud nebyla nalezena žádná instance dekonstrukce, která by odpovídala vaší deklaraci.

   ![Chybějící chyba demontáže](media/deconstruct.png)

2. Proveďte jeden z následujících kroků:

   - **Klávesnice**
      - V deklaraci kurzoru vyberte CTRL +. pro aktivaci nabídky **rychlé akce a refaktoringy** .
   - **Myš**
      - Klikněte pravým tlačítkem a vyberte nabídku **rychlé akce a refaktoring** .
      - Vyberte :::image type="icon" source="media/screwdriver.png"::: ikonu, která se zobrazí v levém okraji, pokud je textový kurzor již na prázdném řádku ve třídě.

      ![Generovat opravu dekonstruktor Code](media/deconstruct-codefix.png)

3. Pro vygenerování dekonstruktoru vyberte **vygenerovat metodu MyInternalClass. deconstruct** .

   ![Výsledný kód dekonstruktoru](media/deconstruct-result.png)

## <a name="see-also"></a>Viz také

- [Generování kódu](../code-generation-in-visual-studio.md)
- [Zobrazit náhled změn](../../ide/preview-changes.md)
- [Tipy pro vývojáře .NET](../csharp-developer-productivity.md)