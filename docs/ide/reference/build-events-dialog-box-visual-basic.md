---
title: Dialogové okno Události sestavení (Visual Basic)
description: Přečtěte si, jak můžete pomocí dialogového okna události sestavení zadat pokyny ke konfiguraci sestavení a podmínky, za kterých se spustí nějaké události před sestavením nebo po sestavení.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesBuildEvents
helpviewer_keywords:
- build events
- build events, specifying
- pre-build events
- Build Events dialog box
- post-build events
ms.assetid: 3a81a7c7-39f9-47a8-ba5a-b351227f380e
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 42b7837dd5253d29ecbd0085ae6159a981fcf15c
ms.sourcegitcommit: c9a84e6c01e12ccda9ec7072dd524830007e02a3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2020
ms.locfileid: "92136638"
---
# <a name="build-events-dialog-box-visual-basic"></a>Dialogové okno Události sestavení (Visual Basic)

Pomocí dialogového okna **události sestavení** můžete zadat pokyny ke konfiguraci sestavení. Můžete také zadat podmínky, za kterých budou spouštěny události před sestavením nebo po sestavení. Další informace naleznete v tématu [How to: zadat události sestavení (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md).

**Příkazový řádek události před sestavením**

Určuje, které příkazy se mají provést před zahájením sestavení. Chcete-li zadat dlouhé příkazy, klikněte na tlačítko **Upravit před sestavením** a zobrazte tak [dialogové okno Příkazový řádek události před sestavením/po sestavení](../../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md).

> [!NOTE]
> Události před sestavením nejsou spuštěny, pokud je projekt aktuální a není spuštěno žádné sestavení.

**Příkazový řádek události po sestavení**

Určuje všechny příkazy, které mají být provedeny po ukončení sestavení. Chcete-li zadat dlouhé příkazy, klikněte na **Upravit po sestavení** , aby se zobrazilo dialogové okno **příkazový řádek události před sestavením/po sestavení** .

> [!NOTE]
> Přidejte `call` příkaz před všechny příkazy po sestavení, které spouštějí soubory. bat. Příkladem je `call C:\MyFile.bat` nebo `call C:\MyFile.bat call C:\MyFile2.bat`.

**Spustit událost po sestavení**

Určuje podmínky pro spuštění události po sestavení, jak je znázorněno v následující tabulce.

|Možnost|Výsledek|
|------------|------------|
|**Vždy**|Událost po sestavení se spustí bez ohledu na to, jestli je sestavení úspěšné.|
|**Po úspěšném sestavení**|Událost po sestavení se spustí, pokud je sestavení úspěšné. Událost se spustí i pro projekt, který je aktuální, pokud je sestavení úspěšné. Toto je výchozí nastavení.|
|**Když sestavení aktualizuje výstup projektu**|Událost po sestavení bude spuštěna pouze v případě, že výstupní soubor kompilátoru (. exe nebo. dll) se liší od předchozího výstupního souboru kompilátoru. Událost po sestavení není spuštěna, pokud je projekt v aktuálním stavu.|

## <a name="see-also"></a>Viz také

- [Stránka Kompilovat, návrhář projektu (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md)
- [Postupy: Určení událostí sestavení (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md)
- [Dialogové okno Příkazový řádek události před sestavením/po sestavení](../../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)