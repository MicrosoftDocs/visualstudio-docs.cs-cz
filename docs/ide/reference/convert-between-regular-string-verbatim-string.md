---
title: Převod mezi pravidelnými a doslovnémi řetězcovými literály
description: Přečtěte si, jak pomocí nabídky rychlé akce a refaktoring převádět mezi regulárním řetězcem a doslovnémi řetězcovými literály.
ms.custom: SEO-VS-2020
ms.date: 06/08/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 1c335c90183e4c5c97b1a2737a2edd8a1b86fb77
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99918341"
---
# <a name="convert-between-regular-string-and-verbatim-string-literals-refactoring"></a>Převod mezi regulárním řetězcem a doslovném přefaktoringem řetězcových literálů

Tento refaktoring platí pro:

- C#

**Co:** Umožňuje převádět mezi regulárním řetězcem a doslovnémi textovými literály.

**Když:** Buď chcete ušetřit místo nebo poskytnout větší přehlednost kódu.

**Proč:** Převod doslovného řetězcového literálu na regulární řetězcový literál může přispět k úspory místa. Převádění regulárního řetězcového literálu na doslovné řetězcový literál může poskytovat větší přehlednost.

## <a name="how-to"></a>Postupy

1. Umístěte blikající kurzor buď na běžný řetězec, nebo na doslovné řetězcový literál:

2. Stiskněte klávesu **CTRL** + **.** pro aktivaci nabídky **rychlé akce a refaktoringy** .

3. Vyberte jednu z následujících možností:

    Vyberte **Převést na běžný řetězec**.

    ![Převést na běžný řetězec](media/convert-to-regular-string.png)

    Vyberte **Převést na doslovný řetězec**.

    ![Převést na doslovné řetězec](media/convert-to-verbatim-string.png)

## <a name="see-also"></a>Viz také

- [Refactoring](../refactoring-in-visual-studio.md)