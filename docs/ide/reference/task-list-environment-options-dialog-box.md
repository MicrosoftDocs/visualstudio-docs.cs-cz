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
ms.sourcegitcommit: eeff6f675e7850e718911647343c5df642063d5e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2020
ms.locfileid: "80233119"
---
# <a name="options-dialog-box-environment--task-list"></a>Dialogové okno Možnosti: Seznam úkolů prostředí \>

Tato stránka možností umožňuje přidávat, odstraňovat a měnit tokeny poznámek, které generují připomenutí **seznamu úkolů.** Chcete-li tato nastavení zobrazit, vyberte **možnosti** z nabídky **Nástroje,** rozbalte složku **Prostředí** a zvolte **Seznam úkolů**.

## <a name="task-list-tokens"></a>Tokeny seznamu úkolů

Když vložíte komentář do kódu, jehož text začíná tokenem ze **seznamu tokenů**, **seznam úkolů** zobrazí váš komentář jako novou položku při každém otevření souboru pro úpravy. Kliknutím na položku **Seznam úkolů** přejdete přímo na řádek komentáře v kódu. Další informace naleznete [v tématu Použití seznamu úkolů](../../ide/using-the-task-list.md).

Seznam tokenů\
Zobrazí seznam tokenů a umožňuje přidat nebo odebrat vlastní tokeny. Tokeny poznámek rozlišují v jazyce C# a C++, ale ne v jazyce Visual Basic.

> [!NOTE]
> Pokud nezadáte požadovaný token přesně tak, jak je uveden v seznamu tokenů, úloha komentáře se v **seznamu úkolů**nezobrazí .

Priorita\
Nastaví prioritu úkolů, které používají vybraný token (nízká, normální nebo vysoká). Komentáře úkolů, které začínají tímto tokenem, jsou automaticky přiřazeny určené priority v **seznamu úkolů**.

Název\
Sem zadejte řetězec tokenu a kliknutím na **Přidat** přidejte řetězec do seznamu tokenů.

Přidat\
Povoleno při zadání nového **názvu**. Klepnutím přidáte nový řetězec tokenu pomocí hodnot zadaných do polí **Název** a **Priorita.**

Odstranit\
Klepnutím odstraníte vybraný token ze seznamu tokenů. Výchozí token komentáře nelze odstranit.

Změnit\
Klepnutím provedete změny existujícího tokenu pomocí hodnot zadaných v polích **Název** a **Priorita.**

> [!NOTE]
> Výchozí token komentáře nelze přejmenovat ani odstranit, ale můžete změnit jeho úroveň priority.

## <a name="see-also"></a>Viz také

- [Použití seznamu úloh](../../ide/using-the-task-list.md)
- [Nastavení záložek v kódu](../../ide/setting-bookmarks-in-code.md)
