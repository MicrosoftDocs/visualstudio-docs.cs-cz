---
title: Použití seznamu úkolů
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- TaskListWindow
- VS.TaskList
- tasklist
helpviewer_keywords:
- task list
- Visual Studio, task list
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7766a7fd935cc1e1131c4780a5a88ef6fa54e838
ms.sourcegitcommit: bc43970c000f07c9cc2051f1264a9742943a9755
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2018
ms.locfileid: "51349390"
---
# <a name="use-the-task-list"></a>Použití seznamu úkolů

Použít **seznamu úkolů** ke sledování komentářů kódu, které používají tokeny jako `TODO` a `HACK`, nebo vlastní tokeny a ke správě klávesových zkratek, které můžete přejít přímo do předdefinovaného místa v kódu. Klikněte na položku v seznamu a přejděte do umístění ve zdrojovém kódu.

> [!NOTE]
> Toto téma se vztahuje k sadě Visual Studio ve Windows. Visual Studio pro Mac, najdete v části [úkolů komentáře (Visual Studio for Mac)](/visualstudio/mac/task-comments).

## <a name="the-task-list-window"></a>Okno Seznam úkolů

Když **seznamu úkolů** je otevřené, zobrazí se v dolní části okna aplikace.

Chcete-li otevřít **seznamu úkolů**vyberte **zobrazení** > **seznamu úkolů**, nebo stisknutím klávesové **Ctrl** + **\\**,**T**.

![okno Seznam úkolů](../ide/media/vs2015_task_list.png)

Chcete-li změnit pořadí řazení seznamu, vyberte záhlaví libovolného sloupce. Chcete-li dále zpřesnit výsledky hledání, stiskněte **Shift** a klikněte na druhé záhlaví sloupce. Další možností je v místní nabídce zvolit **řadit**a pak kliknout na záhlaví. Chcete-li dále zpřesnit výsledky hledání, stiskněte **Shift** a klikněte na druhé záhlaví.

Chcete-li zobrazit nebo skrýt sloupce, v místní nabídce zvolte **zobrazit sloupce**. Vyberte sloupce, které chcete zobrazit nebo skrýt.

Chcete-li změnit pořadí sloupců, přetáhněte libovolné záhlaví sloupce do umístění, které chcete.

## <a name="user-tasks"></a>Uživatelské úkoly

Funkce úkolů uživatele byla odebrána v sadě Visual Studio 2015. Při otevření řešení, které má uživatelská úloha data ze sady Visual Studio 2013 a dříve uživatel úkolů data ve vašich *.suo* soubor nemá vliv, ale uživatelské úkoly se nezobrazují v seznamu úkolů.

Pokud chcete i nadále přístup a aktualizovat uživatelská data úlohy, otevřete projekt v sadě Visual Studio 2013 a zkopírujte obsah všech úkolů uživatele do vašeho nástroje pro správu upřednostňované projektu (například Team Foundation Server).

## <a name="tokens-and-comments"></a>Tokeny a komentáře

Komentáře v kódu předchází značka komentáře a předdefinovaný token se zobrazí také v **seznamu úkolů**. Například následující komentář jazyka C# má tři samostatné části:

- Značka komentáře (`//`)

- Token, například (`TODO`)

- Komentář (zbytek textu)

```csharp
// TODO: Load state from previously suspended application
```

Protože `TODO` je i předdefinovanou token, tento komentář se zobrazí jako `TODO` úkol v seznamu.

### <a name="custom-tokens"></a>Vlastní tokeny

Ve výchozím nastavení, Visual Studio obsahuje následující tokeny: `HACK`, `TODO`, `UNDONE`, a `UnresolvedMergeConflict`. Nejsou malá a velká písmena. Nebo lze také vytvořit vlastní tokeny.

Vytvoření vlastního tokenu:

1. Na **nástroje** nabídce zvolte **možnosti**.

2. Otevřít **prostředí** složky a klikněte na tlačítko **seznamu úkolů**.

   [Stránky Možnosti seznamu úkolů](../ide/reference/task-list-environment-options-dialog-box.md) se zobrazí.

   ![Seznam úkolů sady Visual Studio](../ide/media/vs2015_task_list_options.png)

3. V **název** textové pole, zadejte název tokenu, například **chyb**.

4. V **Priority** rozevírací seznam, vyberte výchozí prioritu pro nový token.

5. Zvolte **přidat**.

### <a name="c-todo-comments"></a>Komentáře C++ TODO

Ve výchozím nastavení, komentáře C++ TODO se zobrazí v **seznamu úkolů**.

Chcete-li vypnout komentáře C++ TODO na **nástroje** nabídce zvolte **možnosti** > **textový Editor** > **C/C++**  >  **Zobrazení** > **vytvořit výčet úkolů komentáře**a nastavte hodnotu na **false**.

## <a name="shortcuts"></a>Zástupci

A *místní* je záložka v kódu, který je sledována v **seznamu úkolů**. Má jinou ikonu než regulární záložku. Dvakrát klikněte na zástupce v **seznamu úkolů** přejít na příslušné místo v kódu.

![Ikonu zástupce seznamu úkolů sady Visual Studio](../ide/media/vs2015_task_list_bookmark.png)

### <a name="create-a-shortcut"></a>Vytvoření zástupce

Vytvoření zástupce, vložte do kódu, ve které chcete umístit zástupce ukazatel. Zvolte **upravit** > **záložky** > **přidat zástupce seznamu úkolů** nebo stiskněte klávesu **Ctrl** + **K**, **Ctrl**+**H**.

Procházet zástupce v kódu, zvolit zástupce v seznamu a klikněte na tlačítko **dalším úkolem** nebo **předchozího úkolu** z místní nabídky.

## <a name="see-also"></a>Viz také:

- [Úloha seznamu prostředí, dialogové okno Možnosti](../ide/reference/task-list-environment-options-dialog-box.md)
- [Komentáře k úkolu (Visual Studio for Mac)](/visualstudio/mac/task-comments)
