---
title: Přidání explicitního přetypování
ms.date: 03/26/2020
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: e159082266b848ce4742e436c706f3f71b2cc9ea
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "84182973"
---
# <a name="add-explicit-cast"></a>Přidání explicitního přetypování

Tato generace kódu platí pro:

- C#

**Co:** Umožňuje automaticky přidat explicitní přetypování na výraz na základě využití.

**Když:** Musíte přidat explicitní přetypování do výrazu a chcete ho správně přiřadit automaticky.

**Proč:** Explicitní přetypování můžete přidat do výrazu ručně, ale tato funkce je automaticky přidá na základě kontextu kódu.

## <a name="how-to-use-it"></a>Jak ji použít

1. Umístěte blikající kurzor na chybu.
2. Stiskněte klávesu **CTRL** + **.** pro aktivaci nabídky **rychlé akce a refaktoringy** .
3. Vyberte možnost **Přidat explicitní přetypování**.

   ![Přidat k rychlé akci explicitního přetypování v aplikaci Visual Studio](media/add-explicit-cast.png)

## <a name="see-also"></a>Viz také

- [Generování kódu](../code-generation-in-visual-studio.md)
- [Refactoring](../refactoring-in-visual-studio.md)
