---
title: Použití seznamu úkolů
description: Přečtěte si, jak Seznam úkolů v aplikaci Visual Studio může pomáhat sledovat a používat komentáře kódu efektivněji.
ms.date: 10/12/2020
ms.topic: how-to
f1_keywords:
- TaskListWindow
- VS.TaskList
- tasklist
helpviewer_keywords:
- task list
- Visual Studio, task list
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8d19794b4fce3e4a1388f864cecf408e0f7e9c53
ms.sourcegitcommit: b1b747063ce0bba63ad2558fa521b823f952ab51
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/26/2020
ms.locfileid: "96189833"
---
# <a name="use-the-task-list"></a>Použití seznamu úkolů

Použijte **seznam úkolů** ke sledování komentářů kódu, které používají tokeny, jako jsou `TODO` a `HACK` , nebo vlastní tokeny, a ke správě zástupců, které vás přejímají přímo na předdefinované umístění v kódu. Kliknutím na položku v seznamu přejdete do jejího umístění ve zdrojovém kódu.

> [!NOTE]
> Toto téma se týká sady Visual Studio ve Windows. Visual Studio pro Mac najdete v tématu [Komentáře k úkolům (Visual Studio pro Mac)](/visualstudio/mac/task-comments).

## <a name="the-task-list-window"></a>Okno Seznam úkolů

Když je **seznam úkolů** otevřené, zobrazí se v dolní části okna aplikace.

Chcete-li otevřít **seznam úkolů**, vyberte možnost **Zobrazit**  >  **seznam úkolů** nebo na klávesnici stiskněte klávesu **CTRL** + **\\** ,**T**.

![okno Seznam úkolů](../ide/media/vs2015_task_list.png)

Chcete-li změnit pořadí řazení seznamu, vyberte záhlaví libovolného sloupce. Chcete-li dále zpřesnit výsledky hledání, stiskněte klávesu **SHIFT** a klikněte na druhé záhlaví sloupce. Případně můžete v místní nabídce vybrat položku **Seřadit podle** a potom zvolit záhlaví. Chcete-li dále zpřesnit výsledky hledání, stiskněte klávesu **SHIFT** a zvolte druhé záhlaví.

Chcete-li zobrazit nebo skrýt sloupce, v místní nabídce vyberte možnost **Zobrazit sloupce**. Vyberte sloupce, které chcete zobrazit nebo skrýt.

Chcete-li změnit pořadí sloupců, přetáhněte libovolné záhlaví sloupce do umístění, které chcete.

## <a name="user-tasks"></a>Uživatelské úkoly

Funkce úlohy uživatele byla odebrána v aplikaci Visual Studio 2015. Když otevřete řešení, které má data úkolu uživatele z Visual Studio 2013 a dříve, nebudou ovlivněna data uživatelských úloh v souboru *. suo* , ale v seznamu úkolů se nezobrazí úkoly uživatele.

Pokud chcete pokračovat v přístupu a aktualizaci dat uživatelských úloh, otevřete projekt v Visual Studio 2013 a zkopírujte obsah všech uživatelských úloh do preferovaného nástroje pro správu projektu (například Team Foundation Server).

## <a name="tokens-and-comments"></a>Tokeny a komentáře

Komentář v kódu předchází značku komentáře a předdefinovaný token se také zobrazí v **seznam úkolů**. Například následující komentář jazyka C# má tři samostatné části:

- Značka komentáře ( `//` )

- Token, například ( `TODO` )

- Komentář (zbytek textu)

```csharp
// TODO: Load state from previously suspended application
```

Vzhledem k tomu `TODO` , že je předdefinovaný token, tento komentář se zobrazí jako `TODO` úkol v seznamu.

### <a name="custom-tokens"></a>Vlastní tokeny

Ve výchozím nastavení Visual Studio obsahuje následující tokeny: `HACK` , `TODO` , `UNDONE` a `UnresolvedMergeConflict` . Velká a malá písmena se v nich nerozlišují. Nebo lze také vytvořit vlastní tokeny.

> [!NOTE]
> Výchozí tokeny jsou dostupné jenom pro jazyky C/C++, C# a VB. Chcete-li vytvořit vlastní tokeny pro jiné programovací jazyky, použijte následující postup.

Vytvoření vlastního tokenu:

1. V nabídce **nástroje** klikněte na příkaz **Možnosti**.

2. Otevřete složku **prostředí** a zvolte možnost **seznam úkolů**.

   Zobrazí se [Stránka možnosti seznam úkolů](../ide/reference/task-list-environment-options-dialog-box.md) .

   ![Seznam úkolů sady Visual Studio](../ide/media/vs2015_task_list_options.png)

3. Do textového pole **název** zadejte název tokenu, například **Chyba**.

4. V rozevíracím seznamu **Priorita** vyberte výchozí prioritu pro nový token.

5. Klikněte na tlačítko **Přidat**.

> [!TIP]
> Tlačítko **Přidat** se aktivuje po zadání názvu. Před kliknutím na **Přidat** je nutné zadat název.

### <a name="c-todo-comments"></a>Komentáře C++ TODO

Ve výchozím nastavení se komentáře C++ TODO zobrazují v **seznam úkolů**.

Chcete-li vypnout komentáře C++ todo, v nabídce **nástroje** vyberte **možnost možnosti**  >  **textový editor**  >  **C/C++**  >  **Zobrazit**  >  **výčet úkolů komentářů** a nastavte hodnotu na **false**.

## <a name="shortcuts"></a>Zástupci

*Zástupce* je záložka v kódu, která je sledována v **seznam úkolů**. Má jinou ikonu než běžná záložka. Dvojím kliknutím na zástupce v **seznam úkolů** přejděte na odpovídající umístění v kódu.

![Ikona zástupce Seznam úkolů sady Visual Studio](../ide/media/vs2015_task_list_bookmark.png)

### <a name="create-a-shortcut"></a>Vytvoření zástupce

Chcete-li vytvořit zástupce, vložte ukazatel do kódu, kam chcete umístit zástupce. Zvolte možnost **Upravit**  >  **záložky**  >  **Přidat seznam úkolů zástupce** nebo stiskněte klávesy **CTRL** + **K**, **CTRL** + **H**.

Chcete-li procházet zástupce v kódu, zvolte zástupce v seznamu a potom v místní nabídce zvolte možnost **Další úkol** nebo **předchozí úkol** .

## <a name="see-also"></a>Viz také

- [Seznam úkolů, prostředí, dialogové okno Možnosti](../ide/reference/task-list-environment-options-dialog-box.md)
- [Komentáře k úkolu (Visual Studio pro Mac)](/visualstudio/mac/task-comments)
