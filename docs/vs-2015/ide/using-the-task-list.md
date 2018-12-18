---
title: Pomocí seznamu úkolů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- TaskListWindow
- VS.TaskList
- tasklist
helpviewer_keywords:
- task list
- Visual Studio, task list
ms.assetid: f46a75a8-47b3-4cb6-bb59-b72e3356a664
caps.latest.revision: 33
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d5662aebeb0e7b8da36c52c0c9fd727c860a4221
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49172026"
---
# <a name="using-the-task-list"></a>Používání seznamu úloh
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Použít **seznamu úkolů** ke sledování komentářů kódu, které používají tokeny jako `TODO` a `HACK`, nebo vlastní tokeny a ke správě klávesových zkratek, které se dostanete přímo do předdefinovaného místa v kódu. Klikněte na položku v seznamu a přejděte do umístění ve zdrojovém kódu.  
  
 V tomto tématu:  
  
-   [Okno seznam úkolů](../ide/using-the-task-list.md#taskListWindow)  
  
-   [Uživatelské úkoly](../ide/using-the-task-list.md#userTasks)  
  
-   [Tokeny a komentáře](../ide/using-the-task-list.md#tokensComments)  
  
-   [Vlastní tokeny](../ide/using-the-task-list.md#customTokens)  
  
-   [Komentáře C++ TODO](../ide/using-the-task-list.md#cppComments)  
  
-   [Klávesové zkratky](../ide/using-the-task-list.md#shortcuts)  
  
##  <a name="taskListWindow"></a> Okno seznam úkolů  
 Když **seznamu úkolů** je otevřené, zobrazí se v dolní části okna aplikace.  
  
#### <a name="to-open-the-task-list"></a>Otevření seznamu úkolů  
  
-   Na **zobrazení** nabídce zvolte **seznamu úkolů** (klávesnice: Ctrl +\\, T).  
  
     ![Okno seznam úkolů](../ide/media/vs2015-task-list.png "vs2015_task_list")  
  
#### <a name="to-change-the-sort-order-of-the-list"></a>Změna pořadí řazení seznamu  
  
-   Klikněte na záhlaví libovolného sloupce. Chcete-li dále zpřesnit výsledky hledání, stiskněte klávesu Shift a klikněte na druhé záhlaví sloupce.  
  
     Jako alternativu v místní nabídce zvolte **řadit**a kliknout na záhlaví. Chcete-li dále zpřesnit výsledky hledání, stiskněte klávesu Shift a klikněte na druhé záhlaví.  
  
#### <a name="to-show-or-hide-columns"></a>Zobrazení nebo skrytí sloupců  
  
-   V místní nabídce zvolte **zobrazit sloupce**. Vyberte sloupce, které chcete zobrazit nebo skrýt.  
  
#### <a name="to-change-the-order-of-the-columns"></a>Změna pořadí sloupců  
  
-   Přetáhněte libovolné záhlaví sloupce do požadovaného umístění.  
  
##  <a name="userTasks"></a> Uživatelské úkoly  
 Odebrali jsme funkci úkolů uživatele v sadě Visual Studio 2015. Když otevřete řešení, které má úloha uživatelská data z aplikace Visual Studio 2013 a dříve v sadě Visual Studio 2015, nebude mít vliv údaje úkolu v souboru .suo, ale uživatelské úkoly se nezobrazí v seznamu úkolů.  
  
 Pokud chcete dál používat a aktualizovat uživatelská data úlohy, by měl projekt otevřít v sadě Visual Studio 2013 a zkopírujte obsah všech úkolů uživatele do vašeho nástroje pro správu upřednostňované projektu (například Team Foundation Server).  
  
##  <a name="tokensComments"></a> Tokeny a komentáře  
 Komentáře v kódu předchází značka komentáře a předdefinovaný token se zobrazí také v **seznamu úkolů** okna. Například následující komentář jazyka C# má tři samostatné části:  
  
-   Značka komentáře (`//`)  
  
-   Token, například (`TODO`)  
  
-   Komentář (zbytek textu)  
  
```  
// TODO: Load state from previously suspended application  
```  
  
 Protože `TODO` je i předdefinovanou token, tento komentář se zobrazí jako `TODO` úkol v seznamu.  
  
###  <a name="customTokens"></a> Vlastní tokeny  
 Ve výchozím nastavení, Visual Studio obsahuje následující tokeny: TODO, HACK VRÁCENO, Poznámka. Ty nejsou velká a malá písmena.  
  
 Nebo lze také vytvořit vlastní tokeny.  
  
##### <a name="to-create-a-custom-token"></a>Vytvoření vlastního tokenu  
  
1.  Na **nástroje** nabídce zvolte **možnosti**.  
  
2.  Otevřít **prostředí** složky a klikněte na tlačítko **seznamu úkolů**.  
  
     [Seznamu úloh, prostředí, dialogové okno Možnosti](../ide/reference/task-list-environment-options-dialog-box.md) se zobrazí.  
  
     ![Seznam úkolů sady Visual Studio](../ide/media/vs2015-task-list-options.png "vs2015_task_list_options")  
  
3.  V **tokeny** kategorie v **název** textového pole zadejte název tokenu, například "Chyba".  
  
4.  V **Priority** rozevírací seznam, vyberte výchozí prioritu pro nový token. Zvolte **přidat** tlačítko.  
  
###  <a name="cppComments"></a> Komentáře C++ TODO  
 Ve výchozím nastavení, komentáře C++ TODO se zobrazí v **seznamu úkolů** okna. Toto chování můžete změnit.  
  
##### <a name="to-turn-off-c-todo-comments"></a>Chcete-li vypnout komentáře C++ TODO  
  
1.  Na **nástroje** nabídky, přejděte na **možnosti &#124; textový Editor &#124; C/C++ &#124; zobrazení &#124; vytvořit výčet úkolů komentáře** a hodnotu nastavte na hodnotu false.  
  
2.  V **možnosti** dialogovém okně Otevřít **textový Editor**.  
  
3.  V části **C/C++**, zvolte **zobrazení**a potom nastavte **vytvořit výčet úkolů komentáře** k **False**.  
  
##  <a name="shortcuts"></a> Klávesové zkratky  
 A *místní* je záložka v kódu, který je sledována v **seznamu úkolů**; má jinou ikonu než regulární záložku. Dvakrát klikněte na zástupce v **seznamu úkolů** přejít na příslušné místo v kódu.  
  
 ![Ikonu zástupce seznamu úkolů sady Visual Studio](../ide/media/vs2015-task-list-bookmark.png "vs2015_task_list_bookmark")  
  
#### <a name="to-create-a-shortcut"></a>Vytvoření zástupce  
  
-   Umístěte ukazatel myši do kódu tam, kde chcete zástupce vložit. Zvolte **upravit &#124; záložky &#124; přidat zástupce seznamu úkolů** nebo stiskněte klávesu (klávesnice: Ctrl + K, Ctrl + H).  
  
     Procházet zástupce v kódu, zvolit zástupce v seznamu a klikněte na tlačítko **dalším úkolem** nebo **předchozího úkolu** z místní nabídky.  
  
## <a name="see-also"></a>Viz také  
 [Seznam úkolů, Prostředí, dialogové okno Možnosti](../ide/reference/task-list-environment-options-dialog-box.md)



