---
title: Třídy pro globální formuláře systému Windows a webové formuláře specifické pro jazykovou verzi
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- globalization [Windows Forms], classes
- Web applications [.NET Framework], globalization
- culture, culture-specific classes
- numbers, international
- localization [Windows Forms], classes
- globalization [Visual Studio], culture-specific classes
- Windows Forms, localization
- international applications [Visual Studio], data formats
- time [Visual Studio], international
- dates [Visual Studio], international
- culture
- international characters
- currency formats
- ASP.NET, globalization
- classes [Visual Studio], culture-specific
- localization [Visual Studio], culture-specific classes
ms.assetid: 0d06a0a4-f887-4f7c-bde7-1d543c06f803
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: d0a6947127fd564eace97c919a425d4a3a3360c4
ms.sourcegitcommit: b6dfa1bdf4c23c2e341754454bbd4758db2218e0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/08/2018
ms.locfileid: "48863566"
---
# <a name="culture-specific-classes-for-global-windows-forms-and-web-forms"></a>Třídy specifické pro jazykovou verzi pro globální Windows forms a webové formuláře

Jednotlivé jazykové verze mají různých konvencí zobrazení data, času, čísla, měny a dalších informací. <xref:System.Globalization> Obor názvů obsahuje třídy, které lze použít k úpravě hodnoty jak specifické pro jazykovou verzi jsou zobrazeny, jako například:
- <xref:System.Globalization.DateTimeFormatInfo>
- **Kalendář**
- <xref:System.Globalization.NumberFormatInfo>

## <a name="using-the-culture-setting"></a>Pomocí nastavení jazykové verze

Použít nastavení jazykové verze uložené v aplikaci nebo v **místní nastavení** ovládací panely k určení úmluv jazykové verze na čas spuštění a odpovídajícím způsobem formátovat informace. Další informace o nastavení jazykové verze, najdete v části [postupy: nastavení jazykové verze a jazykové verze uživatelského rozhraní pro globalizaci webové stránky ASP.NET](https://msdn.microsoft.com/Library/76091f86-f967-4687-a40f-de87bd8cc9a0). Třídy, které automaticky formátovat informace podle nastavení jazykové verze se nazývají *specifické pro jazykovou verzi*. Jsou některé metody specifické pro jazykovou verzi
- <xref:System.IFormattable.ToString%2A?displayProperty=fullName>
- <xref:System.Console.WriteLine%2A?displayProperty=fullName>
- <xref:System.String.Format%2A?displayProperty=fullName>

Některé funkce specifické pro jazykovou verzi (v jazyce Visual Basic) jsou `MonthName` a `WeekDayName`.

Například následující kód ukazuje, jak můžete použít <xref:System.IFormattable.ToString%2A> metodu formát měny pro aktuální jazykovou verzi:

```vb
' Put the Imports statements at the beginning of the code module
Imports System.Threading
Imports System.Globalization
' Display a number with the culture-specific currency formatting
Dim MyInt As Integer = 100
Console.WriteLine(MyInt.ToString("C", Thread.CurrentThread.CurrentCulture))
```

```csharp
// Put the using statements at the beginning of the code module
using System.Threading;
using System.Globalization;
// Display a number with the culture-specific currency formatting
int myInt = 100;
Console.WriteLine(myInt.ToString("C", Thread.CurrentThread.CurrentCulture));
```

Pokud je jazyková verze nastavena na "fr-FR", zobrazí se následující ve výstupním okně:

`100,00`

Pokud je jazyková verze nastavena na hodnotu "en US", zobrazí se následující ve výstupním okně:

`$100.00`

## <a name="see-also"></a>Viz také:

- <xref:System.IFormattable.ToString%2A?displayProperty=fullName>
- <xref:System.Globalization.DateTimeFormatInfo>
- <xref:System.Globalization.NumberFormatInfo>
- <xref:System.Globalization.Calendar>
- <xref:System.Console.WriteLine%2A?displayProperty=fullName>
- <xref:System.String.Format%2A?displayProperty=fullName>
- [Globalizace a lokalizace aplikací](../ide/globalizing-and-localizing-applications.md)