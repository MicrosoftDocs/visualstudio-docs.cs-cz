---
title: Generovat rychlou akci deconstructoru
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 5a3a89d15d05b44575fede98d3043d706b24c1d9
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "65531888"
---
# <a name="generate-a-deconstructor-in-visual-studio"></a>Generování deconstructor v sadě Visual Studio

Toto generování kódu se vztahuje na:

- C#

**Co:** Umožňuje okamžitě vygenerovat zástupný kód metody pro nový deconstructor.

**Kdy:** Chcete správně dekonstruovat typ automaticky.

**Proč:** Můžete ručně zadat deconstructor, ale tato funkce generuje zástupný kód pro vás se správnými parametry out.

## <a name="generate-a-deconstructor"></a>Generovat deconstructor

1. Deklarujte nový typ s požadovanými parametry out. Tato deklarace způsobí chybu, když nelze najít žádnou deconstruct instanci odpovídající vaší deklaraci.

   ![Chybí chyba deconstructor](media/deconstruct.png)

2. Udělejte jeden z následujících kroků:

   - **Klávesnice**
      - S kurzorem v deklaraci vyberte Ctrl+. spouštět nabídku **Rychlé akce a Refaktorings.**
   - **Myš**
      - Klikněte pravým tlačítkem myši a vyberte nabídku **Rychlé akce a Refaktoringy.**
      - Výběrem ![Šroubovák](media/screwdriver.png) ikona, která se zobrazí na levém okraji, pokud je textový kurzor již na prázdném řádku ve třídě.

      ![Generovat opravu kódu deconstructor](media/deconstruct-codefix.png)

3. Vyberte **Generate metoda MyInternalClass.Deconstruct pro** generování deconstructor.

   ![Výsledný deconstructor kód](media/deconstruct-result.png)

## <a name="see-also"></a>Viz také

- [Generování kódu](../code-generation-in-visual-studio.md)
- [Náhled změn](../../ide/preview-changes.md)
- [Tipy pro vývojáře .NET](../csharp-developer-productivity.md)