---
title: Specifikace vlastních událostí sestavení
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
- build events, customizing
ms.assetid: 69e935a5-e208-4bcd-865c-3e5f9b047ca8
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f2dbb785bcc3092872763d23e968cbf699603286
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53067100"
---
# <a name="specifying-custom-build-events-in-visual-studio"></a>Specifikace vlastních událostí sestavení v sadě Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zadání vlastního sestavení události, můžete automaticky spustit příkazy před zahájením sestavení nebo po jejím dokončení. Můžete třeba spustit soubor BAT před během sestavení spustí nebo zkopírujte nové soubory do složky, po dokončení sestavení. Události sestavení spustit pouze v případě, že se sestavení úspěšně dosáhne těchto bodů v procesu sestavení.

 Konkrétní informace o programovacím jazyce, který používáte naleznete v následujících tématech:

-   Visual Basic –[postupy: určení událostí sestavení (Visual Basic)](../ide/how-to-specify-build-events-visual-basic.md).

-   Vizuální C# a F#--[postupy: určení událostí sestavení (C#)](../ide/how-to-specify-build-events-csharp.md).

-   Visual C++ –[určení událostí sestavení](http://msdn.microsoft.com/library/788a6c18-2dbe-4a49-8cd6-86c1ad7a95cc).

## <a name="syntax"></a>Syntaxe
 Události sestavení, postupujte podle stejné syntaxe jako DOS příkazy, ale makra můžete jednoduše vytvořit události sestavení. Seznam dostupných maker naleznete v tématu [pre-build Event/po sestavení příkazového řádku dialogové okno události](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md).

 Nejlepších výsledků dosáhnete postupujte podle těchto formátování tipy:

-   Přidat `call` spustit příkaz před všechny události sestavení, která soubory .bat.

     Příklad: `call C:\MyFile.bat`

     Příklad: `call C:\MyFile.bat call C:\MyFile2.bat`

-   Cesty k souborům uzavřete do uvozovek.

     Příklad (pro [!INCLUDE[win8](../includes/win8-md.md)]): "% ProgramFiles (x86) %\Microsoft SDKs\Windows\v8.0A\Bin\NETFX 4.0 Tools\gacutil.exe"-li "$(TargetPath)"

-   Více příkazů oddělte pomocí konců řádků.

-   Podle potřeby obsahovat zástupné znaky.

     Příklad: `for %I in (*.txt *.doc *.html) do copy %I c:\` *mydirectory*`\`

    > [!NOTE]
    >  `%I` ve výše uvedeném kódu by měla být `%%I` v dávkových skriptů.

## <a name="see-also"></a>Viz také
 [Kompilování a sestavování](../ide/compiling-and-building-in-visual-studio.md) [dialogové okno Příkazový řádek události/po sestavení události před sestavením](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md) [MSBuild speciálních znaků](../msbuild/msbuild-special-characters.md) [názorný postup: Tvorba aplikace](../ide/walkthrough-building-an-application.md)
