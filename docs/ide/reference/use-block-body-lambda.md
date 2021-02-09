---
title: Použití výrazu lambda nebo textu bloku
description: Naučte se, jak pomocí nabídky rychlé akce a refaktoringu Refaktorovat výraz lambda, aby se použil text výrazu nebo tělo bloku.
ms.custom: SEO-VS-2020
ms.date: 02/14/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: bc3b80ad625c58fbe9127978ebc23fd8c764f4d3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99889899"
---
# <a name="use-expression-body-or-block-body-for-lambda-expressions"></a>Pro výrazy lambda použít text výrazu nebo text bloku

Tento refaktoring platí pro:

- C#

**Co:** Umožňuje Refaktorovat výraz lambda, aby používal tělo výrazu nebo tělo bloku.

**Když:** Preferujete výrazy lambda pro použití těla výrazu nebo těla bloku.

**Proč:** Výrazy lambda lze Refaktorovat, aby se zlepšila čitelnost v závislosti na vašich uživatelských preferencích.

## <a name="lambda-expression-body-or-block-body-refactoring"></a>Refaktoring těla výrazu lambda nebo bloku

1. Umístěte kurzor na pravé straně operátoru lambda.
2. Stiskněte klávesu **CTRL** + **.** pro aktivaci nabídky **rychlé akce a refaktoringy** .

  ![Použít lambda výraz/tělo bloku](media/block-body-lambda.png)

3. Vyberte možnost **použít text bloku pro výrazy lambda** nebo **použijte tělo výrazu pro výrazy lambda**.

## <a name="see-also"></a>Viz také

- [Refactoring](../refactoring-in-visual-studio.md)
- [Tipy pro vývojáře na platformě .NET](../csharp-developer-productivity.md)