---
title: 'Krok 7: Zachovat viditelné páry'
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: 42e1d08c-7b2e-4efd-9f47-85d6206afe35
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eeca594849625b548857a23b9d5c8e278dcdf07c
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579292"
---
# <a name="step-7-keep-pairs-visible"></a>Krok 7: Zachovat viditelné páry
Hra funguje dobře tak dlouho, dokud hráč vybírá pouze dvojice ikon, které neodpovídají. Ale zvažte, co by mělo nastat, pokud hráč vybere shodnou dvojici. Místo toho, aby ikony zmizely zapnutím <xref:System.Windows.Forms.Timer.Start> časovače (pomocí metody), hra by se měla resetovat `firstClicked` tak, aby již nesledovala žádné popisky pomocí referenčních proměnných a `secondClicked` bez resetování barev pro dva štítky, které byly vybrány.

## <a name="to-keep-pairs-visible"></a>Zachování dvojic viditelných

1. Přidejte `if` následující příkaz `label_Click()` k metodě obslužné rutiny události, ke konci kódu těsně nad příkazem, kde spustíte časovač. Při přidávání do programu si kód pořádně prohlédněte. Zamyslete se nad tím, jak kód funguje.

     [!code-csharp[VbExpressTutorial4Step7#9](../ide/codesnippet/CSharp/step-7-keep-pairs-visible_1.cs)]
     [!code-vb[VbExpressTutorial4Step7#9](../ide/codesnippet/VisualBasic/step-7-keep-pairs-visible_1.vb)]

       > [!IMPORTANT]
       > Use the programming language control at the top right of this page to view either the C# code snippet or the Visual Basic code snippet.<br><br>![Programming language control for Docs.Microsoft.com](../ide/media/docs-programming-language-control.png)

     První řádek `if` prohlášení, které jste právě přidali, kontroluje, zda je ikona v prvním štítku, který hráč zvolí, stejná jako ikona v druhém štítku. Pokud jsou ikony identické, program provede tři příkazy mezi složené závorky v `if` jazyce C# nebo tři příkazy v rámci příkazu v jazyce Visual Basic. První dva příkazy `firstClicked` `secondClicked` resetují proměnné a referenční proměnné tak, aby již nesledovaly žádné popisky. (Tyto dva příkazy můžete rozpoznat <xref:System.Windows.Forms.Timer.Tick> z obslužné rutiny události časovače.) Třetí příkaz je `return` příkaz, který říká programu přeskočit zbytek příkazy v metodě bez jejich spuštění.

     Pokud programování v jazyce C#, možná jste si všimli,`=`že některé kód používá`==`jeden znaménko rovná se ( ), zatímco jiné příkazy používají dva rovníznaky ( ). Zvažte, proč `=` se `==` používá v některých místech, ale používá se na jiných místech.

     Toto je typický příklad, který ukazuje rozdíl. Pečlivě se podívejte na kód mezi závorky v příkazu. `if`

    ```vb
    firstClicked.Text = secondClicked.Text
    ```

    ```csharp
    firstClicked.Text == secondClicked.Text
    ```

     Pak se pozorně podívejte na první příkaz `if` v bloku kódu po příkazu.

    ```vb
    firstClicked = Nothing
    ```

    ```csharp
    firstClicked = null;
    ```

     První z těchto dvou příkazů ověří, zda jsou dvě ikony stejné. Vzhledem k tomu, že jsou porovnávány `==` dvě hodnoty, používá program Jazyka C# operátor rovnosti. Druhý příkaz ve skutečnosti změní *assignment*hodnotu `firstClicked` (nazývanou přiřazení ) a nastaví referenční proměnnou rovnou `null` k jeho obnovení. Proto místo toho používá `=` operátor přiřazení. C# `=` používá k nastavení `==` hodnot a jejich porovnání. Visual Basic `=` používá pro přiřazení proměnné a porovnání.

2. Uložte a spusťte program a začněte vybírat ikony ve formuláři. Pokud zvolíte dvojici, která neodpovídá, událost časovače Tick se aktivuje a obě ikony zmizí. Pokud zvolíte odpovídající pár, `if` nový příkaz se spustí a příkaz return způsobí, že metoda přeskočí kód, který spustí časovač, takže ikony zůstanou viditelné, jak je znázorněno na následujícím obrázku.

     ![Hra, kterou vytvoříte v tomto tutoriálu](../ide/media/express_finishedgame.png)<br/>
***Odpovídající hra*** *s viditelnými ikonami párů*

## <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat

- Další krok kurzu najdete v **[tématu Krok 8: Přidání metody k ověření, zda hráč vyhrál](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md)**.

- Chcete-li se vrátit k předchozímu kroku kurzu, [přečtěte si číslo 6: Přidání časovače](../ide/step-6-add-a-timer.md).
