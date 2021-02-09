---
title: Převést anonymní typ na třídu
description: Přečtěte si, jak pomocí nabídky rychlé akce a refaktoring převést anonymní typ na třídu v aplikaci Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
monikerRange: '>= vs-2019'
ms.openlocfilehash: 19e755e4b56675265d85a416684f2b42bd7ccd13
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99907653"
---
# <a name="convert-anonymous-type-to-class"></a>Převedení anonymního typu na třídu

Tento refaktoring platí pro:

- C#

- Visual Basic

**Co:** Převést anonymní typ na třídu.

**Když:** Máte anonymní typ, na který chcete pokračovat ve vytváření ve třídě.

**Proč:** Anonymní typy jsou užitečné, pokud je používáte pouze místně. Jak váš kód roste, je vhodné mít snadný způsob, jak je propagovat na třídu.

## <a name="how-to"></a>Postupy

1. Umístěte kurzor do anonymního typu.
2. Stiskněte klávesu **CTRL** + **.** pro aktivaci nabídky **rychlé akce a refaktoringy** .

   ![Převést anonymní typ na třídu](media/convert-anon-to-class.png)

2. Stisknutím klávesy **ENTER** přijměte refaktoring.

   ![Převést anonymní typ na povolenou třídu](media/convert-anon-to-class-complete.png)

## <a name="see-also"></a>Viz také

- [Refactoring](../refactoring-in-visual-studio.md)
