---
title: Upravit a pokračovat (Visual C#) | Microsoft Docs
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
ms.openlocfilehash: 62411229acd2d2f8462984789037fc832dac09b8
ms.sourcegitcommit: 822e61c69514e9f564d37ba6ca6832ccf7fbc60d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/28/2020
ms.locfileid: "91421638"
---
# <a name="edit-and-continue-visual-c"></a>Upravit a pokračovat (Visual C#)
 Při úpravách a pokračování pro jazyk C# můžete provádět změny kódu v režimu pozastavení při ladění. Změny lze použít bez nutnosti zastavit a znovu spustit ladicí relaci. V režimu spuštění je zdrojový Editor určen jen pro čtení.

 Příkaz Upravit a pokračovat podporuje většinu změn, které byste mohli chtít provést během relace ladění, ale existují výjimky. Další informace najdete v tématu [podporované změny kódu (C# a Visual Basic)](../debugger/supported-code-changes-csharp.md).

 Funkce upravit a pokračovat je podporovaná v UWP ve Windows 10 a aplikacích pro x86 a x64, které cílí na .NET Framework 4,6 Desktop nebo novějších verzích (.NET Framework je jenom desktopová verze).

 > [!NOTE]
 > Mezi nepodporované aplikace a platformy patří Silverlight 5 a Windows 8.1.

 Když je povolená možnost upravit a pokračovat, podporované změny se použijí automaticky, když použijete příkaz pro spuštění ladicího programu, jako je například **pokračovat**, **Krok**, **nastavit další příkaz**nebo provést vyhodnocení funkce v okně ladicího programu.

 Další informace najdete v tématu [Postupy: použití funkce upravit a pokračovat (C#)](../debugger/how-to-use-edit-and-continue-csharp.md).

## <a name="see-also"></a>Viz také
- [Postupy: Použití operace Upravit a pokračovat (C#)](../debugger/how-to-use-edit-and-continue-csharp.md)
- [Podporované změny kódu (C# a Visual Basic)](../debugger/supported-code-changes-csharp.md)
- [Zápis a ladění spuštěného kódu XAML pomocí programu XAML Hot reloading v aplikaci Visual Studio](../xaml-tools/xaml-hot-reload.md)
