---
title: Nepoužívané hodnoty a parametry
description: Přečtěte si o nepoužívaných přiřazeních hodnot, proměnných a parametrech a o tom, jak se zobrazí v editoru kódu v aplikaci Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/15/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: cd0b6e936f4478cb4b74a3f004e69d77dbad7fbc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99960608"
---
# <a name="unused-value-assignments-variables-and-parameters"></a>Přiřazení nepoužitých hodnot, proměnné a parametry

Tento refaktoring platí pro:

- C#
- Visual Basic

**Co:** Vykreslí nepoužité parametry a vygeneruje upozornění pro nepoužité hodnoty výrazů. Kompilátor také provádí analýzu toku k vyhledání nepoužitých přiřazení hodnoty. Nepoužitá přiřazení hodnot se rozsvítí a žárovka se zobrazuje jako [rychlá akce](../quick-actions.md) pro odebrání redundantního přiřazení. Nepoužité proměnné s neznámými hodnotami ukazují návrh [rychlé akce](../quick-actions.md) pro místo toho použití [zahození](/dotnet/csharp/discards) . (Výměty jsou dočasné a fiktivní proměnné, které jsou záměrně nepoužívané v kódu aplikace. Můžou snížit přidělení paměti a usnadnit čtení kódu.)

**Když:** Máte přiřazené hodnoty, parametry nebo hodnoty výrazů, které se nikdy nepoužívají.

**Proč:** Někdy je obtížné zjistit, jestli se už nepoužívá přiřazení hodnoty, proměnná nebo parametr. Na základě těchto hodnot nebo vygenerování upozornění získáte vizuální přehled toho, který kód můžete odstranit.

## <a name="unused-expression-values-and-parameters-diagnostic"></a>Nepoužité hodnoty a parametry výrazů pro diagnostiku

1. Mít jakékoli přiřazení hodnoty, proměnnou nebo parametr, který se nepoužívá.
2. Nepoužité přiřazení nebo parametr hodnoty se zobrazí nezvolna. Nepoužitá hodnota výrazu vygeneruje upozornění.

  ![Nepoužitý parametr nepoužité přiřazení hodnoty nepoužité při ](media/unused-parameter.png)
   ![ ](media/unused-value.png)
   ![ ](media/unused-value-assignment.png)
   ![ zahození hodnoty](media/unused-value-discard.png)

## <a name="see-also"></a>Viz také

- [Refactoring](../refactoring-in-visual-studio.md)
- [Tipy pro vývojáře na platformě .NET](../csharp-developer-productivity.md)
