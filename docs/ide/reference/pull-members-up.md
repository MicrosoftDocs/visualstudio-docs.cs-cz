---
title: Vyžádané členy nahoru
description: Přečtěte si, jak pomocí nabídky rychlé akce a refaktoring přetáhnout členy do základního typu.
ms.custom: SEO-VS-2020
ms.date: 02/13/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: ee5776e9fc39b77f8059146848d847e0976a5664
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99958281"
---
# <a name="pull-members-up"></a>Vyžádané členy nahoru

Tento refaktoring platí pro:

- C#

- Visual Basic

**Co:** Umožňuje vyžádat členy až do základního typu.

**Když:** Implementovali jste rozhraní a chcete přesunout člena do základního typu.

**Proč:** Vyjímání členů umožňuje jiným implementům vašeho rozhraní dědit i tyto členy.

## <a name="how-to"></a>Postupy

1. Umístěte kurzor do libovolného člena implementovaného rozhraní.
2. Stiskněte klávesu **CTRL** + **.** pro aktivaci nabídky **rychlé akce a refaktoringy** .

   ![Vyžádané členy nahoru](media/pull-members-up.png)

2. Vyberte **vyžádané členy až do základního typu**.

3. V dialogovém okně vyberte, které členy byste chtěli přidat do vybraného rozhraní.

   ![Vyžádané členství](media/pull-members-up-dialog.png)

4. Vyberte **OK**. Vybraní členové jsou vyzískáni až do rozhraní.

   ![Vyžádaného člena je dokončené.](media/pull-members-up-completed.png)

## <a name="see-also"></a>Viz také

- [Refactoring](../refactoring-in-visual-studio.md)
