---
title: Upravit a pokračovat (Visual C#) | Microsoft Docs
description: Upravit a pokračovat jsou k dispozici pro projekty Visual C#. Přečtěte si, jaké úpravy jsou podporované a jak můžete řídit, jestli a kdy se vaše úpravy aplikují.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 55406001e4017c853895002445d9bd5d614b4b20
ms.sourcegitcommit: 47da50a74fcd3db66d97cb20accac983bc41912f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/08/2020
ms.locfileid: "96862878"
---
# <a name="edit-and-continue-visual-c"></a>Upravit a pokračovat (Visual C#)
 Při úpravách a pokračování pro jazyk C# můžete provádět změny kódu v režimu pozastavení při ladění. Změny lze použít bez nutnosti zastavit a znovu spustit ladicí relaci. V režimu spuštění je zdrojový Editor určen jen pro čtení.

 Příkaz Upravit a pokračovat podporuje většinu změn, které byste mohli chtít provést během relace ladění, ale existují výjimky. Další informace najdete v tématu [podporované změny kódu (C# a Visual Basic)](../debugger/supported-code-changes-csharp.md).

 Funkce upravit a pokračovat je podporovaná v UWP ve Windows 10 a aplikacích pro x86 a x64, které cílí na .NET Framework 4,6 Desktop nebo novějších verzích (.NET Framework je jenom desktopová verze).

 > [!NOTE]
 > Mezi nepodporované aplikace a platformy patří Silverlight 5 a Windows 8.1.

 Když je povolená možnost upravit a pokračovat, podporované změny se použijí automaticky, když použijete příkaz pro spuštění ladicího programu, jako je například **pokračovat**, **Krok**, **nastavit další příkaz** nebo provést vyhodnocení funkce v okně ladicího programu.

 Další informace najdete v tématu [Postupy: použití funkce upravit a pokračovat (C#)](../debugger/how-to-use-edit-and-continue-csharp.md).

## <a name="see-also"></a>Viz také
- [Postupy: Použití operace Upravit a pokračovat (C#)](../debugger/how-to-use-edit-and-continue-csharp.md)
- [Podporované změny kódu (C# a Visual Basic)](../debugger/supported-code-changes-csharp.md)
- [Zápis a ladění spuštěného kódu XAML pomocí programu XAML Hot reloading v aplikaci Visual Studio](../xaml-tools/xaml-hot-reload.md)
