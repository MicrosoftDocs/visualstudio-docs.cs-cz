---
title: 'Krok 7: zůstat páry viditelné'
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: 42e1d08c-7b2e-4efd-9f47-85d6206afe35
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4d0cab30734aa5411f759e85ef555ecb36f3f0cf
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575150"
---
# <a name="step-7-keep-pairs-visible"></a>Krok 7: zůstat páry viditelné
Hra funguje dobře tak dlouho, dokud hráč vybírá pouze dvojice ikon, které neodpovídají. Ale zvažte, co by mělo nastat, pokud hráč vybere shodnou dvojici. Místo toho, aby se ikony ztratily zapnutím časovače (pomocí <xref:System.Windows.Forms.Timer.Start> metody), by se hra měla resetovat, aby už nesledovala popisky pomocí `firstClicked` a `secondClicked` referenčních proměnných, aniž byste museli resetovat barvy pro tyto dvě. zvolené popisky.

## <a name="to-keep-pairs-visible"></a>Zachování dvojic viditelných

1. Přidejte následující příkaz `if` do metody obslužné rutiny události `label_Click()`, poblíž konce kódu těsně nad příkazem, kde spouštíte časovač. Při přidávání do programu si kód pořádně prohlédněte. Zamyslete se nad tím, jak kód funguje.

     [!code-csharp[VbExpressTutorial4Step7#9](../ide/codesnippet/CSharp/step-7-keep-pairs-visible_1.cs)]
     [!code-vb[VbExpressTutorial4Step7#9](../ide/codesnippet/VisualBasic/step-7-keep-pairs-visible_1.vb)]

       > [!IMPORTANT]
       > Use the programming language control at the top right of this page to view either the C# code snippet or the Visual Basic code snippet.<br><br>![Programming language control for Docs.Microsoft.com](../ide/media/docs-programming-language-control.png)

     První řádek příkazu `if`, který jste právě přidali, kontroluje, zda ikona v prvním popisku, kterou hráč zvolí, je stejná jako ikona ve druhém popisku. Pokud jsou ikony stejné, program provede tři příkazy mezi složenou závorkou v C# nebo třemi příkazy v rámci příkazu `if` v Visual Basic. První dva příkazy obnoví `firstClicked` a `secondClicked` referenční proměnné tak, aby již nesledovaly žádný z popisků. (Tyto dva příkazy můžete rozpoznat z obslužné rutiny události <xref:System.Windows.Forms.Timer.Tick> časovače.) Třetí příkaz je příkaz `return`, který instruuje program, aby přeskočil zbytek příkazů v metodě bez jejich spuštění.

     Při programování v C#nástroji jste si všimli, že část kódu používá jediný symbol rovná se (`=`), zatímco jiné příkazy používají dva symboly rovná se (`==`). Zvažte, proč se na některých místech používá `=`, ale `==` se používá na jiných místech.

     Toto je typický příklad, který ukazuje rozdíl. Pozorně se podívejte na kód mezi závorkami v příkazu `if`.

    ```vb
    firstClicked.Text = secondClicked.Text
    ```

    ```csharp
    firstClicked.Text == secondClicked.Text
    ```

     Pak se pečlivě podívejte na první příkaz v bloku kódu po příkazu `if`.

    ```vb
    firstClicked = Nothing
    ```

    ```csharp
    firstClicked = null;
    ```

     První z těchto dvou příkazů ověří, zda jsou dvě ikony stejné. Vzhledem k tomu, že se porovnávají C# dvě hodnoty, používá program operátor rovnosti `==`. Druhý příkaz skutečně změní hodnotu (označované jako *přiřazení*) a nastaví `firstClicked` referenční proměnnou, která se rovná `null` k jejímu resetování. To je důvod, proč místo toho používá operátor přiřazení `=`. C#používá `=` k nastavení hodnot a `==` k jejich porovnání. Visual Basic používá `=` přiřazování a porovnávání proměnných.

2. Uložte a spusťte program a začněte vybírat ikony ve formuláři. Pokud zvolíte dvojici, která neodpovídá, událost časovače Tick se aktivuje a obě ikony zmizí. Pokud zvolíte odpovídající dvojici, příkaz New `if` se spustí a příkaz return způsobí, že metoda přeskočí kód, který spouští časovač, takže ikony zůstanou viditelné, jak je znázorněno na následujícím obrázku.

     ![Game, které v tomto kurzu vytvoříte ](../ide/media/express_finishedgame.png)<br/>
**Porovnávací hra** s viditelnými páry ikon

## <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat

- Pokud chcete přejít na další krok kurzu, přečtěte si [Krok 8: Přidání metody pro ověření, zda hráč zvítězil](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md).

- Pokud se chcete vrátit k předchozímu kroku kurzu, přečtěte si [Krok 6: Přidání časovače](../ide/step-6-add-a-timer.md).
