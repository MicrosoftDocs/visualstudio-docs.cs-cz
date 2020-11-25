---
title: Převést anonymní typ na třídu
description: Přečtěte si, jak pomocí nabídky rychlé akce a refaktoring převést anonymní typ na třídu v aplikaci Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
monikerRange: '>= vs-2019'
ms.openlocfilehash: a041c077a41ce6b37d74507723ec1ce0f8c9585c
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/25/2020
ms.locfileid: "96040782"
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
