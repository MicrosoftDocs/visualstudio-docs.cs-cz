---
title: Určení vlastních událostí sestavení
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
ms.openlocfilehash: fda60ffb97ecb44bd4a881cb42e4d9199cc958b8
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "76115341"
---
# <a name="specify-custom-build-events-in-visual-studio"></a>Určení vlastních událostí sestavení v sadě Visual Studio

Zadáním vlastní události sestavení můžete automaticky spustit příkazy před spuštěním sestavení nebo po jeho dokončení. Můžete například spustit soubor *BAT* před spuštěním sestavení nebo zkopírovat nové soubory do složky po dokončení sestavení. Build události spustit pouze v případě, že sestavení úspěšně dosáhne těchto bodů v procesu sestavení.

Konkrétní informace o programovacím jazyce, který používáte, naleznete v následujících tématech:

- Visual Basic--[Postup: Zadejte události sestavení (Visual Basic)](../ide/how-to-specify-build-events-visual-basic.md).

- C# a F#--[Postup: Zadejte události sestavení (C#)](../ide/how-to-specify-build-events-csharp.md).

- Visual C++--[Zadejte události sestavení](/cpp/build/specifying-build-events).

## <a name="syntax"></a>Syntaxe

Události sestavení se řídí stejnou syntaxí jako příkazy DOSu, ale můžete pomocí maker snadněji vytvářet události sestavení. Seznam dostupných maker naleznete v [tématu Dialogové okno příkazového řádku Událost a po sestavení před sestavením](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md).

Nejlepších výsledků dosáhnete, postupujte podle následujících tipů pro formátování:

- Před `call` všechny události sestavení, které spouštějí soubory *BAT,* přidejte příkaz.

   Příklad: `call C:\MyFile.bat`

   Příklad: `call C:\MyFile.bat call C:\MyFile2.bat`

- Cesty k souborům uzavřete do uvozovek.

   Příklad (pro): [!INCLUDE[win8](../debugger/includes/win8_md.md)]%ProgramFiles(x86)%\Microsoft SDKS\Windows\v8.0A\Bin\NETFX 4.0 Tools\gacutil.exe" -if "$(TargetPath)"

- Oddělte více příkazů pomocí zalomení řádků.

- Podle potřeby zahrňte zástupné znaky.

   Příklad: `for %I in (*.txt *.doc *.html) do copy %I c:\` *mydirectory*`\`

  > [!NOTE]
  > `%I`ve výše uvedeném `%%I` kódu by měly být v dávkových skriptech.

## <a name="see-also"></a>Viz také

- [Kompilace a sestavení](../ide/compiling-and-building-in-visual-studio.md)
- [Dialogové okno Příkazový řádek Události a po sestavení před sestavením](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)
- [MSBuild speciální znaky](../msbuild/msbuild-special-characters.md)
- [Návod: Sestavení aplikace](../ide/walkthrough-building-an-application.md)
