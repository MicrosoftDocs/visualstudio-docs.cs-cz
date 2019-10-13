---
title: 'Krok 7: Zachování dvojic ve viditelném stavu'
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
ms.openlocfilehash: 025e388185651e6b2effb0f53345f2e145e101b3
ms.sourcegitcommit: a5a54b147e772dc39e519da74ec41a0c25d99628
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2019
ms.locfileid: "72289596"
---
# <a name="step-7-keep-pairs-visible"></a>Krok 7: Zachování dvojic ve viditelném stavu
Hra funguje dobře tak dlouho, dokud hráč vybírá pouze dvojice ikon, které neodpovídají. Ale zvažte, co by mělo nastat, pokud hráč vybere shodnou dvojici. Místo toho, aby se ikony ztratily zapnutím časovače (pomocí metody <xref:System.Windows.Forms.Timer.Start>), by se hra měla resetovat, aby už nesledovala žádné popisky pomocí referenčních proměnných `firstClicked` a `secondClicked`, aniž by se musely resetovat barvy pro tyto dvě zvolené popisky.

## <a name="to-keep-pairs-visible"></a>Zachování dvojic viditelných

1. Přidejte následující příkaz `if` do metody obslužné rutiny události `label_Click()`, poblíž konce kódu těsně nad příkazem, kde spouštíte časovač. Při přidávání do programu si kód pořádně prohlédněte. Zamyslete se nad tím, jak kód funguje.

     [!code-csharp[VbExpressTutorial4Step7#9](../ide/codesnippet/CSharp/step-7-keep-pairs-visible_1.cs)]
     [!code-vb[VbExpressTutorial4Step7#9](../ide/codesnippet/VisualBasic/step-7-keep-pairs-visible_1.vb)]

       > [!IMPORTANT]
       > Use the programming language control at the top right of this page to view either the C# code snippet or the Visual Basic code snippet.<br><br>![Programming language control for Docs.Microsoft.com](../ide/media/docs-programming-language-control.png)

     První řádek příkazu `if`, který jste právě přidali, kontroluje, zda ikona v prvním popisku, kterou hráč zvolí, je stejná jako ikona ve druhém popisku. Pokud jsou ikony stejné, program provede tři příkazy mezi složenou závorkou v C# nebo třemi příkazy v rámci příkazu `if` v Visual Basic. První dva příkazy obnovily referenční proměnné `firstClicked` a `secondClicked`, aby již nesledovaly žádný z popisků. (Tyto dva příkazy můžete rozpoznat z obslužné rutiny události časovače <xref:System.Windows.Forms.Timer.Tick>.) Třetí příkaz je příkaz `return`, který programu instruuje, aby přeskočil zbytek příkazů v metodě bez jejich spuštění.

     Při programování v vizuálu C#jste si všimli, že část kódu používá jediný symbol rovná se (`=`), zatímco jiné příkazy používají dva znaménka rovná se (`==`). Zvažte, proč se na některých místech používá `=`, ale na jiných místech se používá `==`.

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

     První z těchto dvou příkazů ověří, zda jsou dvě ikony stejné. Vzhledem k tomu, že se porovnávají dvě C# hodnoty, použije vizuální program operátor rovnosti `==`. Druhý příkaz skutečně změní hodnotu (označované jako *přiřazení*) a nastaví referenční proměnnou `firstClicked` na hodnotu `null` pro její resetování. To je důvod, proč místo toho používá operátor přiřazení `=`. Vizuál C# používá `=` k nastavení hodnot a `==` pro jejich porovnání. Visual Basic používá pro přiřazování a porovnávání proměnných `=`.

2. Uložte a spusťte program a začněte vybírat ikony ve formuláři. Pokud zvolíte dvojici, která neodpovídá, událost časovače Tick se aktivuje a obě ikony zmizí. Pokud zvolíte odpovídající spárování, nový příkaz `if` se spustí a příkaz return způsobí, že metoda přeskočí kód, který spouští časovač, takže ikony zůstanou viditelné, jak je znázorněno na následujícím obrázku.

     @no__t – 0Game, které vytvoříte v tomto kurzu @ no__t-1<br/>
**Porovnávací hra** s viditelnými páry ikon

## <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat

- Pokud chcete přejít na další krok kurzu, přečtěte si téma [Step 8: Přidejte metodu pro ověření, zda hráč zvítězil na hodnotu @ no__t-0.

- Pokud se chcete vrátit k předchozímu kroku kurzu, přečtěte si @no__t 0Step 6: Přidejte časovač @ no__t-0.
