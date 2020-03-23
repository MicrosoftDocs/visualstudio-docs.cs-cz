---
title: 'Kurz 1: Vytvoření prohlížeče obrázků'
ms.date: 10/16/2019
ms.assetid: 3071d6df-2b2f-4e95-ab68-bef727323136
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5f1431d56516c749004cef1b35ada482a6c53446
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579720"
---
# <a name="tutorial-1-create-a-picture-viewer"></a>Kurz 1: Vytvoření prohlížeče obrázků

V tomto kurzu vytvoříte aplikaci, která načte obrázek ze souboru a zobrazí jej v okně. Dozvíte se, jak pomocí **Návrháře formulářů systému Windows** přetáhnout do formuláře ovládací prvky, jako jsou tlačítka a pole obrázků, nastavit jejich vlastnosti a pomocí kontejnerů plynule změnit velikost formuláře. Můžete také začít psát kód.

> [!NOTE]
> Tento kurz zahrnuje c# a visual basic, takže se zaměřte na informace, které jsou specifické pro programovací jazyk, který používáte.

Tento kurz vás provede následujícími úkoly:

* Vytvoření nového projektu

* Testování (ladění) aplikace.

* Přidejte do formuláře základní ovládací prvky, jako jsou zaškrtávací políčka a tlačítka.

* Umístěte ovládací prvky ve formuláři pomocí rozložení.

* Přidejte do formuláře dialogová okna **Otevřít soubor** a **Barvy.**

* Napište kód pomocí technologie IntelliSense a fragmentů kódu.

* Napište metody obslužné rutiny události.

Po dokončení by aplikace měla vypadat podobně jako na následujícím obrázku:

![Aplikace Prohlížeč obrázků, kterou vytvoříte v tomto kurzu](../ide/media/express_pictureviewerdone.png)

## <a name="tutorial-links"></a>Odkazy na kurz

|Nadpis|Popis|
|-----------|-----------------|
|[Krok 1: Vytvoření projektu aplikace pro Windows Forms](../ide/step-1-create-a-windows-forms-application-project.md)|Začněte vytvořením projektu aplikace Windows Forms App.|
|[Krok 2: Spuštění aplikace prohlížeče obrázků](../ide/step-2-run-your-program.md)|Spusťte projekt aplikace Windows Forms App, který jste vytvořili v předchozím kroku.|
|[Krok 3: Nastavení vlastností formuláře](../ide/step-3-set-your-form-properties.md)|Změňte vzhled formuláře pomocí okna **Vlastnosti.**|
|[Krok 4: Rozložení formuláře pomocí ovládacího prvku TableLayoutPanel](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md)|Přidejte `TableLayoutPanel` ovládací prvek do formuláře.|
|[Krok 5: Přidání ovládacích prvků do formuláře](../ide/step-5-add-controls-to-your-form.md)|Přidejte do formuláře `PictureBox` ovládací `CheckBox` prvky, například ovládací prvek a ovládací prvek. Přidejte tlačítka do formuláře.|
|[Krok 6: Pojmenování ovládacích prvků tlačítek](../ide/step-6-name-your-button-controls.md)|Přejmenujte tlačítka na něco smysluplnějšího.|
|[Krok 7: Přidání součástí dialogu do formuláře](../ide/step-7-add-dialog-components-to-your-form.md)|Přidejte `OpenFileDialog` součást `ColorDialog` a součást do formuláře.|
|[Krok 8: Napište kód pro obslužnou rutinu události tlačítka obrázku](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md)|Napište kód pomocí nástroje IntelliSense.|
|[Krok 9: Kontrola, komentování a testování kódu](../ide/step-9-review-comment-and-test-your-code.md)|Zkontrolujte a otestujte svůj kód. Podle potřeby přidejte komentáře.|
|[Krok 10: Napište kód pro další tlačítka a zaškrtávací políčko](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md)|Napište kód, aby ostatní tlačítka a zaškrtávací políčko fungovaly pomocí technologie IntelliSense.|
|[Krok 11: Spuštění aplikace a vyzkoušení dalších funkcí](../ide/step-11-run-your-program-and-try-other-features.md)|Spusťte aplikaci a nastavte barvu pozadí. Vyzkoušejte další funkce, například změnu barev, písem a ohraničení.|

K dispozici jsou také skvělé, bezplatné výukové materiály pro video. Další informace o programování v jazyce C#, viz [Základy jazyka C#: Vývoj pro úplné začátečníky](https://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners). Další informace o programování v jazyce Visual Basic najdete v [tématu Základy jazyka: Vývoj pro úplné začátečníky](https://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners).

## <a name="next-steps"></a>Další kroky

Chcete-li zahájit kurz, začněte krokem **[1: Vytvoření projektu aplikace Windows Forms](../ide/step-1-create-a-windows-forms-application-project.md)**.

## <a name="see-also"></a>Viz také

* [Další výukové programy pro C#](/visualstudio/get-started/csharp/)
* [Výukové programy jazyka Visual Basic](/visualstudio/get-started/visual-basic/)
* [Výukové programy pro C++](/cpp/get-started/tutorial-console-cpp)
