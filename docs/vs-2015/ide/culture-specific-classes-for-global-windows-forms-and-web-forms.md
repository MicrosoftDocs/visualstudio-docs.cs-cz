---
title: Třídy specifické pro jazykovou verzi pro globální Windows Forms a webové formuláře | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: bbd599864cfd1e5af770ab4305380d10c71b622a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49283286"
---
# <a name="culture-specific-classes-for-global-windows-forms-and-web-forms"></a>Třídy pro globální formuláře systému Windows a webové formuláře specifické pro jazykovou verzi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jednotlivé jazykové verze mají různých konvencí zobrazení data, času, čísla, měny a dalších informací. <xref:System.Globalization> Obor názvů obsahuje třídy, které lze použít k úpravě hodnoty jak specifické pro jazykovou verzi jsou zobrazeny, jako například <xref:System.Globalization.DateTimeFormatInfo>, **kalendáře**, a <xref:System.Globalization.NumberFormatInfo>.  
  
## <a name="using-the-culture-setting"></a>Pomocí nastavení jazykové verze  
 Ale ve většině případů bude používat nastavení jazykové verze uložené v aplikaci nebo v **místní nastavení** ovládací panely automaticky určit konvence v době běhu a odpovídajícím způsobem formátovat informace. Další informace o nastavení jazykové verze, najdete v části [jak: nastavit jazykovou verzi a jazykovou verzi uživatelského rozhraní pro Windows Forms globalizace](http://msdn.microsoft.com/en-us/694e049f-0b91-474a-9789-d35124f248f0) nebo [postupy: nastavení jazykové verze a jazykové verze uživatelského rozhraní pro globalizaci webové stránky ASP.NET](http://msdn.microsoft.com/library/76091f86-f967-4687-a40f-de87bd8cc9a0). Třídy, které automaticky formátovat informace podle nastavení jazykové verze, se nazývají specifické pro jazykovou verzi. Některé metody specifické pro jazykovou verzi jsou <xref:System.IFormattable.ToString%2A?displayProperty=fullName>, <xref:System.Console.WriteLine%2A?displayProperty=fullName>, a <xref:System.String.Format%2A?displayProperty=fullName>. Některé funkce specifické pro jazykovou verzi (v jazyce Visual Basic) jsou `MonthName` a `WeekDayName`.  
  
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
  
 Pokud je jazyková verze nastavena na "fr-FR", zobrazí se to v okně výstupu:  
  
 `100,00`  
  
 Pokud je jazyková verze nastavena na hodnotu "en US", zobrazí se to v okně výstupu:  
  
 `$100.00`  
  
## <a name="see-also"></a>Viz také  
 <xref:System.IFormattable.ToString%2A?displayProperty=fullName>   
 <xref:System.Globalization.DateTimeFormatInfo>   
 <xref:System.Globalization.NumberFormatInfo>   
 <xref:System.Globalization.Calendar>   
 <xref:System.Console.WriteLine%2A?displayProperty=fullName>   
 <xref:System.String.Format%2A?displayProperty=fullName>   
 [Globalizace a lokalizace aplikací](../ide/globalizing-and-localizing-applications.md)

