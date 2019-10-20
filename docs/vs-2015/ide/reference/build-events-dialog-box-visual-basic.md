---
title: Dialogové okno události sestavení (Visual Basic) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
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
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9fa3b4365f49d172e077ca132b26a49580228c25
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660963"
---
# <a name="build-events-dialog-box-visual-basic"></a>Dialogové okno Události sestavení (Visual Basic)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pomocí dialogového okna **události sestavení** můžete zadat pokyny ke konfiguraci sestavení. Můžete také zadat podmínky, za kterých budou spouštěny události před sestavením nebo po sestavení. Další informace naleznete v tématu [How to: zadat události sestavení (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md).

 **Příkazový řádek události před sestavením** Určuje, které příkazy se mají provést před zahájením sestavení. Chcete-li zadat dlouhé příkazy, klikněte na tlačítko **Upravit před sestavením** a zobrazte tak [dialogové okno Příkazový řádek události před sestavením/po sestavení](../../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md).

> [!NOTE]
> Události před sestavením nejsou spuštěny, pokud je projekt aktuální a není spuštěno žádné sestavení.

 **Příkazový řádek události po sestavení** Určuje všechny příkazy, které mají být provedeny po ukončení sestavení. Chcete-li zadat dlouhé příkazy, klikněte na **Upravit po sestavení** , aby se zobrazilo pole **události před sestavením/po sestavení události d**IALOG.

> [!NOTE]
> Přidejte příkaz `call` před všechny příkazy po sestavení, které spouštějí soubory. bat. Například `call C:\MyFile.bat` nebo `call C:\MyFile.bat call C:\MyFile2.bat`.

 **Spustit událost po sestavení** Určuje podmínky pro spuštění události po sestavení, jak je znázorněno v následující tabulce.

|Možnost|Výsledek|
|------------|------------|
|**Stál**|Událost po sestavení se spustí bez ohledu na to, jestli je sestavení úspěšné.|
|**Po úspěšném sestavení**|Událost po sestavení se spustí, pokud je sestavení úspěšné. Událost se spustí i pro projekt, který je aktuální, pokud je sestavení úspěšné. Toto je výchozí nastavení.|
|**Když sestavení aktualizuje výstup projektu**|Událost po sestavení bude spuštěna pouze v případě, že výstupní soubor kompilátoru (. exe nebo. dll) se liší od předchozího výstupního souboru kompilátoru. Událost po sestavení není spuštěna, pokud je projekt v aktuálním stavu.|

## <a name="see-also"></a>Viz také
 [Stránka Kompilovat, Návrhář projektu (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md) [Postupy: určení událostí sestavení (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md) [dialogových oken události před sestavením/po sestavení události po sestavení](../../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)
