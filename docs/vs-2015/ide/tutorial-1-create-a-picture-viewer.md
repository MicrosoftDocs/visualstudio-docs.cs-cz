---
title: 'Kurz 1: vytvoření prohlížeče obrázků | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 3071d6df-2b2f-4e95-ab68-bef727323136
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 66988fa88ae347a2db08bf2f6d1b79ba3bcd80b8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "75851320"
---
# <a name="tutorial-1-create-a-picture-viewer"></a>Tutoriál 1: Vytvoření prohlížeče obrázků
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V tomto kurzu sestavíte program, který načte obrázek ze souboru a zobrazí se v okně. Naučíte se přetáhnout ovládací prvky jako tlačítka a pole obrázků ve formuláři, nastavit jejich vlastnosti a plynule změnit velikost formuláře pomocí kontejnerů. Můžete také začít psát kód. Získáte informace o těchto tématech:

- Vytvoření nového projektu

- Otestujte (Ladit) aplikaci.

- Přidejte základní ovládací prvky, jako jsou zaškrtávací políčka a tlačítka, do formuláře.

- Umístěte ovládací prvky na formulář pomocí rozložení.

- Přidejte dialogová okna **otevřít soubor** a **barev** do formuláře.

- Pište kód pomocí technologie IntelliSense a fragmenty kódu.

- Zapište metody obslužné rutiny události.

  Po dokončení bude program vypadat jako na následujícím obrázku.

  ![Obrázek, který v tomto kurzu vytvoříte](../ide/media/express-pictureviewerdone.png "Express_PictureViewerDone") Obrázek, který v tomto kurzu vytvoříte

  ![odkaz na video](../data-tools/media/playvideo.gif "PlayVideo") Verzi videa tohoto tématu naleznete v tématu [How to: Create a Picture Viewer in Visual Basic?](https://msdn.microsoft.com/vstudio/gg315352) nebo [How to: Create a Viewer Picture in C#?](https://msdn.microsoft.com/vcsharp/gg278960.aspx).

> [!NOTE]
> Tato videa používají starší verzi sady Visual Studio, takže existují mírné rozdíly v některých příkazech nabídky a dalších prvcích uživatelského rozhraní. Koncepty a postupy však fungují podobně v aktuální verzi sady Visual Studio. V tomto kurzu se zaměříte na Visual C# a Visual Basic, takže se zaměřte na informace, které jsou specifické pro programovací jazyk, který používáte.
>
> Chcete-li zobrazit kód pro Visual Basic, vyberte kartu **VB** v horní části bloků kódu a chcete-li zobrazit kód pro jazyk Visual C#, vyberte kartu **C#** . Pokud vás zajímá o Visual C++, přečtěte si kurz [Začínáme](../misc/getting-started-with-visual-cpp-in-visual-studio-2015.md) a [jazyk C++](http://www.cplusplus.com/doc/tutorial/).
>
> Pokud vás zajímá, jak psát aplikace Visual C# nebo Visual Basic pro Windows Store, přečtěte si téma [Vytvoření první aplikace pro Windows Store pomocí jazyka C# nebo Visual Basic](https://msdn.microsoft.com/library/windows/apps/hh974581.aspx). Informace o vytváření aplikací JavaScriptu pro Windows Store najdete v tématu [Vytvoření první aplikace pro Windows Store pomocí JavaScriptu](https://msdn.microsoft.com/library/windows/apps/br211385.aspx).

## <a name="related-topics"></a>Související témata

|Nadpis|Popis|
|-----------|-----------------|
|[Krok 1: Vytvořte projekt formulářové aplikace Windows](../ide/step-1-create-a-windows-forms-application-project.md)|Začněte vytvořením projektu model Windows Forms aplikace.|
|[Krok 2: Spusťte svůj program](../ide/step-2-run-your-program.md)|Spusťte program model Windows Forms aplikace, který jste vytvořili v předchozím kroku.|
|[Krok 3: nastavení vlastností formuláře](../ide/step-3-set-your-form-properties.md)|Změňte vzhled formuláře pomocí okna **vlastnosti** .|
|[Krok 4: rozložení formuláře pomocí ovládacího prvku TableLayoutPanel](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md)|Přidejte `TableLayoutPanel` ovládací prvek do formuláře.|
|[Krok 5: Přidání ovládacích prvků do formuláře](../ide/step-5-add-controls-to-your-form.md)|Přidejte ovládací prvky, například `PictureBox` ovládací prvek a `CheckBox` ovládací prvek, do formuláře. Přidejte tlačítka do formuláře.|
|[Krok 6: Pojmenujte své ovládací prvky tlačítek](../ide/step-6-name-your-button-controls.md)|Přejmenujte tlačítka na smysluplnější.|
|[Krok 7: přidejte do svého formuláře komponenty dialogových oken](../ide/step-7-add-dialog-components-to-your-form.md)|Přidejte komponentu **OpenFileDialog** a komponentu **ColorDialog** do formuláře.|
|[Krok 8: Zapište kód pro obslužnou rutinu události zobrazit tlačítko obrázku](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md)|Pište kód pomocí nástroje IntelliSense.|
|[Krok 9: kontrola, komentář a testování kódu](../ide/step-9-review-comment-and-test-your-code.md)|Zkontrolujte a otestujte svůj kód. Přidejte komentáře podle potřeby.|
|[Krok 10: napište kód pro další tlačítka a zaškrtávací políčko](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md)|Napíšete kód pro nastavení dalších tlačítek a zaškrtávací políčko v práci pomocí technologie IntelliSense.|
|[Krok 11: Spusťte svůj program a vyzkoušejte další funkce](../ide/step-11-run-your-program-and-try-other-features.md)|Spusťte program a nastavte barvu pozadí. Vyzkoušejte jiné funkce, jako je například změna barev, písem a ohraničení.|
