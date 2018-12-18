---
title: Vytvoření Windows Forms aplikace pomocí jazyka Visual Basic
description: Zjistěte, jak vytvořit aplikaci Windows Forms v sadě Visual Studio pomocí jazyka Visual Basic, krok za krokem.
ms.date: 12/04/2017
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
ms.devlang: vb
author: TerryGLee
ms.author: tglee
manager: douge
dev_langs:
- vb
ms.workload:
- multiple
ms.openlocfilehash: 81b44e7053b820e625b5ad61d6e537c95cbf9c03
ms.sourcegitcommit: 0cdd8e8a53fb4fd5e869f07c35204419fa12783d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53159630"
---
# <a name="create-a-windows-forms-app-in-visual-studio-with-visual-basic"></a>Vytvoření Windows Forms aplikace v sadě Visual Studio pomocí jazyka Visual Basic

V této krátké Úvod do integrovaného vývojového prostředí (IDE) sady Visual Studio vytvoříte jednoduchou aplikaci Visual Basic, který má na základě Windows uživatelského rozhraní (UI).

Pokud jste ještě nenainstalovali aplikaci Visual Studio, přejděte [stahování sady Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) stránku a nainstalovat zdarma.

## <a name="create-a-project"></a>Vytvoření projektu

Nejprve vytvoříte projekt aplikace Visual Basic. Typ projektu obsahuje všechny soubory šablon, které potřebujete, než jste přidali ještě něco.

1. Otevřete Visual Studio 2017.

2. V horním řádku nabídek zvolte **Soubor** > **Nový** > **Projekt**.

3. V **nový projekt** dialogové okno v levém podokně rozbalte **jazyka Visual Basic**a klikněte na tlačítko **Windows Desktop**. V prostředním podokně vyberte **aplikace Windows Forms (.NET Framework)**. Potom zadejte název souboru `HelloWorld`.

     Pokud se nezobrazí **aplikace Windows Forms (.NET Framework)** projektu šablony, zrušte z celkového počtu **nový projekt** dialogového okna a v horní nabídce vyberte **nástroje**  >  **Získejte nástroje a funkce**. Spustí se instalační program pro Visual Studio. Zvolte **vývoj desktopových aplikací .NET** úloh, klikněte na tlačítko **změnit**.

     ![Úlohy .NET core v instalačním programu sady Visual Studio](../ide/media/install-dot-net-desktop-env.png)

## <a name="create-the-application"></a>Vytvoření aplikace

Po výběru šablony projektu jazyka Visual Basic a název souboru, Visual Studio otevře formulář za vás. Formulář je uživatelské rozhraní Windows. Vytvoříme aplikaci "Hello World" tak, že přidáte ovládací prvky do formuláře, a pak spustíme aplikaci.

### <a name="add-a-button-to-the-form"></a>Přidání tlačítka do formuláře

1. Klikněte na tlačítko **nástrojů** nabídka okno nástrojů.

     ![Klikněte na panelu nástrojů okno nástrojů](../ide/media/vb-toolbox-toolwindow.png)

     (Pokud se nezobrazí **nástrojů** nabídka možností, lze jej otevřít z řádku nabídek. Chcete-li tak učinit, klikněte na tlačítko **zobrazení** > **nástrojů**. Také můžete stisknout klávesu **Ctrl**+**Alt**+**X**.)

2. Klikněte na tlačítko **Pin** ikonu ukotvení **nástrojů** okna.

     ![Klikněte na ikonu připínáčku připněte okno nástrojů do integrovaného vývojového prostředí](../ide/media/vb-pin-the-toolbox-window.png)
3. Klikněte na tlačítko **tlačítko** řídit a přetáhněte ji na formuláři.

     ![Přidání tlačítka do formuláře](../ide/media/vb-add-a-button-to-form1.png)

4. V **vzhled** část **vlastnosti** okno, zadejte `Click this`a potom stiskněte klávesu **Enter**.

     ![Přidejte text pro tlačítko ve formuláři](../ide/media/vb-button-control-text.png)

     (Pokud se nezobrazí **vlastnosti** okna, lze jej otevřít z řádku nabídek. Chcete-li tak učinit, klikněte na tlačítko **zobrazení** > **okno vlastností**. Také můžete stisknout klávesu **F4**.)

5. V **návrhu** část **vlastnosti** okna, změňte název z **Button1** k `btnClickThis`a potom stiskněte klávesu **Enter**.

     ![Přidání funkce do tlačítko ve formuláři](../ide/media/vb-button-control-function.png)

### <a name="add-a-label-to-the-form"></a>Přidejte popisek do formuláře

Teď, když jsme přidali ovládací prvek tlačítko Vytvořit akci, přidáme popisek ovládacího prvku k odeslání text, který se.

1. Vyberte **popisek** ovládacího prvku **nástrojů** okna a přetáhněte ji na formuláři a přetáhněte ho pod **kliknutím na tuto** tlačítko.

2. V **návrhu** část **vlastnosti** okna, změňte název z **Label1** k `lblHelloWorld`a potom stiskněte klávesu **Enter**.

### <a name="add-code-to-the-form"></a>Přidejte kód do formuláře

1. V **Form1.vb &#91;návrhu&#93;**  okna, dvakrát klikněte **kliknutím na tuto** tlačítko Otevřít **Form1.vb** okna.

      (Alternativně můžete rozbalit **Form1.vb** v **Průzkumníka řešení**a potom klikněte na tlačítko **Form1**.)

2. V **Form1.vb** okna, mezi **privátní podprogram** řádku a **End Sub** řádek, zadejte nebo vložte `lblHelloWorld.Text = "Hello World!"`.

     ![Přidejte kód do formuláře](../ide/media/vb-add-code-to-the-form.png)

## <a name="run-the-application"></a>Spuštění aplikace

1. Klikněte na tlačítko **Start** tlačítko ke spuštění aplikace.

     ![Klikněte na příkaz Spustit ladění a spuštění aplikace](../ide/media/vb-click-start-hello-world.png)

   Stane se několik věcí. V sadě Visual Studio IDE **diagnostické nástroje** otevře se okno a **výstup** otevře se okno, příliš. Ale mimo rozhraní IDE **Form1** zobrazí se dialogové okno. Bude obsahovat vaše **kliknutím na tuto** tlačítko a text, který říká **Label1**.

2. Klikněte na tlačítko **kliknutím na tuto** tlačítko **Form1** dialogové okno. Všimněte si, **Label1** text změní na **Hello World!**.

    ![Dialogové okno Form1, které obsahuje Label1 text ](../ide/media/vb-form1-dialog-hello-world.png)

Blahopřejeme k dokončení tohoto rychlého startu! Doufáme, že jste se dozvěděli ještě něco o jazyce Visual Basic a Visual Studio IDE. Pokud chcete podrobnější delve, prosím pokračujte kurz ve **kurzy** část obsahu.

## <a name="see-also"></a>Viz také:

* [Rychlý start: Vytvoření konzolové aplikace v sadě Visual Studio pomocí jazyka Visual Basic](quickstart-visual-basic-console.md)
* [Další informace o jazyce Visual Basic IntelliSense](visual-basic-specific-intellisense.md)
