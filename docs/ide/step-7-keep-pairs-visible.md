---
title: 'Krok 7: Zachování dvojic ve viditelném stavu'
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.devlang:
- csharp
- vb
dev_langs:
- CSharp
- VB
ms.assetid: 42e1d08c-7b2e-4efd-9f47-85d6206afe35
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 01eba06b569d48a6ab49174183438fcea96cb5c7
ms.sourcegitcommit: 541a0556958201ad6626bc8638406ad02640f764
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2019
ms.locfileid: "71079307"
---
# <a name="step-7-keep-pairs-visible"></a>Krok 7: Zachování dvojic ve viditelném stavu
Hra funguje dobře tak dlouho, dokud hráč vybírá pouze dvojice ikon, které neodpovídají. Ale zvažte, co by mělo nastat, pokud hráč vybere shodnou dvojici. Místo toho, aby ikony zmizely zapnutím časovače (pomocí <xref:System.Windows.Forms.Timer.Start> metody), by se hra měla resetovat sama tak, aby již nesledovala popisky `firstClicked` pomocí proměnných a `secondClicked` , aniž by bylo nutné resetovat barvy pro dva popisky, které byly zvoleny.

## <a name="to-keep-pairs-visible"></a>Zachování dvojic viditelných

1. Do metody obslužné `if` rutiny událostipřidejtenásledujícípříkaz,poblížkoncekódutěsněnadpříkazem,kdespouštítečasovač.`label_Click()` Při přidávání do programu si kód pořádně prohlédněte. Zamyslete se nad tím, jak kód funguje.

     [!code-csharp[VbExpressTutorial4Step7#9](../ide/codesnippet/CSharp/step-7-keep-pairs-visible_1.cs)]
     [!code-vb[VbExpressTutorial4Step7#9](../ide/codesnippet/VisualBasic/step-7-keep-pairs-visible_1.vb)]

     První řádek `if` příkazu, který jste právě přidali, kontroluje, zda ikona v prvním popisku, kterou hráč zvolí, je stejná jako ikona ve druhém popisku. Pokud jsou ikony stejné, program provede tři příkazy mezi složenou závorkou v C# nebo třemi příkazy v rámci `if` příkazu v Visual Basic. První dva příkazy obnovily `firstClicked` referenční proměnné a `secondClicked` , aby již nesledovaly žádný z popisků. (Tyto dva příkazy můžete rozpoznat z obslužné rutiny <xref:System.Windows.Forms.Timer.Tick> události časovače.) Třetí příkaz je `return` příkaz, který oznamuje programu, aby přeskočil zbytek příkazů v metodě bez jejich spuštění.

     Pokud programování v vizuálu C#, možná jste si všimli, že část kódu používá jediný znak rovná se (`=`), zatímco jiné příkazy používají dva znaménka rovná`==`se (). Zvažte, `=` proč se na některých místech používá `==` , ale používá se na jiných místech.

     Toto je typický příklad, který ukazuje rozdíl. Pozorně se podívejte na kód mezi závorkami v `if` příkazu.

    ```vb
    firstClicked.Text = secondClicked.Text
    ```

    ```csharp
    firstClicked.Text == secondClicked.Text
    ```

     Pak se pečlivě podívejte na první příkaz v bloku kódu po `if` příkazu.

    ```vb
    firstClicked = Nothing
    ```

    ```csharp
    firstClicked = null;
    ```

     První z těchto dvou příkazů ověří, zda jsou dvě ikony stejné. Vzhledem k tomu, že se porovnávají dvě C# hodnoty, použije `==` vizuální program operátor rovnosti. Druhý příkaz skutečně změní hodnotu (označované jako *přiřazení*) a nastaví `firstClicked` `null` referenční proměnnou rovnou na resetování. To je důvod, proč místo `=` toho používá operátor přiřazení. Visual C# používá `=` k nastavení hodnot a `==` k jejich porovnání. Visual Basic používá `=` pro přiřazování a porovnávání proměnných.

2. Uložte a spusťte program a začněte vybírat ikony ve formuláři. Pokud zvolíte dvojici, která neodpovídá, událost časovače Tick se aktivuje a obě ikony zmizí. Pokud zvolíte odpovídající spárování, příkaz New `if` se spustí a příkaz return způsobí, že metoda přeskočí kód, který spouští časovač, takže ikony zůstanou viditelné, jak je znázorněno na následujícím obrázku.

     ![Hra, kterou v tomto kurzu](../ide/media/express_finishedgame.png)
vytvoříte,**odpovídá hře** s viditelnými páry ikon

## <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat

- Pokud chcete přejít na další krok kurzu, přečtěte si [krok 8: Přidejte metodu k ověření, zda hráč zvítězil](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md).

- Pokud se chcete vrátit k předchozímu kroku kurzu [, přečtěte si krok 6: Přidejte časovač](../ide/step-6-add-a-timer.md).
