---
title: Nastavte kukátko pro proměnné v paralelních vláknech | Microsoft Docs
description: Nastavte kukátko pro proměnné v paralelních vláknech v sadě Visual Studio. Současně zobrazí hodnoty, které jeden výraz obsahuje ve více vláknech.
ms.custom: SEO-VS-2020
ms.date: 04/25/2017
ms.topic: how-to
f1_keywords:
- vs.debug.parallelwatch
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, parallel watch window
ms.assetid: 28004d9b-420c-48f7-b80e-ab1519802558
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 28aeffb629a44c296fb9a349e165c7ce88f70b0c
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/13/2021
ms.locfileid: "98150571"
---
# <a name="set-a-watch-on-variables-in-parallel-threads-in-visual-studio-c-visual-basic-c"></a>Nastavení kukátka pro proměnné v paralelních vláknech v sadě Visual Studio (C#, Visual Basic, C++)
V paralelním okno Kukátko lze současně zobrazit hodnoty, které jeden výraz obsahuje ve více vláknech. Každý řádek představuje vlákno, které běží v aplikaci, ale vlákno může být reprezentované ve více řádcích. Přesněji řečeno, každý řádek představuje volání funkce, jejíž signatura funkce odpovídá funkci v aktuálním bloku zásobníku. Položky, které jsou ve sloupcích, můžete řadit, přeřadit, odebírat a seskupovat. Vlákna můžete označit, zrušit jeho příznak, zablokovat (pozastavit) a uvolnit (pokračovat). V okně **paralelní sledování** se zobrazí následující sloupce:

- Sloupec příznak, ve kterém můžete označit vlákno, kterému chcete věnovat zvláštní pozornost.

- Aktuální sloupec vlákna, ve kterém žlutá šipka indikuje aktuální vlákno (zelená šipka se složenou čárkou, označuje, že neaktuální vlákno má aktuální kontext ladicího programu).

- Konfigurovatelný sloupec, který může zobrazit počítač, proces, dlaždici, úlohu a vlákno.

  > [!TIP]
  > Chcete-li zobrazit informace o úkolu v okně **paralelní sledování** , je nutné nejprve otevřít okno **úkolu** .

- Prázdné sloupce *Přidat kukátko* , ve kterých můžete zadat výrazy ke sledování.

  [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-display-the-parallel-watch-window"></a>Zobrazení paralelního okno Kukátko

1. Nastavte zarážku v kódu.

2. Na řádku nabídek klikněte na položku **ladit**, **Spustit ladění**. Počkejte, než aplikace dorazí na zarážku.

3. V panelu nabídek zvolte položku **ladit**, **okna**, **paralelní kukátko** a pak zvolte okno kukátka. Můžete otevřít až čtyři okna.

### <a name="to-add-a-watch-expression"></a>Přidání výrazu kukátka

- Vyberte jeden z prázdných sloupců *Přidat kukátko* a pak zadejte výraz kukátka.

### <a name="to-flag-or-unflag-a-thread"></a>Označení nebo odoznačení vlákna vláknem

- Vyberte sloupec příznak pro řádek (první sloupec) nebo otevřete místní nabídku pro vlákno a zvolte **příznak** nebo zrušit **označení**.

### <a name="to-display-only-flagged-threads"></a>Chcete-li zobrazit pouze vlákna označená příznakem

- V levém horním rohu okna **paralelního sledování** vyberte tlačítko **Zobrazit pouze označení příznakem** .

### <a name="to-switch-to-another-thread"></a>Přepnutí na jiné vlákno

- Dvakrát klikněte na sloupec aktuálního vlákna (druhý sloupec). (Klávesnice: vyberte řádek a stiskněte klávesu ENTER.)

### <a name="to-sort-a-column"></a>Postup řazení sloupce

- Vyberte záhlaví sloupce.

### <a name="to-group-threads"></a>Seskupení vláken

- Otevřete místní nabídku pro paralelní okno Kukátko, zvolte možnost **Seskupit podle** a pak zvolte příslušnou položku v podnabídce.

### <a name="to-freeze-or-thaw-threads"></a>Zablokování nebo odmrazení vláken

- Otevřete místní nabídku řádku a vyberte možnost **ukotvit** nebo **rozmrazit**.

### <a name="to-export-the-data-in-the-parallel-watch-window"></a>Export dat v paralelním okno Kukátko

- Klikněte na tlačítko **otevřít v aplikaci Excel** a pak zvolte možnost **otevřít v aplikaci Excel** nebo **exportovat do sdíleného svazku clusteru**.

### <a name="to-filter-by-a-boolean-expression"></a>Filtrování podle logického výrazu

- Zadejte logický výraz do pole **filtrovat podle logického výrazu** . Ladicí program vyhodnotí výraz pro každý kontext vlákna. Zobrazí se pouze řádky, ve kterých je hodnota `true` zobrazena.

## <a name="see-also"></a>Viz také
- [Ladění vícevláknových aplikací](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Postupy: použití okna vláken GPU](../debugger/how-to-use-the-gpu-threads-window.md)
- [Návod: ladění aplikace C++ AMP](/cpp/parallel/amp/walkthrough-debugging-a-cpp-amp-application)