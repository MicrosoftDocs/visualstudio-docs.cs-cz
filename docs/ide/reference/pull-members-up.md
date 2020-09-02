---
title: Vyžádané členy nahoru
ms.date: 02/13/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 2d1f7deb7aca1fed7b75b66b17ce2e4d63768a0d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62969154"
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
