---
title: Použití Seznam úkolů | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- TaskListWindow
- VS.TaskList
- tasklist
helpviewer_keywords:
- task list
- Visual Studio, task list
ms.assetid: f46a75a8-47b3-4cb6-bb59-b72e3356a664
caps.latest.revision: 33
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f7537c3007f54480874047f52f186996cf663508
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656406"
---
# <a name="using-the-task-list"></a>Používání seznamu úkolů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Použijte **seznam úkolů** ke sledování komentářů kódu, které používají tokeny, jako jsou `TODO` a `HACK` nebo vlastní tokeny, a ke správě zástupců, které vás přesměrují přímo na předdefinované umístění v kódu. Kliknutím na položku v seznamu přejdete do jejího umístění ve zdrojovém kódu.

 V tomto tématu:

- [Okno Seznam úkolů](../ide/using-the-task-list.md#taskListWindow)

- [Uživatelské úkoly](../ide/using-the-task-list.md#userTasks)

- [Tokeny a komentáře](../ide/using-the-task-list.md#tokensComments)

- [Vlastní tokeny](../ide/using-the-task-list.md#customTokens)

- [C++Komentáře TODO](../ide/using-the-task-list.md#cppComments)

- [Odkazy](../ide/using-the-task-list.md#shortcuts)

## <a name="taskListWindow"></a>Okno Seznam úkolů
 Když je **seznam úkolů** otevřené, zobrazí se v dolní části okna aplikace.

#### <a name="to-open-the-task-list"></a>Otevření seznamu úkolů

- V nabídce **zobrazení** vyberte položku **seznam úkolů** (klávesnice: CTRL + \\, t).

     ![Seznam úkolů okno](../ide/media/vs2015-task-list.png "vs2015_task_list")

#### <a name="to-change-the-sort-order-of-the-list"></a>Změna pořadí řazení seznamu

- Klikněte na záhlaví libovolného sloupce. Chcete-li dále zpřesnit výsledky hledání, stiskněte klávesu Shift a klikněte na druhé záhlaví sloupce.

     Jako alternativu v místní nabídce vyberte položku **Seřadit podle**a vyberte záhlaví. Chcete-li dále zpřesnit výsledky hledání, stiskněte klávesu Shift a klikněte na druhé záhlaví.

#### <a name="to-show-or-hide-columns"></a>Zobrazení nebo skrytí sloupců

- V místní nabídce vyberte možnost **Zobrazit sloupce**. Vyberte sloupce, které chcete zobrazit nebo skrýt.

#### <a name="to-change-the-order-of-the-columns"></a>Změna pořadí sloupců

- Přetáhněte libovolné záhlaví sloupce do požadovaného umístění.

## <a name="userTasks"></a>Uživatelské úkoly
 Funkce úlohy uživatele byla v aplikaci Visual Studio 2015 odebrána. Když otevřete řešení, které má data úkolu uživatele od Visual Studio 2013 a starších verzí v aplikaci Visual Studio 2015, nebudou ovlivněna data uživatelských úloh v souboru. suo, ale v seznamu úkolů nebudou zobrazeny úkoly uživatele.

 Pokud chcete pokračovat v přístupu k datům uživatelských úloh a aktualizovat je, měli byste projekt otevřít v Visual Studio 2013 a kopírovat obsah všech uživatelských úloh do vašeho preferovaného nástroje pro správu projektu (například Team Foundation Server).

## <a name="tokensComments"></a>Tokeny a komentáře
 Komentář v kódu předchází značku komentáře a předdefinovaný token se zobrazí také v okně **seznam úkolů** . Například následující komentář jazyka C# má tři samostatné části:

- Značka komentáře (`//`)

- Token, například (`TODO`)

- Komentář (zbytek textu)

```
// TODO: Load state from previously suspended application
```

 Vzhledem k tomu, že `TODO` je předdefinovaný token, tento komentář se zobrazí jako úloha `TODO` v seznamu.

### <a name="customTokens"></a>Vlastní tokeny
 Ve výchozím nastavení Visual Studio zahrnuje následující tokeny: NAPADENí, TODO, VRÁCENo, Poznámka. Nerozlišují se malá a velká písmena.

 Nebo lze také vytvořit vlastní tokeny.

##### <a name="to-create-a-custom-token"></a>Vytvoření vlastního tokenu

1. V nabídce **nástroje** klikněte na příkaz **Možnosti**.

2. Otevřete složku **prostředí** a zvolte možnost **seznam úkolů**.

     Zobrazí se [dialogové okno seznam úkolů, prostředí, možnosti](../ide/reference/task-list-environment-options-dialog-box.md) .

     ![Seznam úkolů sady Visual Studio](../ide/media/vs2015-task-list-options.png "vs2015_task_list_options")

3. V kategorii **tokeny** zadejte do textového pole **název** svůj název tokenu, například "Chyba".

4. V rozevíracím seznamu **Priorita** vyberte výchozí prioritu pro nový token. Klikněte na tlačítko **Přidat** .

### <a name="cppComments"></a>C++ Komentáře todo
 Ve výchozím nastavení C++ se komentáře TODO zobrazují v okně **seznam úkolů** . Toto chování můžete změnit.

##### <a name="to-turn-off-c-todo-comments"></a>Vypnutí komentářů C++ todo

1. V nabídce **nástroje** přejděte do části **možnosti &#124; textový &#124; Editor CC++ &#124; /zobrazit &#124; výčet úkolů komentářů** a nastavte hodnotu na false.

2. V dialogovém okně **Možnosti** otevřete **textový editor**.

3. V části **CC++/** zvolte možnost **zobrazení**a pak nastavte možnost zobrazit **výčet úkolů komentáře** na **hodnotu NEPRAVDA**.

## <a name="shortcuts"></a>Odkazy
 *Zástupce* je záložka v kódu, který je sledován v **seznam úkolů**; má jinou ikonu než běžná záložka. Dvojím kliknutím na zástupce v **seznam úkolů** přejděte na příslušné umístění v kódu.

 ![Ikona zástupce Seznam úkolů sady Visual Studio](../ide/media/vs2015-task-list-bookmark.png "vs2015_task_list_bookmark")

#### <a name="to-create-a-shortcut"></a>Vytvoření zástupce

- Umístěte ukazatel myši do kódu tam, kde chcete zástupce vložit. Zvolte **Upravit &#124; záložky &#124; přidat seznam úkolů zástupce** nebo stiskněte klávesu (klávesnice: CTRL + K, CTRL + H).

     Chcete-li procházet zástupce v kódu, zvolte zástupce v seznamu a potom v místní nabídce zvolte možnost **Další úkol** nebo **předchozí úkol** .

## <a name="see-also"></a>Viz také
 [Seznam úkolů, Prostředí, dialogové okno Možnosti](../ide/reference/task-list-environment-options-dialog-box.md)
