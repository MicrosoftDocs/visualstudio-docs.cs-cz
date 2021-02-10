---
title: Spusťte aplikaci pro prohlížení obrázků a zkuste jiné funkce.
description: Spusťte aplikaci Prohlížeč obrázků a vyzkoušejte si další funkce v kurzu Vytvoření prohlížeče obrázků.
ms.date: 09/11/2019
ms.custom: SEO-VS-2020
ms.assetid: 656614d0-4fe7-4a67-8edc-c10919377d09
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1a4488c212cabe95d73f75246fb297c17ce073b4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99950897"
---
# <a name="step-11-run-your-picture-viewer-app-and-try-other-features"></a>Krok 11: spuštění aplikace pro prohlížeč obrázků a vyzkoušejte jiné funkce

Vaše aplikace pro prohlížení obrázků je dokončená a připravená ke spuštění. Můžete spustit aplikaci a nastavit barvu pozadí <xref:System.Windows.Forms.PictureBox> . Pokud se chcete dozvědět víc, zkuste aplikaci vylepšit změnou barvy formuláře, přizpůsobením tlačítek a zaškrtávacím políčkem a změnou vlastností formuláře.

## <a name="how-to-run-your-app-and-set-the-background-color"></a>Jak spustit aplikaci a nastavit barvu pozadí

1. Vyberte **F5** nebo na panelu nabídek vyberte **ladit**  >  **Spustit ladění**.

1. Než otevřete obrázek, klikněte na tlačítko **nastavit barvu pozadí** . Otevře se dialogové okno **Barva** .

     ![Dialogové okno barvy](../ide/media/express_colordialog.png)<br/>
***Color** _ _dialog box *

1. Vyberte barvu pro nastavení barvy pozadí ovládacího prvku PictureBox. Prohlédněte si úzce na `backgroundButton_Click()` metodě (nebo `BackgroundButton_Click()` ), abyste pochopili, jak funguje.

    > [!NOTE]
    > Obrázek můžete načíst z Internetu vložením jeho adresy URL do dialogového okna **otevřít soubor** . Zkuste najít obrázek s průhledným pozadím, aby se zobrazila barva pozadí.

1. Klikněte na tlačítko **Vymazat obrázek** , abyste se ujistili, že se vymaže. Pak aplikaci ukončete kliknutím na tlačítko **Zavřít** .

## <a name="try-other-features"></a>Vyzkoušení dalších funkcí

* Změňte barvu formuláře a tlačítek pomocí vlastnosti **BackColor** .

* Přizpůsobte si tlačítka a zaškrtávací políčko pomocí vlastností **Font** a **ForeColor** .

* Změňte vlastnosti **FormBorderStyle** a **ovládací nabídka** formuláře.

* Použijte vlastnosti **AcceptButton** a **CancelButton** vašeho formuláře, aby se tlačítka automaticky brala, když uživatel zvolí klávesu **ENTER** nebo **ESC** . Nastavit aplikaci tak, aby otevřela dialogové okno **otevřít soubor** , když uživatel zvolí **ENTER** a zavřít pole, když uživatel zvolí **klávesu ESC**.

## <a name="next-steps"></a>Další kroky

Další informace najdete v následujícím kurzu:

> [!div class="nextstepaction"]
> [Kurz 2: vytvoření časovaného matematického kvízu](../ide/tutorial-2-create-a-timed-math-quiz.md)

Chcete-li se vrátit k předchozímu kroku kurzu, přečtěte si část [Krok 10: psaní kódu pro další tlačítka a zaškrtávací políčko](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md).

## <a name="see-also"></a>Viz také

* [Další kurzy C#](../get-started/csharp/index.yml)
* [Další kurzy Visual Basic](../get-started/visual-basic/index.yml)
* [Kurz pro C++](/cpp/get-started/tutorial-console-cpp)