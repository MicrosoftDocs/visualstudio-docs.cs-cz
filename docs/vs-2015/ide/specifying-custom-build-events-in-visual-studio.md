---
title: Určení vlastních událostí sestavení
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- build events, customizing
ms.assetid: 69e935a5-e208-4bcd-865c-3e5f9b047ca8
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fabbd4dc42ac4f66c7f53b639c6e7ed1f432878c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667131"
---
# <a name="specifying-custom-build-events-in-visual-studio"></a>Specifikace vlastních událostí sestavení v sadě Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zadáním vlastní události sestavení můžete automaticky spustit příkazy před spuštěním sestavení nebo po jeho dokončení. Například můžete spustit soubor. bat před spuštěním sestavení nebo zkopírovat nové soubory do složky po dokončení sestavení. Události sestavení se spouštějí pouze v případě, že sestavení úspěšně dosáhne těchto bodů v procesu sestavení.

 Konkrétní informace o programovacím jazyce, který používáte, najdete v následujících tématech:

- Visual Basic--[Postupy: určení událostí sestavení (Visual Basic)](../ide/how-to-specify-build-events-visual-basic.md).

- Vizuál C# a F#--[Postupy: určení událostí sestavení (C#)](../ide/how-to-specify-build-events-csharp.md).

- Vizuál C++–[Určení událostí sestavení](https://msdn.microsoft.com/library/788a6c18-2dbe-4a49-8cd6-86c1ad7a95cc)

## <a name="syntax"></a>Syntaxe
 Události sestavení následují stejnou syntaxi jako příkazy pro systém DOS, ale makra můžete použít k jednoduššímu vytváření událostí sestavení. Seznam dostupných maker naleznete v tématu [dialogové okno Příkazový řádek události před sestavením/po sestavení](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md).

 Nejlepších výsledků dosáhnete pomocí těchto tipů pro formátování:

- Před všemi událostmi sestavení, které spouštějí soubory. bat, přidejte příkaz `call`.

     Příklad: `call C:\MyFile.bat`

     Příklad: `call C:\MyFile.bat call C:\MyFile2.bat`

- Uzavřete cesty k souborům do uvozovek.

     Příklad (pro [!INCLUDE[win8](../includes/win8-md.md)]): "% ProgramFiles (x86)% \ Microsoft SDKs\Windows\v8.0A\Bin\NETFX 4,0 Tools\gacutil.exe"-If "$ (TargetPath)"

- Oddělte více příkazů pomocí konců řádků.

- Podle potřeby zahrňte zástupné znaky.

     Příklad: `for %I in (*.txt *.doc *.html) do copy %I c:\`*mydirectory* `\`

    > [!NOTE]
    > `%I` ve výše uvedeném kódu by se měly `%%I` v dávkových skriptech.

## <a name="see-also"></a>Viz také
 Návod k sestavování [a](../ide/compiling-and-building-in-visual-studio.md) sestavování událostí [před sestavením/po sestavení v příkazovém řádku](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md) nástroje [MSBuild speciální znaky](../msbuild/msbuild-special-characters.md) [: sestavování aplikace](../ide/walkthrough-building-an-application.md)
