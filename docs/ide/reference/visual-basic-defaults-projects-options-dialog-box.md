---
title: Výchozí možnosti jazyka Visual Basic, projekty, dialogové okno Možnosti
description: Naučte se používat stránku výchozích hodnot Visual Basic v části projekty a řešení k určení výchozího nastavení pro Visual Basic možnosti projektu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Projects.VBDefaults
helpviewer_keywords:
- Option Explicit statement, setting in the IDE
- Option Compare statement, setting in the IDE
- Option Strict statement, setting in the IDE
ms.assetid: 2465cd9d-18b6-4c4a-b1ea-86dbab23fc79
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3de415f99dbb9a91f2fa0e30ffc5e40727d10303
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99889743"
---
# <a name="visual-basic-defaults-projects-options-dialog-box"></a>Výchozí možnosti jazyka Visual Basic, projekty, dialogové okno Možnosti
Určuje výchozí nastavení pro Visual Basic možnosti projektu. Při vytvoření nového projektu budou zadané příkazy Option přidány do záhlaví projektu v editoru kódu. Možnosti platí pro všechny projekty Visual Basic.

Chcete-li získat přístup k tomuto dialogovému oknu, v nabídce **nástroje** klikněte na položku **Možnosti**, rozbalte složku **projekty a řešení** a potom klikněte na položku **výchozí hodnoty VB**.

 **Možnost Explicit**

Nastaví výchozí kompilátor tak, aby se vyžadovaly explicitní deklarace proměnných. Ve výchozím nastavení je **možnost explicitně** nastavená na hodnotu **zapnuto**. Další informace najdete v tématu [/OptionExplicit](/dotnet/visual-basic/reference/command-line-compiler/optionexplicit).

 **Možnost Strict**

Nastaví výchozí kompilátor tak, aby byly vyžadovány explicitní zužující převody a pozdní vazba není povolena. Ve výchozím nastavení je **možnost Option Strict** nastavená na **off (vypnuto**). Další informace najdete v tématu [/OptionStrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict).

 **Možnost Compare**

Nastaví výchozí kompilátor pro porovnávání řetězců: binární (rozlišuje velká a malá písmena) nebo text (bez rozlišení velkých a malých písmen). Ve výchozím nastavení je **možnost Compare** nastavena na hodnotu **Binary**. Další informace najdete v tématu [/OptionCompare](/dotnet/visual-basic/reference/command-line-compiler/optioncompare).

 **Odvoditelné možnosti**

Nastaví výchozí kompilátor pro odvození lokálního typu. Ve výchozím nastavení je **možnost odvozování** u nově vytvořených projektů **a u migrovaných** projektů vytvořených v dřívějších verzích Visual Basic nastavena na hodnotu **zapnuto** . Další informace najdete v tématu [/optioninfer](/dotnet/visual-basic/reference/command-line-compiler/optioninfer).

## <a name="see-also"></a>Viz také

- [Řešení a projekty](../../ide/solutions-and-projects-in-visual-studio.md)
