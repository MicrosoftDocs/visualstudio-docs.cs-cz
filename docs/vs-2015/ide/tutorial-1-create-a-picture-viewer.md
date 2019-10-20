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
ms.openlocfilehash: ad57a05e45b7e9acd3db455f0a8849166dc3c735
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654753"
---
# <a name="tutorial-1-create-a-picture-viewer"></a>Tutoriál 1: Vytvoření prohlížeče obrázků
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V tomto kurzu sestavíte program, který načte obrázek ze souboru a zobrazí se v okně. Naučíte se přetáhnout ovládací prvky jako tlačítka a pole obrázků ve formuláři, nastavit jejich vlastnosti a plynule změnit velikost formuláře pomocí kontejnerů. Můžete také začít psát kód. Získáte informace o následujících postupech:

- Vytvořte nový projekt.

- Otestujte (Ladit) aplikaci.

- Přidejte základní ovládací prvky, jako jsou zaškrtávací políčka a tlačítka, do formuláře.

- Umístěte ovládací prvky na formulář pomocí rozložení.

- Přidejte dialogová okna **otevřít soubor** a **barev** do formuláře.

- Pište kód pomocí technologie IntelliSense a fragmenty kódu.

- Zapište metody obslužné rutiny události.

  Po dokončení bude program vypadat jako na následujícím obrázku.

  ![Obrázek, který v tomto kurzu vytvoříte](../ide/media/express-pictureviewerdone.png "Express_PictureViewerDone") Obrázek, který v tomto kurzu vytvoříte

  Pokud si chcete stáhnout dokončenou verzi ukázky, přečtěte si [ukázku kurzu dokončení prohlížeče obrázků](http://code.msdn.microsoft.com/Complete-Picture-Viewer-7d91d3a8).

  ![odkaz na video](../data-tools/media/playvideo.gif "PlayVideo") Verzi videa tohoto tématu naleznete v části [How to: Create a Picture Viewer in Visual Basic?](http://go.microsoft.com/fwlink/?LinkId=205207) nebo [How to: Create a Picture Viewer in C#?](http://go.microsoft.com/fwlink/?LinkId=205198).

> [!NOTE]
> Tato videa používají starší verzi sady Visual Studio, takže existují mírné rozdíly v některých příkazech nabídky a dalších prvcích uživatelského rozhraní. Koncepty a postupy však fungují podobně v aktuální verzi sady Visual Studio. V C# tomto kurzu se zaměříte na vizuál a Visual Basic, takže se zaměřte na informace, které jsou specifické pro programovací jazyk, který používáte.
>
> Chcete-li zobrazit kód pro Visual Basic, vyberte kartu **VB** v horní části bloků kódu a zobrazte kód pro vizuál C#, vyberte **C#** kartu. Pokud vás zajímá o vizuál C++, přečtěte si kurz [Začínáme](../misc/getting-started-with-visual-cpp-in-visual-studio-2015.md) a [ C++ jazyk](http://www.cplusplus.com/doc/tutorial/).
>
> Pokud vás zajímá, jak psát Visual C# nebo Visual Basic aplikace pro Windows Store, přečtěte si téma [Vytvoření první aplikace pro Windows store pomocí C# nebo Visual Basic](https://msdn.microsoft.com/library/windows/apps/hh974581.aspx). Informace o vytváření aplikací JavaScriptu pro Windows Store najdete v tématu [Vytvoření první aplikace pro Windows Store pomocí JavaScriptu](https://msdn.microsoft.com/library/windows/apps/br211385.aspx).

## <a name="related-topics"></a>Související témata

|Název|Popis|
|-----------|-----------------|
|[Krok 1: Vytvořte projekt formulářové aplikace Windows](../ide/step-1-create-a-windows-forms-application-project.md)|Začněte vytvořením projektu model Windows Forms aplikace.|
|[Krok 2: Spusťte svůj program](../ide/step-2-run-your-program.md)|Spusťte program model Windows Forms aplikace, který jste vytvořili v předchozím kroku.|
|[Krok 3: Nastavte vlastnosti svého formuláře](../ide/step-3-set-your-form-properties.md)|Změňte vzhled formuláře pomocí okna **vlastnosti** .|
|[Krok 4: Rozvrhněte svůj formulář pomocí ovládacího prvku TableLayoutPanel](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md)|Přidejte ovládací prvek `TableLayoutPanel` do formuláře.|
|[Krok 5: Přidejte do svého formuláře ovládací prvky](../ide/step-5-add-controls-to-your-form.md)|Do formuláře přidejte ovládací prvky, například ovládací prvek `PictureBox` a ovládací prvek `CheckBox`. Přidejte tlačítka do formuláře.|
|[Krok 6: Pojmenujte své ovládací prvky tlačítek](../ide/step-6-name-your-button-controls.md)|Přejmenujte tlačítka na smysluplnější.|
|[Krok 7: Přidejte do svého formuláře komponenty dialogových oken](../ide/step-7-add-dialog-components-to-your-form.md)|Přidejte komponentu **OpenFileDialog** a komponentu **ColorDialog** do formuláře.|
|[Krok 8: Zapište kód pro obslužnou rutinu události zobrazení tlačítka s obrázkem](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md)|Pište kód pomocí nástroje IntelliSense.|
|[Krok 9: Zrevidujte, okomentujte a otestujte svůj kód](../ide/step-9-review-comment-and-test-your-code.md)|Zkontrolujte a otestujte svůj kód. Přidejte komentáře podle potřeby.|
|[Krok 10: Zapište kód pro přídavná tlačítka a zaškrtávací pole](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md)|Napíšete kód pro nastavení dalších tlačítek a zaškrtávací políčko v práci pomocí technologie IntelliSense.|
|[Krok 11: Spusťte svůj program a vyzkoušejte další funkce](../ide/step-11-run-your-program-and-try-other-features.md)|Spusťte program a nastavte barvu pozadí. Vyzkoušejte jiné funkce, jako je například změna barev, písem a ohraničení.|
