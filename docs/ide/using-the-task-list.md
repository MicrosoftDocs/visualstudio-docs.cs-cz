---
title: Použití seznamu úkolů
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: db39850350f99e6c046996f6408973cbc6543868
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75594224"
---
# <a name="use-the-task-list"></a>Použití seznamu úkolů

**Pomocí seznamu úkolů** můžete sledovat komentáře kódu, které používají tokeny, jako `TODO` jsou například a `HACK`, nebo vlastní tokeny a spravovat zkratky, které vás přenesou přímo do předdefinovaného umístění v kódu. Kliknutím na položku v seznamu přejdete na její umístění ve zdrojovém kódu.

> [!NOTE]
> Toto téma platí pro Visual Studio v systému Windows. Visual Studio pro Mac najdete v [tématu Komentáře k úkolům (Visual Studio pro Mac).](/visualstudio/mac/task-comments)

## <a name="the-task-list-window"></a>Okno Seznam úkolů

Když je **seznam úkolů** otevřený, zobrazí se v dolní části okna aplikace.

Chcete-li otevřít **seznam úkolů**, vyberte **možnost Zobrazit** > **seznam úkolů**nebo na klávesnici stiskněte **kombinaci kláves Ctrl**+**\\**,**T**.

![okno Seznam úkolů](../ide/media/vs2015_task_list.png)

Chcete-li změnit pořadí řazení v seznamu, vyberte záhlaví libovolného sloupce. Chcete-li výsledky hledání dále upřesnit, stiskněte **shift** a klepněte na záhlaví druhého sloupce. Případně v místní nabídce zvolte **Seřadit podle**a pak zvolte záhlaví. Chcete-li výsledky hledání dále upřesnit, stiskněte **klávesu Shift** a zvolte druhé záhlaví.

Chcete-li zobrazit nebo skrýt sloupce, zvolte v místní nabídce **možnost Zobrazit sloupce**. Vyberte sloupce, které chcete zobrazit nebo skrýt.

Chcete-li změnit pořadí sloupců, přetáhněte libovolné záhlaví sloupce do požadovaného umístění.

## <a name="user-tasks"></a>Uživatelské úkoly

Funkce úlohy uživatele byla odebrána v sadě Visual Studio 2015. Při otevření řešení, které obsahuje data uživatelských úloh z Visual Studia 2013 a starší, data úlohy uživatele v *souboru .suo* není ovlivněna, ale uživatelské úkoly nejsou zobrazeny v seznamu úkolů.

Pokud chcete pokračovat v přístupu k datům uživatelských úkolů a aktualizovat je, otevřete projekt v sadě Visual Studio 2013 a zkopírujte obsah všech uživatelských úkolů do upřednostňovaného nástroje pro správu projektů (například Team Foundation Server).

## <a name="tokens-and-comments"></a>Tokeny a komentáře

Komentář v kódu, kterému předchází značka komentáře a předdefinovaný token, se zobrazí také v **seznamu úkolů**. Například následující komentář jazyka C# má tři samostatné části:

- Značka komentáře`//`( )

- Token, například`TODO`( )

- Komentář (zbytek textu)

```csharp
// TODO: Load state from previously suspended application
```

Protože `TODO` je předdefinovaný token, tento `TODO` komentář se zobrazí jako úkol v seznamu.

> [!NOTE]
> Výchozí tokeny jsou k dispozici pouze pro jazyky C/C++, C# a VB. Další jazyky najdete v části **Vlastní tokeny.**

### <a name="custom-tokens"></a>Vlastní tokeny

Ve výchozím nastavení obsahuje visual studio `HACK` `TODO`následující `UNDONE`tokeny: , , a `UnresolvedMergeConflict`. Velká a malá písmena se v nich nerozlišují. Nebo lze také vytvořit vlastní tokeny.

Vytvoření vlastního tokenu:

1. V nabídce **Nástroje** zvolte **Možnosti**.

2. Otevřete složku **Prostředí** a zvolte **Seznam úkolů**.

   Zobrazí se [stránka Možností seznamu úkolů.](../ide/reference/task-list-environment-options-dialog-box.md)

   ![Seznam úloh sady Visual Studio](../ide/media/vs2015_task_list_options.png)

3. Do textového pole **Název** zadejte název tokenu, například **BUG**.

4. V rozevíracím seznamu **Priorita** zvolte výchozí prioritu pro nový token.

5. Zvolte **Přidat**.

> [!TIP]
> Po zadání názvu se tlačítko **Přidat** aktivuje. Před klepnutím na tlačítko **Přidat**je je nutné zadat název.

### <a name="c-todo-comments"></a>Komentáře C++ TODO

Ve výchozím nastavení jsou komentáře c++ todo zobrazeny v **seznamu úkolů**.

Chcete-li vypnout komentáře c++ todo, v nabídce **Nástroje** zvolte **Možnosti** > **textového editoru** > **C/C++** > **Zobrazit** > **výčet úkolů komentářů**a nastavte hodnotu na **hodnotu false**.

## <a name="shortcuts"></a>Zástupci

*Zástupce* je záložka v kódu, který je sledován v **seznamu úkolů**. Má jinou ikonu než běžná záložka. Poklepáním na zástupce v **seznamu úkolů** přejděte na odpovídající umístění v kódu.

![Ikona zástupce seznamu úloh sady Visual Studio](../ide/media/vs2015_task_list_bookmark.png)

### <a name="create-a-shortcut"></a>Vytvoření zástupce

Chcete-li vytvořit zástupce, vložte ukazatel do kódu, kam chcete zástupce umístit. Zvolte **Upravit** > **záložky** > **Přidat zástupce seznamu úkolů** nebo stiskněte **Ctrl**+**K**, **Ctrl**+**H**.

Chcete-li procházet zkratkami v kódu, zvolte zástupce v seznamu a pak z místní nabídky zvolte **Další úkol** nebo **Předchozí úkol.**

## <a name="see-also"></a>Viz také

- [Dialogové okno Seznam úkolů, Prostředí, Možnosti](../ide/reference/task-list-environment-options-dialog-box.md)
- [Komentáře k úkolům (Visual Studio pro Mac)](/visualstudio/mac/task-comments)
