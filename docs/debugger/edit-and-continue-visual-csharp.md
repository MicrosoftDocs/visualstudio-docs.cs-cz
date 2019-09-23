---
title: Upravit a pokračovat (vizuál C#) | Microsoft Docs
ms.date: 10/11/2017
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, Edit and Continue
- Edit and Continue [C#]
- debugging [C#], Edit and Continue
ms.assetid: 591bd1b7-ef10-4d10-817b-3f92ca4be006
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 665e778fc0881ac05e165c85700d15285622c762
ms.sourcegitcommit: 88f576ac32af31613c1a10c1548275e1ce029f4f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71186354"
---
# <a name="edit-and-continue-visual-c"></a>Upravit a pokračovat (Visual C#)
 S úpravou a pokračováním pro C#můžete provádět změny kódu v režimu pozastavení při ladění. Změny lze použít bez nutnosti zastavit a znovu spustit ladicí relaci. V režimu spuštění je zdrojový Editor určen jen pro čtení.

 Příkaz Upravit a pokračovat podporuje většinu změn, které byste mohli chtít provést během relace ladění, ale existují výjimky. Další informace najdete v tématu [podporované změny kódu (C# a Visual Basic)](../debugger/supported-code-changes-csharp.md).

 Funkce upravit a pokračovat je podporovaná v UWP ve Windows 10 a aplikacích pro x86 a x64, které cílí na .NET Framework 4,6 Desktop nebo novějších verzích (.NET Framework je jenom desktopová verze).

 > [!NOTE]
 > Mezi nepodporované aplikace a platformy patří ASP.NET 5, Silverlight 5 a Windows 8.1.

 Když je povolená možnost upravit a pokračovat, podporované změny se použijí automaticky, když použijete příkaz pro spuštění ladicího programu, jako je například **pokračovat**, **Krok**, **nastavit další příkaz**nebo provést vyhodnocení funkce v okně ladicího programu.

 Další informace najdete v tématu [jak: Použijte úpravy a pokračování (C#)](../debugger/how-to-use-edit-and-continue-csharp.md).

## <a name="see-also"></a>Viz také
- [Postupy: Použití operace Upravit a pokračovat (C#)](../debugger/how-to-use-edit-and-continue-csharp.md)
- [Podporované změny kódu (C# a Visual Basic)](../debugger/supported-code-changes-csharp.md)
- [Zápis a ladění spuštěného kódu XAML pomocí programu XAML Hot reloading v aplikaci Visual Studio](../debugger/xaml-hot-reload.md)
