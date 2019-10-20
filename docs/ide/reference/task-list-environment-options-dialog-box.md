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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f2d0ba45ffea940ddb57a6da1e6df55e3da8867b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72644864"
---
# <a name="options-dialog-box-environment--task-list"></a>Dialogové okno Možnosti: prostředí \> Seznam úkolů

Tato stránka možností umožňuje přidávat, odstraňovat a měnit tokeny komentářů, které generují **seznam úkolů** připomenutí. Chcete-li zobrazit tato nastavení, vyberte **Možnosti** v nabídce **nástroje** , rozbalte složku **prostředí** a zvolte možnost **seznam úkolů**.

## <a name="task-list-tokens"></a>Tokeny Seznam úkolů

Když vložíte komentář do kódu, jehož text začíná tokenem ze **seznamu tokenu**, **seznam úkolů** zobrazí váš komentář jako novou položku vždy, když je soubor otevřen pro úpravy. Klikněte na položku **seznam úkolů** pro přechod přímo na řádek komentáře ve vašem kódu. Další informace najdete v tématu [použití seznam úkolů](../../ide/using-the-task-list.md).

Seznam tokenů \
Zobrazí seznam tokenů a umožňuje přidat nebo odebrat vlastní tokeny. Tokeny komentáře rozlišují velká a C# malá C++písmena v a, ale ne v Visual Basic.

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

## <a name="see-also"></a>Viz také:

- [Použití seznamu úloh](../../ide/using-the-task-list.md)
- [N záložky v kódu](../../ide/setting-bookmarks-in-code.md)