---
title: 'Krok 11: Spusťte svůj program a vyzkoušejte další funkce'
ms.custom: ''
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
ms.assetid: 656614d0-4fe7-4a67-8edc-c10919377d09
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 87992bb8ab2557dbca4c8e7e3a94dd99e5de7682
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50671921"
---
# <a name="step-11-run-your-program-and-try-other-features"></a>Krok 11: Spusťte svůj program a vyzkoušejte další funkce
Aplikace je dokončené a připravené ke spuštění. Můžete spustit váš program a nastavit barvu pozadí <xref:System.Windows.Forms.PictureBox>. Další informace, zkuste program zlepšit změnou barvy formuláře, přizpůsobením tlačítek a zaškrtávacího políčka a změnou vlastností formuláře.

 Chcete-li stáhnout úplnou verzi vzorku, přečtěte si téma [ukázkový kurz pro prohlížeč ucelený přehled](https://code.msdn.microsoft.com/Complete-Picture-Viewer-7d91d3a8).

 ![odkaz na video](../data-tools/media/playvideo.gif)video verzi tohoto tématu naleznete v tématu [kurz 1: vytvoření prohlížeče obrázků v jazyce Visual Basic - Video 5](http://go.microsoft.com/fwlink/?LinkId=205216) nebo [kurz 1: vytvoření prohlížeče obrázků v C# – Video 5](http://go.microsoft.com/fwlink/?LinkId=205206). Tato videa používají starší verzi sady Visual Studio, takže existují mírné rozdíly v některých příkazech nabídek a jiných prvcích uživatelského rozhraní. Nicméně koncepty a postupy fungují podobně jako v aktuální verzi sady Visual Studio.

## <a name="to-run-your-program-and-set-the-background-color"></a>Spusťte program a nastavit barvu pozadí

1.  Zvolte **F5**, nebo na panelu nabídek zvolte položky **ladění** > **spustit ladění**.

2.  Před otevřením obrázku vyberte **nastavit barvu pozadí** tlačítko. **Barva** zobrazí se dialogové okno.

     ![Dialogové okno barev](../ide/media/express_colordialog.png)
**barva** dialogové okno

3.  Zvolte barvu, kterou chcete nastavit barvu pozadí ovládacího prvku PictureBox. Prohlédněte si blíže `backgroundButton_Click()` metoda pochopit, jak to funguje.

    > [!NOTE]
    >  Načíst obrázek z Internetu vložením jeho URL do **otevřít soubor** dialogové okno. Pokuste se najít obrázek s průhledným pozadím, takže se zobrazí barva pozadí.

4.  Zvolte **Vymazat obrázek** tlačítko, abyste měli jistotu, že se vymaže. Ukončete program výběrem **Zavřít** tlačítko.

## <a name="to-try-other-features"></a>Vyzkoušení dalších funkcí

-   Změňte barvu formuláře a tlačítek pomocí **BackColor** vlastnost.

-   Přizpůsobte si tlačítka a zaškrtávací políčko pomocí **písmo** a **ForeColor** vlastnosti.

-   Změna formuláře **FormBorderStyle** a **ControlBox** vlastnosti.

-   Pomocí formuláře **AcceptButton** a **CancelButton** vlastností tohoto tlačítka je automaticky kliknuto, když uživatel klikne **Enter** nebo **Esc** klíč. Nechejte program otevřít **otevřít soubor** dialogové okno když uživatel vybere **Enter** a zavřít okno, když uživatel vybere **Esc**.

## <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat

-   Další informace o programování v sadě Visual Studio najdete v tématu [koncepty programování](https://msdn.microsoft.com/Library/65c12cca-af4f-4017-886e-2dbc00a189d6).

-   Další informace o jazyce Visual Basic, naleznete v tématu [vývoj aplikací pomocí jazyka Visual Basic](/dotnet/visual-basic/developing-apps/index).

-   Další informace o Visual C#, naleznete v tématu [Úvod do C# jazyk a rozhraní .NET Framework](/dotnet/csharp/getting-started/introduction-to-the-csharp-language-and-the-net-framework).

-   Chcete-li přejít k dalšímu kurzu, přečtěte si téma [kurz 2: vytvoření matematického kvízu](../ide/tutorial-2-create-a-timed-math-quiz.md).

-   Chcete-li vrátit k předchozímu kroku tutoriálu, přečtěte si téma [krok 10: napsat kód pro přídavná tlačítka a zaškrtávací políčko](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md).
