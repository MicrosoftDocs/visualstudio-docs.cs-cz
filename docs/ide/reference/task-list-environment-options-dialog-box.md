---
title: Seznam úkolů, prostředí, dialogové okno Možnosti
ms.date: 03/28/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Environment.Task_List
- VS.ToolsOptionsPages.Environment.TaskList
- VS.Environment.Task List
helpviewer_keywords:
- Token List
- tokens
- icons, in Task List
- Task List, customizing environment
- Options dialog box, Task List environment
- exclamation points
- comments, comment tasks in Task List
- tokens, and the Task List
- Task List, comment tasks
ms.assetid: 88327e04-fa3e-48db-995b-ad89e0dc4ed2
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e28b3b9c3fe4d6e89228dc18ba8b98aa5e0d2e76
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80233119"
---
# <a name="options-dialog-box-environment--task-list"></a>Dialogové okno Možnosti: prostředí \> seznam úkolů

Tato stránka možností umožňuje přidávat, odstraňovat a měnit tokeny komentářů, které generují **seznam úkolů** připomenutí. Chcete-li zobrazit tato nastavení, vyberte **Možnosti** v nabídce **nástroje** , rozbalte složku **prostředí** a zvolte možnost **seznam úkolů**.

## <a name="task-list-tokens"></a>Tokeny Seznam úkolů

Když vložíte komentář do kódu, jehož text začíná tokenem ze **seznamu tokenu**, **seznam úkolů** zobrazí váš komentář jako novou položku vždy, když je soubor otevřen pro úpravy. Klikněte na položku **seznam úkolů** pro přechod přímo na řádek komentáře ve vašem kódu. Další informace najdete v tématu [použití seznam úkolů](../../ide/using-the-task-list.md).

Seznam tokenů \
Zobrazí seznam tokenů a umožňuje přidat nebo odebrat vlastní tokeny. Tokeny komentáře rozlišují velká a malá písmena v jazycích C# a C++, ale ne v Visual Basic.

> [!NOTE]
> Pokud nechcete požadovaný token zadat přesně tak, jak se zobrazuje v seznamu tokenů, nebude se v **seznam úkolů**zobrazovat úloha s komentářem.

Upřednostněn
Nastaví prioritu úloh, které používají vybraný token (nízká, normální nebo vysoká). K komentářům úlohy začínajícím tímto tokenem se automaticky přiřadí určená priorita v **seznam úkolů**.

Název
Sem zadejte řetězec tokenu a potom kliknutím na **Přidat** přidejte řetězec do seznamu tokenů.

Přidávání
Tato možnost je povolená, když zadáte nový **název**. Kliknutím můžete přidat nový řetězec tokenu s použitím hodnot zadaných do polí **název** a **Priorita** .

Dstranit
Kliknutím odstraníte vybraný token ze seznamu tokenů. Nelze odstranit výchozí token komentáře.

Mění
Kliknutím provedete změny v existujícím tokenu pomocí hodnot zadaných do polí **název** a **Priorita** .

> [!NOTE]
> Výchozí token komentáře nelze přejmenovat ani odstranit, ale můžete změnit jeho úroveň priority.

## <a name="see-also"></a>Viz také

- [Použití seznamu úkolů](../../ide/using-the-task-list.md)
- [Nastavení záložek v kódu](../../ide/setting-bookmarks-in-code.md)
