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
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2020
ms.locfileid: "76115341"
---
# <a name="specify-custom-build-events-in-visual-studio"></a>Určení vlastních událostí sestavení v sadě Visual Studio

Zadání vlastního sestavení události, můžete automaticky spustit příkazy před zahájením sestavení nebo po jejím dokončení. Například můžete spustit *.bat* souborů před spuštěním sestavení nebo zkopírujte nové soubory do složky, po dokončení sestavení. Události sestavení spustit pouze v případě, že se sestavení úspěšně dosáhne těchto bodů v procesu sestavení.

Konkrétní informace o programovacím jazyce, který používáte naleznete v následujících tématech:

- Visual Basic –[postupy: určení události (Visual Basic) sestavení](../ide/how-to-specify-build-events-visual-basic.md).

- C#a F#--[postupy: určení událostí sestavení (C#)](../ide/how-to-specify-build-events-csharp.md).

- Visual C++ –[události sestavení zadejte](/cpp/build/specifying-build-events).

## <a name="syntax"></a>Syntaxe

Události sestavení, postupujte podle stejné syntaxe jako DOS příkazy, ale makra můžete jednoduše vytvořit události sestavení. Seznam dostupných maker naleznete v tématu [dialogové okno Příkazový řádek události před sestavením události/po sestavení](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md).

Nejlepších výsledků dosáhnete postupujte podle těchto formátování tipy:

- Přidat `call` příkaz před všechny události, na kterých běží sestavení *.bat* soubory.

   Příklad: `call C:\MyFile.bat`

   Příklad: `call C:\MyFile.bat call C:\MyFile2.bat`

- Cesty k souborům uzavřete do uvozovek.

   Příklad (pro [!INCLUDE[win8](../debugger/includes/win8_md.md)]): "% ProgramFiles (x86) %\Microsoft SDKs\Windows\v8.0A\Bin\NETFX 4.0 Tools\gacutil.exe"-li "$(TargetPath)"

- Více příkazů oddělte pomocí konců řádků.

- Podle potřeby obsahovat zástupné znaky.

   Příklad: `for %I in (*.txt *.doc *.html) do copy %I c:\` *mydirectory*`\`

  > [!NOTE]
  > `%I` ve výše uvedeném kódu by měla být `%%I` v dávkových skriptů.

## <a name="see-also"></a>Viz také:

- [Kompilace a sestavení](../ide/compiling-and-building-in-visual-studio.md)
- [Dialogové okno Příkazový řádek události/po sestavení události před sestavením](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)
- [Speciální znaky nástroje MSBuild](../msbuild/msbuild-special-characters.md)
- [Návod: Sestavení aplikace](../ide/walkthrough-building-an-application.md)
