---
title: Seznam úkolů, prostředí, dialogové okno Možnosti | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Environment.Task_List
- VS.ToolsOptionsPag.Environment.Task_List
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
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 72e5f82fa3ca4b7ca909ee07e5b77a31b3e20879
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650964"
---
# <a name="task-list-environment-options-dialog-box"></a>Seznam úkolů, prostředí, dialogové okno Možnosti
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Tato stránka možností umožňuje přidávat, odstraňovat a měnit tokeny komentářů, které generují **seznam úkolů** připomenutí. Chcete-li zobrazit tato nastavení, vyberte **Možnosti** v nabídce **nástroje** , rozbalte složku **prostředí** a zvolte možnost **seznam úkolů**.

## <a name="task-list-options"></a>Možnosti Seznam úkolů
 Potvrďte odstranění úkolů, pokud je vybraná možnost, zobrazí se okno se zprávou pokaždé, když se z **seznam úkolů**odstraní úkol uživatele, což vám umožní potvrzení odstranění. Tato možnost je vybrána ve výchozím nastavení.

> [!NOTE]
> Chcete-li odstranit komentář úkolu, použijte odkaz k vyhledání komentáře a jeho odebrání z kódu.

 Zobrazit názvy souborů pouze v případě, že je vybrána, sloupec **soubor** v **seznam úkolů** zobrazí pouze názvy souborů, které mají být upraveny, nikoli jejich úplné cesty.

## <a name="tokens"></a>Tokeny
 Když vložíte komentář do kódu, jehož text začíná tokenem ze **seznamu tokenu**, **seznam úkolů** zobrazí váš komentář jako novou položku vždy, když se soubor otevře pro úpravy. Kliknutím na tuto položku **seznam úkolů** můžete přejít přímo k řádku komentáře ve vašem kódu. Další informace najdete v tématu [použití seznam úkolů](../../ide/using-the-task-list.md).

 Seznam tokenů zobrazuje seznam tokenů a umožňuje přidat nebo odebrat vlastní tokeny. Tokeny komentáře rozlišují velká a malá C# písmena v C++vizuálech a vizuálů, ale ne v Visual Basic.

> [!NOTE]
> Pokud nechcete požadovaný token zadat přesně tak, jak se zobrazuje v **seznamu tokenů**, nebude se v **seznam úkolů**zobrazovat úloha s komentářem.

 Priorita nastaví prioritu úloh, které používají vybraný token. K komentářům úlohy začínajícím tímto tokenem se automaticky přiřadí určená priorita v **seznam úkolů**.

 Název zadejte řetězec tokenu. Tím povolíte tlačítko **Přidat** . Při **Přidání**je tento řetězec obsažen v **seznamu tokenů**a komentáře začínající tímto názvem budou zobrazeny v **seznam úkolů**.

 Přidejte povoleno, když zadáte nový **název**. Kliknutím můžete přidat nový řetězec tokenu s použitím hodnot zadaných do polí **název** a **Priorita** .

 Odstranit kliknutím odstraníte vybraný token ze **seznamu tokenů**. Nelze odstranit výchozí token komentáře.

 Změňte kliknutím na změny v existujícím tokenu pomocí hodnot zadaných do polí **název** a **Priorita** .

> [!NOTE]
> Výchozí token komentáře nelze přejmenovat ani odstranit, ale můžete změnit jeho úroveň priority.

## <a name="see-also"></a>Viz také
 [Použití seznam úkolů](../../ide/using-the-task-list.md) [Nastavení záložek v](../../ide/setting-bookmarks-in-code.md) části [možnosti prostředí kódu – dialogové okno](../../ide/reference/environment-options-dialog-box.md)
