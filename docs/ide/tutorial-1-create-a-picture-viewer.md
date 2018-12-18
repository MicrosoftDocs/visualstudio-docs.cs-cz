---
title: 'Tutoriál 1: Vytvoření prohlížeče obrázků'
ms.custom: ''
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
ms.assetid: 3071d6df-2b2f-4e95-ab68-bef727323136
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 966634ee9a71854334bdd5342326c1663b9ad16c
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50672155"
---
# <a name="tutorial-1-create-a-picture-viewer"></a>Tutoriál 1: Vytvoření prohlížeče obrázků

V tomto kurzu vytvoříte program, který načte obrázek ze souboru a zobrazí jej v okně. Další informace o použití **Návrháře formulářů Windows** se přetáhnout prvky jako tlačítka a pole obrázků ve formuláři, nastavit jejich vlastnosti a plynule změnit velikost formuláře pomocí kontejnerů. Můžete také začít psát kód. Získáte informace o následujících postupech:

-   Vytvořte nový projekt.

-   Otestujte (vylaďte) aplikaci.

-   Přidejte základní ovládací prvky jako zaškrtávací políčka a tlačítka do formuláře.

-   Umístit ovládací prvky na formulář pomocí rozložení.

-   Přidat **otevřít soubor** a **barva** dialogová okna do formuláře.

-   Pište kód pomocí technologie IntelliSense a fragmentů kódu.

-   Zápis obslužné rutiny události.

Jakmile skončíte, program bude vypadat jako na následujícím obrázku:

![Obrázek, který vytvoříte v tomto kurzu](../ide/media/express_pictureviewerdone.png)

## <a name="tutorial-links"></a>Kurz odkazy

Chcete-li stáhnout úplnou verzi vzorku, přečtěte si téma [ukázkový kurz pro prohlížeč ucelený přehled](https://code.msdn.microsoft.com/Complete-Picture-Viewer-7d91d3a8).

![odkaz na video](../data-tools/media/playvideo.gif)video verzi tohoto tématu naleznete v tématu [jak mohu: vytvořit prohlížeče obrázků v jazyce Visual Basic?](http://go.microsoft.com/fwlink/?LinkId=205207) nebo [jak mohu: vytvořit prohlížeče obrázků v jazyce C#?](http://go.microsoft.com/fwlink/?LinkId=205198).

> [!NOTE]
> Tato videa používají starší verzi sady Visual Studio, takže existují mírné rozdíly v některých příkazech nabídek a jiných prvcích uživatelského rozhraní. Nicméně koncepty a postupy fungují podobně jako v aktuální verzi sady Visual Studio. Visual C# a Visual Basic jsou obě popsané v tomto kurzu, takže se zaměřte na informace, které jsou specifické pro programovací jazyk, který používáte.
>
> Chcete-li zobrazit kód v jazyce Visual Basic, zvolte **VB** kartě v horní části bloků kódu a chcete-li zobrazit kód pro jazyk Visual C#, zvolte **jazyka C#** kartu. Pokud máte zájem o získání informací o jazyce Visual C++, přejděte [Začínáme](../ide/getting-started-with-cpp-in-visual-studio.md) a [kurz jazyka C++](http://www.cplusplus.com/doc/tutorial/).
>
> Pokud máte zájem se naučit, jak psát aplikace Visual C# nebo Visual Basic UPW, přečtěte si téma [aplikací pro UWP sestavení](https://developer.microsoft.com/windows/apps).

## <a name="related-topics"></a>Související témata

|Název|Popis|
|-----------|-----------------|
|[Krok 1: Vytvoření projektu aplikace Windows Forms](../ide/step-1-create-a-windows-forms-application-project.md)|Začněte vytvořením projektu aplikace Windows Forms.|
|[Krok 2: Spusťte svůj program](../ide/step-2-run-your-program.md)|Spusťte program aplikace Windows Forms, který jste vytvořili v předchozím kroku.|
|[Krok 3: Nastavte vlastnosti svého formuláře](../ide/step-3-set-your-form-properties.md)|Změnit způsob, jakým vzhled formuláře pomocí **vlastnosti** okna.|
|[Krok 4: Rozvrhněte svůj formulář pomocí ovládacího prvku TableLayoutPanel](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md)|Přidat `TableLayoutPanel` ovládací prvek do formuláře.|
|[Krok 5: Přidejte do svého formuláře ovládací prvky](../ide/step-5-add-controls-to-your-form.md)|Přidejte ovládací prvky, například `PictureBox` ovládacího prvku a `CheckBox` ovládací prvek do formuláře. Přidejte tlačítka do formuláře.|
|[Krok 6: Pojmenujte své ovládací prvky tlačítek](../ide/step-6-name-your-button-controls.md)|Přejmenujte tlačítka na něco smysluplnějšího.|
|[Krok 7: Přidejte do svého formuláře komponenty dialogových oken](../ide/step-7-add-dialog-components-to-your-form.md)|Přidat `OpenFileDialog` komponenty a `ColorDialog` komponentu do formuláře.|
|[Krok 8: Zapište kód pro zobrazení obslužné rutiny události obrázku tlačítka](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md)|Pište kód pomocí nástroje technologie IntelliSense.|
|[Krok 9: Kontrola, komentáře a testování kódu](../ide/step-9-review-comment-and-test-your-code.md)|Zkontrolujte a otestujte svůj kód. Podle potřeby přidejte komentáře.|
|[Krok 10: Zapište kód pro přídavná tlačítka a zaškrtávací políčko](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md)|Psaní kódu, aby další tlačítka a zaškrtávací políčko pracovala pomocí technologie IntelliSense.|
|[Krok 11: Spusťte svůj program a vyzkoušejte další funkce](../ide/step-11-run-your-program-and-try-other-features.md)|Spusťte svůj program a nastavit barvu pozadí. Vyzkoušejte další funkce, jako je například změna barvy, písma a ohraničení.|
