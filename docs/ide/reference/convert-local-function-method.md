---
title: Převod lokální funkce na metodu
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 3572682fe68d9b0b1bc4adee537de5cd056a8906
ms.sourcegitcommit: 9a3972eb85de5443ac2bc03964c5a251c39b2921
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/26/2019
ms.locfileid: "71301693"
---
# <a name="convert-a-local-function-to-a-method"></a>Převod lokální funkce na metodu

Tento refaktoring platí pro:

- C#

**Co:** Převod místní funkce na metodu.

**Kdy:** Máte místní funkci, kterou chcete definovat mimo aktuální místní kontext.

**Proč:** Chcete převést lokální funkci na metodu, aby ji bylo možné volat mimo místní kontext. Je možné, že budete chtít převést na metodu, když je místní funkce příliš dlouhá. Při definování funkce v samostatné metodě je váš kód snazší číst.

## <a name="convert-local-function-to-method-refactoring"></a>Převod místní funkce na refaktoring metody

1. Umístěte kurzor do místní funkce.

    ![Převod místní funkce na ukázku kódu metody](media/convert-local-function-to-method.png)

2. Stisknutím klávesy **Ctrl**+ **.** aktivační událost **rychlé akce a Refaktoringy** nabídky.

    ![Ukázka převodu místní funkce na kód metody oprava](media/convert-local-function-to-method-codefix.png)

2. Stisknutím klávesy Enter přijměte refaktoring.

    ![Převod místní funkce na vzorek výsledku metody](media/convert-local-function-to-method-result.png)

## <a name="see-also"></a>Viz také:

- [Refactoring](../refactoring-in-visual-studio.md)
- [Tipy pro vývojáře .NET](../csharp-developer-productivity.md)
