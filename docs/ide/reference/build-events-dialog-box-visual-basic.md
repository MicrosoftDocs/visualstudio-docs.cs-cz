---
title: Dialogové okno Události sestavení (Visual Basic)
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
ms.openlocfilehash: bb4cd0a46e5ab4cc9c3a9e00773818d536b84891
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "68461439"
---
# <a name="build-events-dialog-box-visual-basic"></a>Dialogové okno Události sestavení (Visual Basic)

Dialogové okno **Události sestavení** slouží k určení pokynů konfigurace sestavení. Můžete také určit podmínky, za kterých jsou spuštěny všechny události před sestavením nebo po sestavení. Další informace naleznete v [tématu How to: Specify Build Events (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md).

**Příkazový řádek události před sestavením**

Určuje všechny příkazy, které mají být provedeny před spuštěním sestavení. Chcete-li zadat dlouhé příkazy, klepněte na **tlačítko Upravit předsestavení,** [chcete-li zobrazit dialogové okno příkazového řádku události před sestavením nebo po sestavení](../../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md).

> [!NOTE]
> Události předběžného sestavení se nespustí, pokud je projekt aktuální a neaktivuje se žádné sestavení.

**Příkazový řádek události po sestavení**

Určuje všechny příkazy, které mají být provedeny po ukončení sestavení. Chcete-li psát dlouhé příkazy, klepněte na **tlačítko Upravit po sestavení** a zobrazte dialogové okno **Příkazový řádek události před sestavením** nebo po sestavení.

> [!NOTE]
> Přidejte `call` příkaz před všechny příkazy po sestavení, které spouštějí soubory BAT. Příkladem je `call C:\MyFile.bat` nebo `call C:\MyFile.bat call C:\MyFile2.bat`.

**Spuštění události po sestavení**

Určuje podmínky pro spuštění události po sestavení, jak je znázorněno v následující tabulce.

|Možnost|Výsledek|
|------------|------------|
|**Vždy**|Po sestavení události se spustí, bez ohledu na to, zda sestavení úspěšné.|
|**Na úspěšné sestavení**|Událost po sestavení se spustí, pokud je sestavení úspěšné. Událost bude spuštěna i pro projekt, který je aktuální, pokud sestavení proběhne úspěšně. Toto je výchozí nastavení.|
|**Když sestavení aktualizuje výstup projektu**|Událost po sestavení bude spuštěna pouze v případě, že se výstupní soubor kompilátoru (.exe nebo .dll) liší od předchozího výstupního souboru kompilátoru. Událost po sestavení není spuštěna, pokud je projekt aktuální.|

## <a name="see-also"></a>Viz také

- [Stránka Kompilovat, návrhář projektu (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md)
- [Postupy: Určení událostí sestavení (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md)
- [Dialogové okno Příkazového řádku události před sestavením události/po sestavení](../../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)