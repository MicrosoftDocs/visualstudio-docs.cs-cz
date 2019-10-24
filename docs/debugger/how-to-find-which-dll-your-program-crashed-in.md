---
title: 'Postupy: hledání knihovny DLL, ve které došlo k chybě programu | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.dll
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, DLL crashes
- Module List dialog box
- errors [debugger], DLL crashes
- Modules window
- debugging [Visual Studio], DLL crashes
- DLLs, load order of
ms.assetid: ecf62568-8b65-4a41-b8a4-e962ff2dfb71
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bff4f164e16a65efe4ec3d1f057025168eab8cd2
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72733274"
---
# <a name="how-to-find-which-dll-your-program-crashed-in-c-c-visual-basic-f"></a>Postupy: hledání knihovny DLL, ve které došlo k chybě programuC#( C++,, Visual Basic F#,)

 Pokud vaše aplikace selže během volání systémové knihovny DLL nebo kódu někoho jiného, je nutné zjistit, která knihovna DLL byla aktivní, když došlo k chybě. Pokud dojde k chybě v knihovně DLL mimo vlastní program, můžete umístění identifikovat pomocí okna **moduly** .

### <a name="to-find-where-a-crash-occurred-using-the-modules-window"></a>Zjištění, kde došlo k chybě, pomocí okna moduly

1. Poznamenejte si adresu, kde došlo k chybě.

    Pokud adresa není zobrazená v chybové zprávě, možná budete muset použít alternativní metody k identifikaci knihovny DLL. Pokud se domníváte, že systémová knihovna DLL, můžete při ladění [načíst symboly](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) ze serverů symbolů společnosti Microsoft. V opačném případě možná budete muset místo toho [vytvořit soubor s výpisem paměti](../debugger/using-dump-files.md) s informacemi o haldě. K dispozici jsou různé [nástroje](https://blogs.msdn.microsoft.com/andrehal/2009/12/31/what-is-a-dump-and-how-do-i-create-one/) pro vytváření souborů s výpisem paměti.

2. V nabídce **ladění** vyberte možnost **Windows**a klikněte na **moduly**.

3. V okně **moduly** Najděte sloupec **adresa** . Možná budete muset použít posuvník, abyste ho viděli.

4. Kliknutím na tlačítko **adresa** v horní části sloupce seřadíte knihovny DLL podle adres.

5. Prohledejte seřazený seznam a vyhledejte knihovnu DLL, jejíž rozsah adres obsahuje umístění selhání.

6. Podívejte se na sloupce **název** a **cesta** , kde se zobrazí název a cesta ke knihovně DLL.

## <a name="see-also"></a>Viz také:
- [Ladění projektů knihovny DLL](../debugger/debugging-dll-projects.md)
- [Postupy: Použití okna Moduly](../debugger/how-to-use-the-modules-window.md)