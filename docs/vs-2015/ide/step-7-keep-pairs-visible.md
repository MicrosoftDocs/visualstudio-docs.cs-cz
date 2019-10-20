---
title: 'Krok 7: zachovat viditelné páry | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 42e1d08c-7b2e-4efd-9f47-85d6206afe35
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d7981ca81839cc8d0959cf5ae75c6d9a001d39a9
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72646949"
---
# <a name="step-7-keep-pairs-visible"></a>Krok 7: Uchovejte páry ve viditelném stavu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Hra funguje dobře tak dlouho, dokud hráč vybírá pouze dvojice ikon, které neodpovídají. Ale zvažte, co by mělo nastat, pokud hráč vybere shodnou dvojici. Místo toho, aby se ikony ztratily zapnutím časovače (pomocí `Start()` metody), by se hra měla resetovat, aby už nesledovala popisky pomocí `firstClicked` a `secondClicked` referenčních proměnných, aniž byste museli resetovat barvy pro tyto dvě. zvolené popisky.

### <a name="to-keep-pairs-visible"></a>Zachování dvojic viditelných

1. Přidejte následující příkaz `if` do metody obslužné rutiny události `label_Click()`, poblíž konce kódu těsně nad příkazem, kde spouštíte časovač. Při přidávání do programu si kód pořádně prohlédněte. Zamyslete se nad tím, jak kód funguje.

     [!code-csharp[VbExpressTutorial4Step7#9](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step7/cs/form1.cs#9)]
     [!code-vb[VbExpressTutorial4Step7#9](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step7/vb/form1.vb#9)]

     První řádek příkazu `if`, který jste právě přidali, kontroluje, zda ikona v prvním popisku, kterou hráč zvolí, je stejná jako ikona ve druhém popisku. Pokud jsou ikony stejné, program provede tři příkazy mezi složenou závorkou v C# nebo třemi příkazy v rámci příkazu `if` v Visual Basic. První dva příkazy obnoví `firstClicked` a `secondClicked` referenční proměnné tak, aby již nesledovaly žádný z popisků. (Tyto dva příkazy můžete rozpoznat z obslužné rutiny události časovače Tick.) Třetí příkaz je příkaz `return`, který instruuje program, aby přeskočil zbytek příkazů v metodě bez jejich spuštění.

     Pokud programování v vizuálu C#, možná jste si všimli, že část kódu používá jediný symbol rovná se (`=`), zatímco jiné příkazy používají dva symboly rovná se (`==`). Zvažte, proč se na některých místech používá `=`, ale `==` se používá na jiných místech.

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

     První z těchto dvou příkazů ověří, zda jsou dvě ikony stejné. Vzhledem k tomu, že se porovnávají dvě C# hodnoty, používá vizuální program operátor rovnosti `==`. Druhý příkaz skutečně změní hodnotu (označované jako *přiřazení*) a nastaví `firstClicked` referenční proměnnou, která se rovná `null` k jejímu resetování. To je důvod, proč místo toho používá operátor přiřazení `=`. Vizuál C# používá `=` k nastavení hodnot a `==` k jejich porovnání. Visual Basic používá `=` přiřazování a porovnávání proměnných.

2. Uložte a spusťte program a začněte vybírat ikony ve formuláři. Pokud zvolíte dvojici, která neodpovídá, událost časovače Tick se aktivuje a obě ikony zmizí. Pokud zvolíte odpovídající dvojici, příkaz New `if` se spustí a příkaz return způsobí, že metoda přeskočí kód, který spouští časovač, takže ikony zůstanou viditelné, jak je znázorněno na následujícím obrázku.

     ![Hra, kterou v tomto kurzu vytvoříte](../ide/media/express-finishedgame.png "Express_FinishedGame") Porovnávací hra s viditelnými páry ikon

### <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat

- Pokud chcete přejít na další krok kurzu, přečtěte si [Krok 8: Přidání metody pro ověření, zda hráč zvítězil](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md).

- Pokud se chcete vrátit k předchozímu kroku kurzu, přečtěte si [Krok 6: Přidání časovače](../ide/step-6-add-a-timer.md).
