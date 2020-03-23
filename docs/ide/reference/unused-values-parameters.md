---
title: Nepoužívané hodnoty a parametry
ms.date: 02/15/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: ce2b0f1e0c0db45c478c3917306683b314da0564
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "65531879"
---
# <a name="unused-value-assignments-variables-and-parameters"></a>Přiřazení nepoužitých hodnot, proměnné a parametry

Toto refaktoring se vztahuje na:

- C#
- Visual Basic

**Co:** Zeslabí nepoužívané parametry a vygeneruje upozornění pro nepoužívané hodnoty výrazů. Kompilátor také provádí analýzu toku k vyhledání všech nevyužitých přiřazení hodnot. Nevyužité přiřazení hodnot zeslábne a zobrazí se žárovka s [rychlou akcí](../quick-actions.md) k odebrání nadbytečného přiřazení. Nepoužívané proměnné s neznámými hodnotami zobrazují návrh [rychlé akce,](../quick-actions.md) který místo toho použije [zahozené hodnoty.](/dotnet/csharp/discards) (Zahození jsou dočasné, fiktivní proměnné, které jsou záměrně nepoužívané v kódu aplikace. Mohou snížit přidělení paměti a usnadnit čtení kódu.)

**Kdy:** Máte přiřazení hodnot, parametry nebo hodnoty výrazu, které se nikdy nepoužívají.

**Proč:** Někdy je obtížné zjistit, zda se přiřazení hodnoty, proměnná nebo parametr již nepoužívá. Vyblednutím těchto hodnot nebo generováním upozornění získáte vizuální upozornění na to, jaký kód můžete odstranit.

## <a name="unused-expression-values-and-parameters-diagnostic"></a>Nevyužité hodnoty výrazů a diagnostika parametrů

1. Mít libovolnou hodnotu přiřazení, proměnnou nebo parametr, který se nepoužívá.
2. Nevyužité přiřazení hodnoty nebo parametr se zobrazí vybledlé. Nepoužitá hodnota výrazu generuje upozornění.

  ![Nepoužívaný](media/unused-parameter.png)
  ![parametr Nevyužitá](media/unused-value.png)
  ![hodnota](media/unused-value-assignment.png)
  ![Přiřazení nevyužité hodnoty Nevyužitá hodnota zahozena](media/unused-value-discard.png)

## <a name="see-also"></a>Viz také

- [Refactoring](../refactoring-in-visual-studio.md)
- [Tipy pro vývojáře rozhraní .NET](../csharp-developer-productivity.md)
