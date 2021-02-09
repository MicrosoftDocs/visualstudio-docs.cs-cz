---
title: Převod lokální funkce na metodu
description: Přečtěte si, jak pomocí nabídky rychlé akce a refaktoring převést místní funkci na metodu.
ms.custom: SEO-VS-2020
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 3cecafe64f7ead8157a9cb6c80d2f0a245566390
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99919718"
---
# <a name="convert-a-local-function-to-a-method"></a>Převod lokální funkce na metodu

Tento refaktoring platí pro:

- C#

**Co:** Převod místní funkce na metodu.

**Když:** Máte místní funkci, kterou chcete definovat mimo aktuální místní kontext.

**Proč:** Chcete převést lokální funkci na metodu, aby ji bylo možné volat mimo místní kontext. Je možné, že budete chtít převést na metodu, když je místní funkce příliš dlouhá. Při definování funkce v samostatné metodě je váš kód snazší číst.

## <a name="convert-local-function-to-method-refactoring"></a>Převod místní funkce na refaktoring metody

1. Umístěte kurzor do místní funkce.

    ![Převod místní funkce na ukázku kódu metody](media/convert-local-function-to-method.png)

2. Stiskněte klávesu **CTRL** + **.** pro aktivaci nabídky **rychlé akce a refaktoringy** .

    ![Ukázka převodu místní funkce na kód metody oprava](media/convert-local-function-to-method-codefix.png)

2. Stisknutím klávesy Enter přijměte refaktoring.

    ![Převod místní funkce na vzorek výsledku metody](media/convert-local-function-to-method-result.png)

## <a name="see-also"></a>Viz také

- [Refactoring](../refactoring-in-visual-studio.md)
- [Tipy pro vývojáře na platformě .NET](../csharp-developer-productivity.md)
