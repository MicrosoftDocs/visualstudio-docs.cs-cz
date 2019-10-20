---
title: Ladění nebo zakázání kódu projektu v Návrhář XAML | Microsoft Docs
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: ac600581-8fc8-49e3-abdf-1569a3483d74
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e7de0b3985e09f61fd0c63d1764304b150503883
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657935"
---
# <a name="debugging-or-disabling-project-code-in-xaml-designer"></a>Ladění nebo zakázání kódu projektu v Návrháři XAML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V mnoha případech může být Neošetřená výjimka v Návrháři XAML způsobena tím, že se kód projektu pokusí získat přístup k vlastnostem nebo metodám, které vracejí jiné hodnoty nebo pracují různými způsoby, pokud je aplikace spuštěna v návrháři. Tyto výjimky můžete vyřešit laděním kódu projektu v jiné instanci aplikace Visual Studio, nebo je dočasně zabránit zakázáním kódu projektu v návrháři.

 Kód projektu zahrnuje:

- Vlastní ovládací prvky a uživatelské ovládací prvky

- Knihovny tříd

- Převaděče hodnot

- Vazby na data doby návrhu generovaná z kódu projektu

  Když je kód projektu zakázán, Visual Studio zobrazí zástupné symboly, jako je název vlastnosti pro vazbu, kde data již nejsou k dispozici; nebo zástupný symbol pro ovládací prvek, který již není spuštěn.

  ![Neošetřená výjimka – dialogové okno](../designers/media/xaml-unhandledexception.png "XAML_UnhandledException")

#### <a name="to-determine-if-project-code-is-causing-an-exception"></a>Určení, zda kód projektu způsobuje výjimku

1. V dialogu Neošetřená výjimka vyberte **kliknutím sem znovu načtěte odkaz návrháře** .

2. Na panelu nabídek vyberte možnost **ladit**, **Spustit ladění** a sestavte a spusťte aplikaci.

     V případě úspěšného sestavení a spuštění aplikace může být výjimka v době návrhu způsobena kódem vašeho projektu spuštěným v návrháři.

#### <a name="to-debug-project-code-running-in-the-designer"></a>Ladění kódu projektu spuštěného v Návrháři

1. V dialogu Neošetřená výjimka vyberte **kliknutím sem zakážete spuštění kódu projektu a znovu načtěte odkaz návrháře** .

2. Ve Správci úloh systému Windows klikněte na tlačítko **Ukončit úlohu** a zavřete tak všechny instance Návrhář XAML sady Visual Studio, které jsou aktuálně spuštěny.

     ![Instance návrháře XAML v TaskManager](../designers/media/xaml-taskmanager.png "XAML_TaskManager")

3. V aplikaci Visual Studio otevřete stránku XAML, která obsahuje kód nebo ovládací prvek, který chcete ladit.

4. Otevřete novou instanci sady Visual Studio a poté otevřete druhou instanci projektu.

5. Nastavte zarážku v kódu projektu.

6. V nové instanci aplikace Visual Studio, na panelu nabídek vyberte možnost **ladit**, **připojit k procesu**.

7. V dialogovém okně **připojit k procesu** zvolte v seznamu **procesy k dispozici** možnost **XDesProc. exe**a poté klikněte na tlačítko **připojit** .

     ![Proces návrháře XAML](../designers/media/xaml-attach.png "XAML_Attach")

     To je proces pro návrháře XAML v první instanci sady Visual Studio.

8. V první instanci aplikace Visual Studio, na panelu nabídek vyberte **ladit**, **Spustit ladění**.

     Nyní můžete krokovat kód, který je spuštěn v návrháři.

#### <a name="to-disable-project-code-in-the-designer"></a>Zakázání kódu projektu v Návrháři

- V dialogu Neošetřená výjimka vyberte **kliknutím sem zakážete spuštění kódu projektu a znovu načtěte odkaz návrháře** .

- Případně můžete na panelu nástrojů v Návrháři XAML zvolit tlačítko **Zakázat kód projektu** .

     ![Tlačítko Zakázat kód projektu](../designers/media/xaml-disablecode.png "XAML_DisableCode")

     Můžete znovu přepínat tlačítko a znovu povolit kód projektu.

    > [!NOTE]
    > Pro projekty, které cílí na procesory ARM nebo x64, nemůže Visual Studio spustit kód projektu v návrháři, takže tlačítko **Zakázat kód projektu** je v Návrháři zakázané.

- Kterákoli z možností způsobí, že Návrhář znovu načte a potom zakáže veškerý kód pro přidružený projekt.

    > [!NOTE]
    > Zakázáním kódu projektu může dojít ke ztrátě dat v době návrhu. Alternativou je ladění kódu spuštěného v návrháři.

## <a name="see-also"></a>Viz také
 [Návrh XAML v sadě Visual Studio a Blend pro Visual Studio](../designers/designing-xaml-in-visual-studio.md)
