---
title: Seznam úloh, prostředí, dialogové okno Možnosti
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
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
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c152e7a193fff8d444daf86d098681f20a8f5434
ms.sourcegitcommit: 1abb9cf4c3ccb90e3481ea8079272c98aad12875
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/26/2018
ms.locfileid: "50143135"
---
# <a name="task-list-environment-options-dialog-box"></a>Seznam úloh, prostředí, dialogové okno Možnosti

Tato stránka možností umožňuje přidat, odstranit a změnit tokeny komentáře, které generují **seznamu úkolů** připomenutí. Chcete-li zobrazit tato nastavení, vyberte **možnosti** z **nástroje** nabídky, rozbalte **prostředí** složky a zvolte **seznamu úkolů**.

## <a name="task-list-options"></a>Nastavení seznamu úkolů
 Potvrdit odstranění úlohy

 Pokud je vybráno, pokaždé, když se odstranění uživatelského úkolu ze, zobrazí se okno se zprávou **seznamu úkolů**, umožňuje potvrďte odstranění. Ve výchozím nastavení je vybraná tato možnost.

> [!NOTE]
> Odstranit komentář k úkolu, použijte odkaz k nalezení komentář a pak ji odebrat z vašeho kódu.


 Zobrazovat pouze názvy souborů

 Při výběru, **souboru** sloupec **seznamu úkolů** zobrazuje pouze názvy souborů, které mají být upravena, není jejich úplné cesty.

## <a name="tokens"></a>Tokeny
 Když vložíte komentář do svého kódu, jejichž text začíná s tokenem od **seznam tokenů**, **seznamu úkolů** komentáře jako nová položka se zobrazí pokaždé, když je soubor otevřen pro úpravy. Můžete kliknout na to **seznamu úkolů** položky můžete přejít přímo na řádku komentáře v kódu. Další informace najdete v tématu [pomocí seznamu úkolů](../../ide/using-the-task-list.md).

 seznam tokenů

 Zobrazí seznam tokenů a umožňuje přidat nebo odebrat vlastní tokeny. Tokeny komentáře jsou malá a velká písmena v C# a Visual C++, ale ne v jazyce Visual Basic.

> [!NOTE]
> Pokud nezadáte požadovaný token, přesně tak, jak se zobrazuje v **seznam tokenů**, úkolu komentář se nezobrazí v **seznamu úkolů**.


 Priorita

 Nastaví prioritu úlohy, které používají vybraný token. Komentáře k úkolu, které začínají s tímto tokenem jsou automaticky přiřazeny určené priority v **seznamu úkolů**.

 Název

 Zadejte řetězec tokenu. Díky tomu **přidat** tlačítko. Na **přidat**, tento řetězec je součástí **seznam tokenů**, a komentáře, které začínají s tímto názvem se zobrazí v **seznamu úkolů**.

 Přidejte

 Povolený při zadání nového **název**. Klikněte na tlačítko Přidat nový řetězec tokenu pomocí zadaných hodnot **název** a **Priority** pole.

 Odstranit

 Chcete odstranit vybraný token z, klikněte **seznam tokenů**. Nelze odstranit výchozí token komentář.

 Změna

 Kliknutím provést změny existujícího tokenu pomocí zadaných hodnot **název** a **Priority** pole.

> [!NOTE]
> Nelze přejmenovat nebo odstranit výchozí token komentář, ale můžete změnit jeho úroveň priority.


## <a name="see-also"></a>Viz také

- [Používání seznamu úkolů](../../ide/using-the-task-list.md)
- [Nastavení záložek v kódu](../../ide/setting-bookmarks-in-code.md)
- [Prostředí, dialogové okno Možnosti](../../ide/reference/environment-options-dialog-box.md)