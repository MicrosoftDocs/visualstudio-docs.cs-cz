---
title: 'Kurz 1: vytvoření prohlížeče obrázků'
description: Naučte se, jak vytvořit aplikaci, která načte obrázek ze souboru a zobrazí ji v okně.
ms.custom: SEO-VS-2020
ms.date: 10/16/2019
ms.assetid: 3071d6df-2b2f-4e95-ab68-bef727323136
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: cdfd4294511752e201c2291a03f89d0bded2506b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99971450"
---
# <a name="tutorial-1-create-a-picture-viewer"></a>Kurz 1: vytvoření prohlížeče obrázků

V tomto kurzu sestavíte aplikaci, která načte obrázek ze souboru a zobrazí se v okně. Naučíte se, jak pomocí **Návrhář formulářů** přetahovat ovládací prvky jako tlačítka a pole obrázků do formuláře, nastavit jejich vlastnosti a plynule změnit velikost formuláře pomocí kontejnerů. Můžete také začít psát kód.

> [!NOTE]
> Tento kurz se zabývá C# i Visual Basic, takže se zaměřte na informace, které jsou specifické pro programovací jazyk, který používáte.

Tento kurz vás provede následujícími úlohami:

* Vytvoření nového projektu

* Otestujte (Ladit) aplikaci.

* Přidejte základní ovládací prvky, jako jsou zaškrtávací políčka a tlačítka, do formuláře.

* Umístěte ovládací prvky na formulář pomocí rozložení.

* Přidejte dialogová okna **otevřít soubor** a **barev** do formuláře.

* Pište kód pomocí technologie IntelliSense a fragmenty kódu.

* Zapište metody obslužné rutiny události.

Až skončíte, aplikace by měla vypadat podobně jako na následujícím obrázku:

![Aplikace pro prohlížeč obrázků, kterou vytvoříte v tomto kurzu](../ide/media/express_pictureviewerdone.png)

## <a name="tutorial-links"></a>Odkazy na kurz

|Nadpis|Popis|
|-----------|-----------------|
|[Krok 1: Vytvoření projektu aplikace modelu Windows Forms](../ide/step-1-create-a-windows-forms-application-project.md)|Začněte vytvořením projektu aplikace model Windows Forms.|
|[Krok 2: spuštění aplikace pro prohlížeč obrázků](../ide/step-2-run-your-program.md)|Spusťte projekt aplikace model Windows Forms, který jste vytvořili v předchozím kroku.|
|[Krok 3: Nastavení vlastností formuláře](../ide/step-3-set-your-form-properties.md)|Změňte vzhled formuláře pomocí okna **vlastnosti** .|
|[Krok 4: Rozvržení formuláře pomocí ovládacího prvku TableLayoutPanel](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md)|Přidejte `TableLayoutPanel` ovládací prvek do formuláře.|
|[Krok 5: Přidání ovládacích prvků do formuláře](../ide/step-5-add-controls-to-your-form.md)|Přidejte ovládací prvky, například `PictureBox` ovládací prvek a `CheckBox` ovládací prvek, do formuláře. Přidejte tlačítka do formuláře.|
|[Krok 6: Pojmenování tlačítkových ovládacích prvků](../ide/step-6-name-your-button-controls.md)|Přejmenujte tlačítka na smysluplnější.|
|[Krok 7: Přidání komponent dialogových oken do formuláře](../ide/step-7-add-dialog-components-to-your-form.md)|Přidejte `OpenFileDialog` komponentu a `ColorDialog` komponentu do formuláře.|
|[Krok 8: Zapište kód pro obslužnou rutinu události zobrazit tlačítko obrázku](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md)|Pište kód pomocí nástroje IntelliSense.|
|[Krok 9: Kontrola, okomentování a otestování kódu](../ide/step-9-review-comment-and-test-your-code.md)|Zkontrolujte a otestujte svůj kód. Přidejte komentáře podle potřeby.|
|[Krok 10: Napsání kódu pro přídavná tlačítka a zaškrtávací políčko](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md)|Napíšete kód pro nastavení dalších tlačítek a zaškrtávací políčko v práci pomocí technologie IntelliSense.|
|[Krok 11: Spuštění aplikace a vyzkoušení dalších funkcí](../ide/step-11-run-your-program-and-try-other-features.md)|Spusťte aplikaci a nastavte barvu pozadí. Vyzkoušejte jiné funkce, jako je například změna barev, písem a ohraničení.|

K dispozici jsou také skvělé a bezplatné studijní materiály pro video. Další informace o programování v jazyce C# najdete v tématu [základy jazyka c#: vývoj pro naprostou začátečníky](https://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners). Další informace o programování v Visual Basic najdete v tématu [Visual Basic základy: vývoj pro absolutní začátečníky](https://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners).

## <a name="next-steps"></a>Další kroky

Chcete-li začít s kurzem, začněte v **[kroku 1: vytvoření projektu aplikace model Windows Forms](../ide/step-1-create-a-windows-forms-application-project.md)**.

## <a name="see-also"></a>Viz také

* [Další kurzy C#](../get-started/csharp/index.yml)
* [Kurzy Visual Basic](../get-started/visual-basic/index.yml)
* [Kurzy C++](/cpp/get-started/tutorial-console-cpp)