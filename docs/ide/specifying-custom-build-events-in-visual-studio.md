---
title: Určení vlastních událostí sestavení
description: Přečtěte si, jak můžete automaticky spouštět příkazy v aplikaci Visual Studio před spuštěním sestavení nebo po jeho dokončení.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- build events, customizing
ms.assetid: 69e935a5-e208-4bcd-865c-3e5f9b047ca8
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f1d339f9bbf170d2df545e69c698f786198695ad
ms.sourcegitcommit: c9a84e6c01e12ccda9ec7072dd524830007e02a3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2020
ms.locfileid: "92136781"
---
# <a name="specify-custom-build-events-in-visual-studio"></a>Určení vlastních událostí sestavení v aplikaci Visual Studio

Zadáním vlastní události sestavení můžete automaticky spustit příkazy před spuštěním sestavení nebo po jeho dokončení. Například můžete spustit soubor *. bat* před spuštěním sestavení nebo zkopírovat nové soubory do složky po dokončení sestavení. Události sestavení se spouštějí pouze v případě, že sestavení úspěšně dosáhne těchto bodů v procesu sestavení.

Konkrétní informace o programovacím jazyce, který používáte, najdete v následujících tématech:

- Visual Basic--[Postupy: určení událostí sestavení (Visual Basic)](../ide/how-to-specify-build-events-visual-basic.md).

- C# a F #--[Postupy: určení událostí sestavení (C#)](../ide/how-to-specify-build-events-csharp.md).

- Visual C++ –[Zadejte události sestavení](/cpp/build/specifying-build-events).

## <a name="syntax"></a>Syntax

Události sestavení následují stejnou syntaxi jako příkazy pro systém DOS, ale makra můžete použít k jednoduššímu vytváření událostí sestavení. Seznam dostupných maker naleznete v tématu [dialogové okno Příkazový řádek události před sestavením/po sestavení](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md).

Nejlepších výsledků dosáhnete pomocí těchto tipů pro formátování:

- Přidejte `call` příkaz před všechny události sestavení, které spouštějí soubory *. bat* .

   Příklad: `call C:\MyFile.bat`

   Příklad: `call C:\MyFile.bat call C:\MyFile2.bat`

- Uzavřete cesty k souborům do uvozovek.

   Příklad (pro [!INCLUDE[win8](../debugger/includes/win8_md.md)] ): "% ProgramFiles (x86)% \ Microsoft SDKs\Windows\v8.0A\Bin\NETFX 4,0 Tools\gacutil.exe"-If "$ (TargetPath)"

- Oddělte více příkazů pomocí konců řádků.

- Podle potřeby zahrňte zástupné znaky.

   Příklad: `for %I in (*.txt *.doc *.html) do copy %I c:\` *MyDirectory*`\`

  > [!NOTE]
  > `%I` ve výše uvedeném kódu by měly být `%%I` v dávkových skriptech.

## <a name="see-also"></a>Viz také

- [Kompilace a sestavení](../ide/compiling-and-building-in-visual-studio.md)
- [Dialogové okno Příkazový řádek události před sestavením/po sestavení](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)
- [Speciální znaky nástroje MSBuild](../msbuild/msbuild-special-characters.md)
- [Návod: Vytvoření aplikace](../ide/walkthrough-building-an-application.md)
