---
title: Stránka události sestavení, Návrhář projektu (C#) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- cs.ProjectPropertiesBuildEvents
helpviewer_keywords:
- build events
- Project Designer, Build Events page
- pre-build events
- post-build events
ms.assetid: 3fff9ae5-213c-46ea-a660-1d70acb6c922
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a310de2e1fd754f16fd701f264f8d5ee8aac4166
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660951"
---
# <a name="build-events-page-project-designer-c"></a>Stránka Události sestavení, návrhář projektu (C#)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pomocí stránky **události sestavení** **Návrháře projektu** můžete zadat pokyny ke konfiguraci sestavení. Můžete také zadat podmínky, za kterých budou spouštěny události po sestavení. Další informace naleznete v tématu [Postupy: určení událostí sestavení (C#)](../../ide/how-to-specify-build-events-csharp.md)a [Postupy: určení událostí sestavení (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md).

## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní
 **Konfigurace** Tento ovládací prvek není na této stránce možné upravovat. Popis tohoto ovládacího prvku naleznete v tématu [Stránka sestavení, Návrhář projektu (C#)](../../ide/reference/build-page-project-designer-csharp.md).

 **Platforma** Tento ovládací prvek není na této stránce možné upravovat. Popis tohoto ovládacího prvku naleznete v tématu [Stránka sestavení, Návrhář projektu (C#)](../../ide/reference/build-page-project-designer-csharp.md).

 **Příkazový řádek události před sestavením** Určuje, které příkazy se mají provést před zahájením sestavení. Chcete-li zadat dlouhé příkazy, klikněte na tlačítko **Upravit před sestavením** a zobrazte tak [dialogové okno Příkazový řádek události před sestavením/po sestavení](../../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md).

> [!NOTE]
> Události před sestavením se nespustí, pokud je projekt aktuální a není spuštěno žádné sestavení.

 **Příkazový řádek události po sestavení** Určuje všechny příkazy, které mají být provedeny po ukončení sestavení. Chcete-li zadat dlouhé příkazy, klikněte na **Upravit po sestavení** , aby se zobrazilo **dialogové okno Příkazový řádek události před sestavením/po sestavení**.

> [!NOTE]
> Přidejte `call` příkaz před všechny příkazy po sestavení, které spouštějí soubory. bat. Příkladem je `call C:\MyFile.bat` nebo `call C:\MyFile.bat call C:\MyFile2.bat`.

 **Spustit událost po sestavení** Určuje následující podmínky pro spuštění události po sestavení, jak je znázorněno v následující tabulce.

|Možnost|Výsledek|
|------------|------------|
|**Vždy**|Událost po sestavení se spustí bez ohledu na to, jestli je sestavení úspěšné.|
|**Po úspěšném sestavení**|Událost po sestavení se spustí, pokud je sestavení úspěšné. Proto se událost spustí i pro projekt, který je aktuální, pokud je sestavení úspěšné.|
|**Když sestavení aktualizuje výstup projektu**|Událost po sestavení se spustí pouze v případě, že výstupní soubor kompilátoru (. exe nebo. dll) je jiný než předchozí výstupní soubor kompilátoru. Proto se událost po sestavení nespustí, pokud je projekt aktuální.|

## <a name="see-also"></a>Viz také
 [Postupy: určení událostí sestavení (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md) [Postupy: určení událostí sestavení (C#)](../../ide/how-to-specify-build-events-csharp.md) [Vlastnosti projektu odkaz](../../ide/reference/project-properties-reference.md) na [kompilaci a sestavení](../../ide/compiling-and-building-in-visual-studio.md)
